# 📱 Samsung Galaxy A71 (SM-A715F) - Auditoría y Conexión

Documentación técnica del proceso de conexión y configuración del dispositivo para el laboratorio de seguridad móvil.

## 🛠️ 1. Preparación del Entorno (Modo Desarrollador)

El primer paso crítico es habilitar el puente de depuración (ADB) oculto por defecto en Android 13 (One UI 5.1).

### Habilitar opciones de desarrollo
Navegamos a **Ajustes > Información de software** y pulsamos 7 veces sobre el número de compilación.

> **Evidencia:**
> ![Numero de Compilacion](img/numero_compilacion.png)

### Activar Depuración USB
Una vez habilitado el menú secreto, accedemos a **Opciones de desarrollador** y activamos el interruptor de depuración.

> **Evidencia:**
> ![Opciones de Desarrollador](img/Opciones_desarrollador.png)

## 💻 2. Conexión Exitosa con Scrcpy

Tras conectar el cable USB y aceptar la huella RSA en el dispositivo, establecemos la conexión.

**Comando ejecutado:**
```bash
scrcpy
