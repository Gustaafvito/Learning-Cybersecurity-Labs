# 📱 Mobile Security Lab & Device Analysis

![Android](https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active_Research-blue?style=for-the-badge)

> **Entorno de pruebas controlado y documentación de análisis de seguridad en dispositivos físicos.**

Este directorio centraliza la configuración, herramientas y hallazgos obtenidos durante mis auditorías de seguridad en hardware real Android.

---

## 📂 Estructura del Laboratorio

He dividido el laboratorio según el dispositivo y la fase de preparación:

| Directorio | Descripción |
| :--- | :--- |
| **[📂 00_Configuracion_Entorno](./00_Configuracion_Entorno)** | Scripts de preparación (`ADB`), instalación de certificados (Burp Suite) y herramientas base (`Frida`, `Objection`). |
| **[📱 Galaxy A71](./Galaxy%20A71)** | Análisis de vulnerabilidades, Rooting y pruebas específicas sobre Samsung Galaxy A71. |
| **[📱 POCO M5](./POCO_M5)** | Pruebas de explotación, desbloqueo de Bootloader y bypass de seguridad en Xiaomi POCO M5. |

---

## 🛠️ Stack Tecnológico
Para estas pruebas utilizo un arsenal estándar de Mobile Hacking:

* **Conexión & Debug:** `ADB`, `Fastboot`, `Scrcpy`.
* **Análisis Dinámico:** `Frida`, `Objection`.
* **Análisis Estático:** `MobSF`, `Jadx`.
* **Interceptación de Tráfico:** `Burp Suite Pro` (con instalación de CA a nivel de sistema).

---

## ⚠️ Disclaimer
Todo el contenido de este repositorio tiene **fines puramente educativos y de investigación**. Las pruebas se han realizado en dispositivos de mi propiedad en un entorno de red aislado.

<div align="center">
  <sub>Research by <a href="https://github.com/Gustaafvito">Gustaafvito</a></sub>
</div>
