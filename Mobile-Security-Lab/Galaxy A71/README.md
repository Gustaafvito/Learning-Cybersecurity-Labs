# 📱 Samsung Galaxy A71 - Configuración y Uso

Documentación de conexión, configuración y atajos para controlar el Samsung Galaxy A71 mediante `scrcpy`.

## 🛠️ Requisitos Previos (En el A71)

Para permitir la conexión ADB es necesario activar las opciones de desarrollador:

1. Ir a **Ajustes** > **Acerca del teléfono** > **Información de software**.
2. Pulsar **7 veces** sobre **Número de compilación** (introducir PIN si lo pide).
3. Volver a Ajustes, entrar en **Opciones de desarrollador**.
4. Activar **Depuración por USB**.

## 🚀 Conexión Rápida

1. Conectar el móvil por USB al PC.
2. Aceptar la huella digital RSA en la pantalla del móvil ("Permitir siempre...").
3. Ejecutar el comando:
   ```bash
   scrcpy
