# 🧬 PROYECTO RAPTOR PIPELINE: Inteligencia Artificial aplicada a la Contención Biológica

![InGen Logo](https://img.shields.io/badge/Proyecto-Raptor-Pipeline)
![Department](https://img.shields.io/badge/Department-DataAnalyst-green)

Bienvenido al repositorio oficial del **Departamento de Data Analyst de InGen**. Este proyecto integra nuestra estrategia de negocio de seguridad con el motor predictivo de Machine Learning para la predicción de ataques de especímenes de *Raptor*.

## 📖 Descripción del Proyecto

Este repositorio tiene como objetivo demostrar un **Pipeline de Machine Learning completo**, vinculando la toma de decisiones estratégicas con la implementación técnica. El proyecto se divide en dos grandes ejes:

1.  **Marco Estratégico (`/docs/estrategias_gestion_riesgo.md`)**: Define por qué InGen necesita IA, cómo medimos el éxito y cómo gestionamos las falsas alarmas para mantener el parque rentable.
2.  **Motor Predictivo (`/notebooks/ practica_guiada.ipynb`)**: Un modelo de clasificación binaria (Decision Tree) entrenado con datos de biosensores para predecir intentos de ataque en tiempo real.

## 🚀 Estructura del Repositorio

```text
jurassic-pipeline-ml/
├── assets/               
    └── Imágenes
├── docs/               
    └── Glosario.md 
│   └── Estrategia_gestion_riesgo.md 
├── notebooks/          
│   └── practica_guiada.ipynb      
├── requirements.txt           
└── README.md                  
```
---

## 🛠️ Instalación y Configuración

Para ejecutar este proyecto en tu estación de trabajo InGen, sigue estos pasos:

1. Clonar el repositorio:

```
  Bash
  git clone https://github.com/lucypelaez/PIPELINE_ML.git
```
2. Crear y activar el entorno virtual:
```
  Bash
  python -m venv .venv
  .venv\Scripts\activate
```
3. Instalar dependencias:
```
  Bash
  pip install -r requirements.txt
```
---
## 📋 Práctica guiada
Este repositorio está diseñado para que lo explores en este orden:

**1. Fase de Negocio:** Lee el archivo **Estrategia_gestion_riesgo.md** en la carpeta docs. Comprende el problema del Threshold y la importancia del Recall en un entorno donde un error significa un dinosaurio suelto.

**2. Fase Técnica:** Práctica guiada ya resuelta. Abre el Notebook y ejecuta las celdas. Verás cómo los datos de biosensores (Hambre, vocalizaciones, etc.) se transforman en una predicción de probabilidad.

Desafío Final: Al final del Notebook, intenta ajustar el modelo para reducir las falsas alarmas sin dejar que el riesgo de ataque suba del 10%. Juega con las variables, los ajustes de los pesos asignados a las mismas, la semilla de reproducibilidad, ... y observa los cambios que devuelve el modelo, en la experimentación favorece el aprendizaje.

---

## 🔍 ¿Confundido con los términos? 

Consulta el Glosario Técnico de InGen para entender la terminología de Machine Learning utilizada en el proyecto, disponible en la carpeta docs del repositorio.
