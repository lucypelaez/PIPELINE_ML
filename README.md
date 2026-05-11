# 🧬 Operaciones Jurásicas: Inteligencia Artificial aplicada a la Contención Biológica

![InGen Logo](https://img.shields.io/badge/Status-Active_Research-red)
![Department](https://img.shields.io/badge/Department-Behavioral_Research-blue)

Bienvenido al repositorio oficial del **Departamento de Investigación Conductual de InGen**. Este proyecto integra nuestra estrategia de negocio de seguridad con el motor predictivo de Machine Learning para la contención de especímenes de *Velocirraptor*.

## 📖 Descripción del Proyecto

Este repositorio tiene como objetivo demostrar un **Pipeline de Machine Learning completo**, vinculando la toma de decisiones estratégicas con la implementación técnica. El proyecto se divide en dos grandes ejes:

1.  **Marco Estratégico (`/docs/estrategias_gestion_riesgo.md`)**: Define por qué InGen necesita IA, cómo medimos el éxito (ROI de seguridad) y cómo gestionamos las falsas alarmas para mantener el parque rentable.
2.  **Motor Predictivo (`/notebooks/ 01_entrenamiento_raptores.ipynb`)**: Un modelo de clasificación binaria (Decision Tree) entrenado con datos de biosensores para predecir intentos de ataque en tiempo real.

## 🚀 Estructura del Repositorio

```text
jurassic-pipeline-ml/
├── docs/               
│   └── estrategia_gestion_riesgo.md # Estrategia de gestión de seguridad y negocio
├── notebooks/          
│   └── 01_entrenamiento_raptores.ipynb      # El Pipeline paso a paso (EDA, Prep, Model)
├── requirements.txt           # Dependencias para ejecutar el laboratorio
└── README.md                  # Manual de operaciones (esta guía)
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
## 📋 El Ejercicio para Compañeros
Este repositorio está diseñado para que lo explores en este orden:

**1. Fase de Negocio:** Lee el archivo .md en la carpeta docs. Comprende el problema del Threshold y la importancia del Recall en un entorno donde un error significa un dinosaurio suelto.

**2. Fase Técnica:** Práctica guiada ya resuelta. Abre el Notebook y ejecuta las celdas. Verás cómo los datos de biosensores (Hambre, Estrés Vocal, etc.) se transforman en una predicción de probabilidad.

Desafío Final: Al final del Notebook, intenta ajustar el modelo para reducir las falsas alarmas sin dejar que el riesgo de ataque suba del 10%.
```
"Sus científicos estaban tan preocupados por si podían hacerlo o no, que no se detuvieron a pensar si debían hacerlo." > — Dr. Ian Malcolm
```
