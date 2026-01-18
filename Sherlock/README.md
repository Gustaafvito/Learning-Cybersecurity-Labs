# 🕵️‍♂️ Laboratorio: Sherlock - Auditoría de Huella Digital

## 🎯 Objetivo

Realizar una auditoría de **OSINT (Open Source Intelligence)** sobre mi propia marca personal (`gustaafvito.creador.ia`) para verificar qué información es públicamente accesible a través del nombre de usuario en diversas plataformas.

---

## 🛠️ Fase 1: Instalación y Solución de Errores

El primer paso fue clonar el repositorio oficial de la herramienta en mi entorno Kali Linux.

![Clonando repositorio](Sherlock/Git%20Clone.png)

### 🚧 El Reto Técnico (PEP 668)

Al intentar instalar las dependencias con `pip`, me encontré con el error `externally-managed-environment`. Esto es una medida de seguridad en las versiones nuevas de Kali/Debian para proteger el sistema base.

**Solución aplicada:**
En lugar de forzar la instalación, implementé las mejores prácticas creando un **Entorno Virtual (venv)** para aislar las librerías.

```bash
# 1.1 Crear el entorno virtual
python3 -m venv entornovirtual

# 1.2 Activar el entorno
source entornovirtual/bin/activate

# 1.3 Instalar dependencias de forma segura
pip3 install .
```

---

## 💻 Fase 2: Ejecución del Escaneo

Una vez configurado el entorno, lancé la herramienta contra mi usuario objetivo para buscar coincidencias en más de 300 plataformas sociales.

### 2.1 Búsqueda de usuario

```bash
sherlock gustaafvito.creador.ia
```

![Resultado de búsqueda de usuario](Sherlock/Busqueda%20usuario.png)

---

## ✅ Fase 3: Validación Manual (Blue Team)

Como analista, es fundamental verificar los hallazgos para descartar *falsos positivos*. Realicé una navegación manual a las URLs proporcionadas por Sherlock.

Se confirmó la existencia y accesibilidad de los perfiles detectados:

![Validación en navegador](Sherlock/Navegador.png)

---

## 🚀 Conclusión

Sherlock ha demostrado ser una herramienta eficaz para la fase de **Reconocimiento**. He podido comprobar la exposición de mi marca personal en segundos.

Esta práctica refuerza la importancia de auditar periódicamente nuestra propia huella digital para entender qué información estamos exponiendo al público.
