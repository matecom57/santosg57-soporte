.. _list-of-mrtrix3-commands:

########################
List of MRtrix3 commands
########################

https://mrtrix.readthedocs.io/en/dev/reference/commands_list.html

.. toctree::
    :hidden:

    commands/5tt2gmwmi
    commands/5tt2vis
    commands/5ttcheck
    commands/5ttedit
    commands/5ttgen
    commands/afdconnectivity
    commands/amp2response
    commands/amp2sh
    commands/connectome2tck
    commands/connectomeedit
    commands/connectomestats
    commands/dcmedit
    commands/dcminfo
    commands/dirflip
    commands/dirgen
    commands/dirmerge
    commands/dirorder
    commands/dirrotate
    commands/dirsplit
    commands/dirstat
    commands/dwi2adc
    commands/dwi2fod
    commands/dwi2mask
    commands/dwi2response
    commands/dwi2tensor
    commands/dwibiascorrect
    commands/dwibiasnormmask
    commands/dwicat
    commands/dwidenoise
    commands/dwiextract
    commands/dwifslpreproc
    commands/dwigradcheck
    commands/dwinormalise
    commands/dwirecon
    commands/dwishellmath
    commands/fixel2peaks
    commands/fixel2sh
    commands/fixel2tsf
    commands/fixel2voxel
    commands/fixelcfestats
    commands/fixelconnectivity
    commands/fixelcorrespondence
    commands/fixelcrop
    commands/fixelfilter
    commands/fixelreorient
    commands/fixeltransform
    commands/fod2dec
    commands/fod2fixel
    commands/for_each
    commands/label2colour
    commands/label2mesh
    commands/labelconvert
    commands/labelsgmfirst
    commands/labelstats
    commands/mask2glass
    commands/maskdump
    commands/maskfilter
    commands/mesh2voxel
    commands/meshconvert
    commands/meshfilter
    commands/mraverageheader
    commands/mrcalc
    commands/mrcat
    commands/mrcentroid
    commands/mrcheckerboardmask
    commands/mrclusterstats
    commands/mrcolour
    commands/mrconvert
    commands/mrdegibbs
    commands/mrdump
    commands/mredit
    commands/mrfilter
    commands/mrgrid
    commands/mrhistmatch
    commands/mrhistogram
    commands/mrinfo
    commands/mrmath
    commands/mrmetric
    commands/mrregister
    commands/mrstats
    commands/mrthreshold
    commands/mrtransform
    commands/mrtrix_cleanup
    commands/mrview
    commands/mtnormalise
    commands/peaks2amp
    commands/peaks2fixel
    commands/peakscheck
    commands/peaksconvert
    commands/population_template
    commands/responsemean
    commands/sh2amp
    commands/sh2peaks
    commands/sh2power
    commands/sh2response
    commands/shconv
    commands/shview
    commands/tck2connectome
    commands/tck2fixel
    commands/tckconvert
    commands/tckdfc
    commands/tckedit
    commands/tckgen
    commands/tckglobal
    commands/tckinfo
    commands/tckmap
    commands/tckresample
    commands/tcksample
    commands/tcksift
    commands/tcksift2
    commands/tckstats
    commands/tcktransform
    commands/tensor2metric
    commands/transformcalc
    commands/transformcompose
    commands/transformconvert
    commands/tsfdivide
    commands/tsfinfo
    commands/tsfmult
    commands/tsfsmooth
    commands/tsfthreshold
    commands/tsfvalidate
    commands/vectorstats
    commands/voxel2fixel
    commands/voxel2mesh
    commands/warp2metric
    commands/warpconvert
    commands/warpcorrect
    commands/warpinit
    commands/warpinvert


.. csv-table::
    :header: "Lang", "Command", "Synopsis"

    |cpp.png|, :ref:`5tt2gmwmi`, "Generate a mask image appropriate for seeding streamlines on the grey matter-white matter interface"
    |cpp.png|, :ref:`5tt2vis`, "Generate an image for visualisation purposes from an ACT 5TT segmented anatomical image"
    |cpp.png|, :ref:`5ttcheck`, "Thoroughly check that one or more images conform to the expected ACT five-tissue-type (5TT) format"
    |cpp.png|, :ref:`5ttedit`, "Manually set the partial volume fractions in an ACT five-tissue-type (5TT) image using mask images"
    |python.png|, :ref:`5ttgen`, "Generate a 5TT image suitable for ACT"
    |cpp.png|, :ref:`afdconnectivity`, "Obtain an estimate of fibre connectivity between two regions using AFD and streamlines tractography"


.. |cpp.png| image:: cpp.png
   :alt: C++

.. |python.png| image:: python.png
   :alt: Python

