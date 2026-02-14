# 🛠️ Transformación de Entorno en Kali Linux: AutoBspwmKali

Este laboratorio documenta el proceso de despliegue de un entorno profesional de pentesting utilizando **BSPWM** (Binary Space Partitioning Window Manager).

El objetivo es migrar de un entorno de escritorio tradicional (XFCE/Gnome) a un entorno de ventanas tipo *tiling* optimizado para la productividad, bajo consumo de recursos y agilidad en auditorías de ciberseguridad.

Utilizaremos la herramienta automatizada: [AutoBspwmKali](https://github.com/Justice-Reaper/AutoBspwmKali).

---

## 1. Estado Inicial (The "Before")

Partimos de una instalación estándar de Kali Linux. Como se observa, el entorno de escritorio por defecto consume más recursos gráficos y la gestión de ventanas es manual.

**Especificaciones del sistema actual:**

![Estado Inicial - Kali Linux XFCE](img/Kali_antes.png)
*Captura de pantalla mostrando el entorno XFCE por defecto y las especificaciones del sistema (Fastfetch).*

---

## 2. Instalación y Despliegue

El proceso se realiza clonando el repositorio oficial de la herramienta y ejecutando el script de orquestación.

### Paso 2.1: Actualización del Sistema
Antes de comenzar, aseguramos que el sistema y las dependencias base estén actualizadas para evitar conflictos durante la compilación de herramientas.

```bash
sudo apt update && sudo apt upgrade -y
```

---

Paso 2.2: Clonación del Repositorio
Descargamos el código fuente de AutoBspwmKali en nuestro directorio de trabajo.

```bash
git clone https://github.com/Justice-Reaper/AutoBspwmKali
```
![Clonación repositorio](img/2-Clonación.png)

Paso 2.3: Ejecución del Instalador
Accedemos al directorio descargado, otorgamos permisos de ejecución al script principal (AutoBSPWM.sh) y lo ejecutamos con privilegios de superusuario.

```bash
cd AutoBspwmKali
chmod +x AutoBSPWM.sh
sudo ./AutoBSPWM.sh
```

⚠️ Nota de ejecución: Durante el proceso, el script detectará el entorno y nos pedirá confirmación sobre si estamos instalando en una Máquina Virtual o en Hardware Físico. Selecciona la opción adecuada para tu caso.

---
### Paso 2.4: Definición de Usuario
Una vez iniciado el script, veremos el banner de bienvenida. El sistema nos solicitará el nombre del usuario al que se aplicarán los cambios (en nuestro caso, el usuario actual).

![Inicio del Script y Selección de Usuario](img/3-Inicio_script.png)
*Introducimos nuestro nombre de usuario para que el script configure los permisos y directorios en `/home/usuario`.*

---

### Paso 2.5: Optimización de Entorno
El script nos preguntará si estamos ejecutando Kali Linux en una máquina virtual. Es **crítico** responder correctamente para que se apliquen las configuraciones gráficas adecuadas (Picom) y evitar lag en la interfaz.

![Selección de Virtual Machine](img/4_Seleccion_vm.png)

*Seleccionamos "YES" para desactivar efectos pesados de blur y transparencias que no rinden bien en virtualización.*


