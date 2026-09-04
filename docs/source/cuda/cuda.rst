cuda
====

**2.1.2. Kernels**

.. video:: movie.mp4
   :width: 640
   :autoplay:
   :controls:

As mentioned in the introduction to the CUDA Programming Model, functions which execute on the GPU which can be invoked from the host are called kernels. Kernels are written to be run by many parallel threads simultaneously.

2.1.2.1. Specifying Kernels

The code for a kernel is specified using the __global__ declaration specifier. This indicates to the compiler that this function will be compiled for the GPU in a way that allows it to be invoked from a kernel launch. A kernel launch is an operation which starts a kernel running, usually from the CPU. Kernels are functions with a void return type.

.. code:: Bash

   // Kernel definition
   __global__ void vecAdd(float* A, float* B, float* C)
   {

   }

https://docs.nvidia.com/cuda/cuda-programming-guide/02-basics/intro-to-cuda-cpp.html

**2.1.2.2. Launching Kernels**

The number of threads that will execute the kernel in parallel is specified as part of the kernel launch. This is called the execution configuration. Different invocations of the same kernel may use different execution configurations, such as a different number of threads or thread blocks.

There are two ways of launching kernels from CPU code, triple chevron notation and cudaLaunchKernelEx. Triple chevron notation, the most common way of launching kernels, is introduced here. An example of launching a kernel using cudaLaunchKernelEx is shown and discussed in detail in in section Section 3.1.1.

**2.1.2.2.1. Triple Chevron Notation**

Triple chevron notation is a CUDA C++ Language Extension which is used to launch kernels. It is called triple chevron because it uses three chevron characters to encapsulate the execution configuration for the kernel launch, i.e. <<< >>>. Execution configuration parameters are specified as a comma separated list inside the chevrons, similar to parameters to a function call. The syntax for a kernel launch of the vecAdd kernel is shown below.


.. code:: Bash

__global__ void vecAdd(float* A, float* B, float* C)
 {

 }

int main()
   {
       ...
       // Kernel invocation
       vecAdd<<<1, 256>>>(A, B, C);
       ...
   }

The first two parameters to the triple chevron notation are the grid dimensions and the thread block dimensions, respectively. When using 1-dimensional thread blocks or grids, integers can be used to specify dimensions.

The above code launches a single thread block containing 256 threads. Each thread will execute the exact same kernel code. In Thread and Grid Index Intrinsics, we’ll show how each thread can use its index within the thread block and grid to change the data it operates on.

There is a limit to the number of threads per block, since all threads of a block reside on the same streaming multiprocessor(SM) and must share the resources of the SM. On current GPUs, a thread block may contain up to 1024 threads. If resources allow, more than one thread block can be scheduled on an SM simultaneously.

Kernel launches are asynchronous with respect to the host thread. That is, the kernel will be setup for execution on the GPU, but the host code will not wait for the kernel to complete (or even start) executing on the GPU before proceeding. Some form of synchronization between the GPU and CPU must be used to determine that the kernel has completed. The most basic version, completely synchronizing the entire GPU, is shown in Synchronizing CPU and GPU. More sophisticated methods of synchronization are covered in Asynchronous Execution.

When using 2 or 3-dimensional grids or thread blocks, the CUDA type dim3 is used as the grid and thread block dimension parameters. The code fragment below shows a kernel launch of a MatAdd kernel using 16 by 16 grid of thread blocks, each thread block is 8 by 8.

https://docs.nvidia.com/cuda/cuda-programming-guide/02-basics/intro-to-cuda-cpp.html

.. code:: Bash

   int main()
   {
       ...
       dim3 grid(16,16);
       dim3 block(8,8);
       MatAdd<<<grid, block>>>(A, B, C);
       ...
   }

**2.1.2.3. Thread and Grid Index Intrinsics**


Within kernel code, CUDA provides intrinsics to access parameters of the execution configuration and the index of a thread or block.

* threadIdx gives the index of a thread within its thread block. Each thread in a thread block will have a different index.

* blockDim gives the dimensions of the thread block, which was specified in the execution configuration of the kernel launch.

* blockIdx gives the index of a thread block within the grid. Each thread block will have a different index.

* gridDim gives the dimensions of the grid, which was specified in the execution configuration when the kernel was launched.

Each of these intrinsics is a 3-component vector with a .x, .y, and .z member. Dimensions not specified by a launch configuration will default to 1. threadIdx and blockIdx are zero indexed. That is, threadIdx.x will take on values from 0 up to and including blockDim.x-1. .y and .z operate the same in their respective dimensions.

Similarly, blockIdx.x will have values from 0 up to and including gridDim.x-1, and the same for .y and .z dimensions, respectively.

These allow an individual thread to identify what work it should carry out. Returning to the vecAdd kernel, the kernel takes three parameters, each is a vector of floats. The kernel performs an element-wise addition of A and B and stores the result in C. The kernel is parallelized such that each thread will perform one addition. Which element it computes is determined by its thread and grid index.

.. code:: Bash

   __global__ void vecAdd(float* A, float* B, float* C)
   {
      // calculate which element this thread is responsible for computing
      int workIndex = threadIdx.x + blockDim.x * blockIdx.x

      // Perform computation
      C[workIndex] = A[workIndex] + B[workIndex];
   }

   int main()
   {
       ...
       // A, B, and C are vectors of 1024 elements
       vecAdd<<<4, 256>>>(A, B, C);
       ...
   }

In this example, 4 thread blocks of 256 threads are used to add a vector of 1024 elements. In the first thread block, blockIdx.x will be zero, and so each thread’s workIndex will simply be its threadIdx.x. In the second thread block, blockIdx.x will be 1, so blockDim.x * blockIdx.x will be the same as blockDim.x, which is 256 in this case. The workIndex for each thread in the second thread block will be its threadIdx.x + 256. In the third thread block workIndex will be threadIdx.x + 512.

This computation of workIndex is very common for 1-dimensional parallelizations. Expanding to two or three dimensions often follows the same pattern in each of those dimensions.

**2.1.2.3.1. Bounds Checking**

The example given above assumes that the length of the vector is a multiple of the thread block size, 256 threads in this case. To make the kernel handle any vector length, we can add checks that the memory access is not exceeding the bounds of the arrays as shown below, and then launch one thread block which will have some inactive threads.

.. code:: Bash

   __global__ void vecAdd(float* A, float* B, float* C, int vectorLength)
   {
        // calculate which element this thread is responsible for computing
        int workIndex = threadIdx.x + blockDim.x * blockIdx.x

        if(workIndex < vectorLength)
        {
            // Perform computation
            C[workIndex] = A[workIndex] + B[workIndex];
        }
   }

With the above kernel code, more threads than needed can be launched without causing out-of-bounds accesses to the arrays. When workIndex exceeds vectorLength, threads exit and do not do any work. Launching extra threads in a block that do no work does not incur a large overhead cost, however launching thread blocks in which no threads do work should be avoided. This kernel can now handle vector lengths which are not a multiple of the block size.

The number of thread blocks which are needed can be calculated as the ceiling of the number of threads needed, the vector length in this case, divided by the number of threads per block. That is, the integer division of the number of threads needed by the number of threads per block, rounded up. A common way of expressing this as a single integer division is given below. By adding threads - 1 before the integer division, this behaves like a ceiling function, adding another thread block only if the vector length is not divisible by the number of threads per block.

.. code::

   // vectorLength is an integer storing number of elements in the vector
   int threads = 256;
   int blocks = (vectorLength + threads-1)/threads;
   vecAdd<<<blocks, threads>>>(devA, devB, devC, vectorLength);

The CUDA Core Compute Library (CCCL) provides a convenient utility, cuda::ceil_div, for doing this ceiling divide to calculate the number of blocks needed for a kernel launch. This utility is available by including the header <cuda/cmath>.

.. code:: Bash

   // vectorLength is an integer storing number of elements in the vector
   int threads = 256;
   int blocks = cuda::ceil_div(vectorLength, threads);
   vecAdd<<<blocks, threads>>>(devA, devB, devC, vectorLength);

The choice of 256 threads per block here is arbitrary, but this is quite often a good value to start with.

**2.1.3. Memory in GPU Computing**

https://docs.nvidia.com/cuda/cuda-programming-guide/02-basics/intro-to-cuda-cpp.html











