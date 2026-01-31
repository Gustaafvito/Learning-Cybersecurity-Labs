# 🕵️‍♂️ Laboratorio: Sherlock - Auditoría de Huella Digital

## 🎯 Objetivo

Realizar una auditoría de **OSINT (Open Source Intelligence)** sobre mi propia marca personal, sobre mi canal de creación de imagenes y videos con IA (`gustaafvito.creador.ia`) para verificar qué información es públicamente accesible a través del nombre de usuario en diversas plataformas.

---

## 🛠️ Fase 1: Instalación y Solución de Errores

El primer paso fue clonar el repositorio oficial de la herramienta en mi entorno Kali Linux.
```bash
git clone https://github.com/sherlock-project/sherlock.git
```
![Clonando repositorio](Git%20Clone.png)

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
![instalar dependencias](Pip%20install.png)
---

## 💻 Fase 2: Ejecución del Escaneo

Una vez configurado el entorno, lancé la herramienta contra un usuario que tengo para redes sociales de creacion de imagenes y videos con IA, para buscar coincidencias en más de 300 plataformas sociales.

### 2.1 Búsqueda de usuario

```bash
sherlock gustaafvito.creador.ia
```

![Resultado de búsqueda de usuario](Busqueda%20usuario.png)

---

## ✅ Fase 3: Validación Manual (Blue Team)

Como analista, es fundamental verificar los hallazgos para descartar *falsos positivos*. Realicé una navegación manual a las URLs proporcionadas por Sherlock.

Se confirmó la existencia y accesibilidad de los perfiles detectados:

![Validación en navegador](Navegador.png)

---

## 🎓 Conclusión

Sherlock ha demostrado ser una herramienta eficaz para la fase de **Reconocimiento**. He podido comprobar la exposición de mi marca personal en segundos.

Esta práctica refuerza la importancia de auditar periódicamente nuestra propia huella digital para entender qué información estamos exponiendo al público.

---

## ⚠️ Disclaimer
El uso de este material y las herramientas mencionadas es estrictamente **educativo y formativo**.

Las pruebas realizadas en este laboratorio se llevaron a cabo sobre **mis propios activos y cuentas** (`gustaafvito.creador.ia`) con el fin de auditar mi propia seguridad.

El autor no se hace responsable del mal uso que terceros puedan dar a la información aquí expuesta. El acceso no autorizado a sistemas informáticos o el ciberacoso son delitos penados por la ley.

### 📚 Autor: Gustavo Luis Sánchez Escobar
*CyberSecurity Researcher | Pentesting · OSINT · Linux* 📅 **2026**
