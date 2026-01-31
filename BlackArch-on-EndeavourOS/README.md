🛡️ Lab Deployment: BlackArch Linux "The Smart Way" (via EndeavourOS)
⚠️ Disclaimer: Este repositorio y documentación han sido creados exclusivamente con fines educativos y de investigación en Ciberseguridad. El autor no se hace responsable del mal uso de las herramientas aquí descritas. "Knowledge is power, but power requires responsibility."

🎯 Objetivo del Proyecto
Desplegar un laboratorio de pruebas de penetración (Pentesting) robusto y actualizado, integrando el repositorio oficial de BlackArch Linux (+2800 herramientas) sobre una base de sistema estable.

Este proyecto documenta el proceso de Troubleshooting y resolución de conflictos al intentar virtualizar la ISO oficial Legacy, y cómo se solucionó mediante una arquitectura modular.

🚩 Fase 1: El Problema (The Legacy ISO Fail)
Inicialmente, se intentó desplegar la imagen oficial blackarch-linux-slim-2023.05.01. Al tratarse de una versión "Rolling Release" congelada en 2023, surgieron conflictos críticos con las firmas digitales (GPG Keys) durante la instalación en vivo.

Evidencia del Fallo:
Selección de la Imagen: Se optó por la versión Slim para agilizar la descarga.

Arranque: El sistema booteó correctamente en modo Live.

Intento de Instalación: Se ejecutó el instalador gráfico nativo (Calamares).

El Conflicto: Durante el desempaquetado y actualización de paquetes...

Error Crítico: El gestor de paquetes pacman devolvió un error de Keyring (llaves desactualizadas), impidiendo continuar.

Diagnóstico: La ISO oficial contiene llaves GPG caducadas que impiden la conexión segura con los repositorios actuales, haciendo la instalación inviable sin un mantenimiento manual extenso previo.

🛠️ Fase 2: La Solución (Arquitectura Modular con EndeavourOS)
Para garantizar estabilidad, se pivotó la estrategia: "Instalar una base Arch Linux sólida primero, y añadir el arsenal después".

Se eligió EndeavourOS (Ganymede Neo) por ser la implementación más pura y amigable de Arch Linux.

Proceso de Instalación Base:
Descarga de la Base: Obtención de la ISO actualizada de EndeavourOS.

Configuración de Mirrors: Selección de servidores rápidos.

Arranque del Nuevo Motor: Inicio del entorno Live de Endeavour.

Configuración del Instalador: Se lanzó Calamares en el nuevo entorno.

La Clave del Éxito (Modo Offline): Se seleccionó la instalación Offline para desplegar el escritorio XFCE nativo desde la ISO, eliminando cualquier riesgo de error de descarga durante la instalación.

Sistema Base Operativo: Instalación completada y primer arranque exitoso con GRUB.

⚡ Fase 3: La Transformación (BlackArch Strap)
Con el sistema base estable, se ejecutó el script oficial de BlackArch (strap.sh) para convertir la máquina en un laboratorio de hacking.

Comandos de Integración:
Evidencia de la Transformación:
Ejecución del Script: El script actualizó automáticamente las llaves GPG (solucionando el error de la Fase 1).

Repositorio Sincronizado: El sistema confirmó: BlackArch repository is ready!.

✅ Estado Final del Laboratorio
El sistema opera ahora bajo un Kernel actualizado, con el entorno ligero XFCE y acceso total al repositorio de BlackArch.

Ventajas de esta arquitectura:

🟢 Estabilidad: Base mantenida por EndeavourOS.

🟢 Potencia: Arsenal completo de BlackArch disponible.

🟢 Seguridad: Firmas y llaves actualizadas al día.

Next Steps: Configuración de herramientas post-explotación y hardening del entorno.

Documentación realizada por Gustavo - CyberSecurity Researcher - 2026
