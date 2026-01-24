# 📱 POCO M5 - "El Atacante Rápido"
**Estado de la Misión:** 🟡 En Configuración (Fase 2)
**Objetivo:** Despliegue de Kali NetHunter Rootless

## 1. Conexión y Reconocimiento (ADB)
Para iniciar la auditoría, establecimos la conexión mediante el puente de depuración (ADB).

### 1.1 Autorización del Dispositivo
Tras activar las "Opciones de desarrollador" y la "Depuración USB", realizamos el handshake RSA.
- **Comando:** `./adb devices`
- **Resultado:** El dispositivo pasó de `unauthorized` a `device`, confirmando control total.

![Estado Device Autorizado](01-device.png)

### 1.2 Extracción de Ficha Técnica (Forensics)
En lugar de tomar notas manuales, realizamos un volcado completo de las propiedades del sistema (`build.prop`) para tener una referencia exacta del hardware y software.

- **Comando ejecutado:**
  ```powershell
  ./adb shell getprop > POCO_M5_specs.txt

### 1.3 Verificación de la Evidencia
Se generó correctamente el archivo `POCO_M5_specs.txt` en el directorio de trabajo, conteniendo todas las flags del sistema (versión de SDK, configuración de Bluetooth, detalles del kernel, etc.).

![Archivo generado en Windows](03-archivo.png)
![Vista previa de los datos internos](04-vista%20informacion%20del%20movil.png)
