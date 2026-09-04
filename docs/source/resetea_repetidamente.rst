resetea repetidamente
=====================

Para solucionar los reinicios constantes en Ubuntu, debes revisar los registros del sistema con el comando ``journalctl -b -1`` en la terminal para identificar la causa exacta del fallo.

**Pasos para identificar y solucionar el problema**

* **Accede al modo de recuperación:** Si la máquina se reinicia antes de dejarte iniciar sesión, enciende el equipo y mantén presionada la tecla ``Shift`` (en BIOS) o ``Esc`` (en UEFI) para abrir el menú de `**GRUB**. Selecciona **Opciones avanzadas para Ubuntu** y entra al **modo recuperación** (recovery mode). [1] (https://laboratoriolinux.es/index.php/-noticias-mundo-linux-/distribuciones/37445-como-solucionar-problemas-comunes-en-ubuntu-guia-para-principiantes.html)

* **Revisa los registros de errores:** Una vez dentro de la terminal de recuperación o cuando logres estabilidad, ejecuta ``journalctl -b -1`` para ver los errores del último arranque que provocaron el apagado o reinicio repentino. 

* **Problemas de temperatura o hardware:** Un reinicio repetido suele ser síntoma de sobrecalentamiento del procesador o fallas en la memoria RAM. Limpia el polvo del equipo y verifica el estado de tus componentes.

* Controladores gráficos dañados: Si actualizaste recientemente el sistema y el fallo ocurre al cargar el entorno gráfico, reinstala los controladores desde el menú de recuperación o actualizalos (por ejemplo, sudo apt install --reinstall ubuntu-desktop).

* Unidades de instalación conectadas: Si es una máquina virtual o física, asegúrate de no tener una memoria USB o una imagen ISO montada que fuerce un bucle de reinicio o reinstalación.




