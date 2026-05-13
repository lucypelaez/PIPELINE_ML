# 🦖 Estrategia de ML: Gestión de Seguridad en Jurassic Park

## 1. Definición del Problema

1. **Decisión de Negocio y Variable Objetivo**  🎯

En un parque con dinosaurios, la seguridad es lo primero. Si podemos predecir un ataque antes de que ocurra, podemos actuar.

- **Decisión de negocio:** Optimizar la activación de protocolos de seguridad (cierre de sectores, refuerzo de vallas o sedación preventiva).

-  **Variable objetivo:** El objetivo es predecir la probabilidad de que un dinosaurio, en este caso, los velociraptores, ataque. Es una variable binaria donde 1 es "Intento de ataque detectado" y 0 es "Comportamiento normal".

2. **Horizonte temporal** ⏱️

* **Operativo:** Predicción de riesgo en tiempo real (próximos 15-30 min).

* **Estratégico:** Análisis de tendencias mensuales para rediseñar protocolos de alimentación y perímetros.

## 2. Datos y Variables 
* **Variables candidatas:**

Variables (*Features*)|Qué mide
|---|---|
Hambre| Nivel detectado por biosensores.
Distancia_presa| Distancia entre el raptor y el humano más cercano.
Temperatura| Factor ambiental que afecta el metabolismo.
Vocalizaciones| Nivel de estrés detectado por sensores acústicos. 
En_manada| modo de caza, en solitario o en grupo

    Considerar nuevas variables como por ejemplo: estado_valla (Integridad del sensor de corriente en el perímetro). ⚡

* **Riesgos de calidad:** 


- **Fallo de sensores:** Sensores de distancia obstruidos por vegetación. 🌿

- **Latencia:** Retraso en la llegada de la señal de hambre desde los biosensores.⌛


## 3. Evaluación y Acción 📝
* **Baseline:** **Clasificación por Clase Mayoritaria**. 

    * Asumir el comportamiento más frecuente según histórico. Y asignamos etiquetas, Ataca (1) o No ataca (0) en función de la distribución de clases.

* **Métrica:** **Recall (Sensibilidad)** 🎯. 
    * *¿Por qué?* Porque el coste de un "Falso Negativo" (decir que no ataca cuando sí lo va a hacer) es una catástrofe humana y financiera. Preferimos falsas alarmas (Falsos Positivos) que garanticen seguridad total.
* **Acción ante predicción alta:** 
    * **Inmediata:** Evacuación de zonas adyacentes y despliegue de medidas de emergencia y contención.
    * **Preventiva:** Si la probabilidad sube de forma constante, se reprograman las rondas de alimentación y se inspeccionan los niveles de estrés de los especímenes.

## 4. Seguimiento y Mejora Continua
* **Revisión mensual:** 

Analizaremos la **Matriz de Confusión** del último mes.
- Si detectamos muchos ataques reales no previstos, ajustaremos los pesos de la variable `hambre`.
- Evaluaremos si el aumento de distancia en los protocolos de alimentación ha suavizado la "frontera de decisión" del modelo.
* **Comparativa biológica:** Revisaremos si los pesos asignados coinciden con estudios etológicos de aves carnívoras sociales. Si las aves son silenciosas al atacar, el peso de `vocalizaciones` debería bajar en favor de `distancia`

## RESUMEN EJECUTIVO

|Puntos clave|Estrategia de negocio|
|---|---|
Decisión|Rediseño de protocolos de seguridad y alimentación mediante el análisis de patrones biológicos (vocalizaciones y jerarquía de manada).🦖
Métrica |Recall (Sensibilidad), porque en un parque con humanos, no podemos permitirnos ignorar ni un solo ataque real. 
Mayor Riesgo| Falsos Negativos por subestimar ataques de baja intensidad o "silenciosos" si no ajustamos bien los pesos de las variables. ⚠️

## REVISIÓN DEL MODELO 🔎

Un mes después, se propone realizar la revisión del modelo para comprobar si su funcionamiento está siendo efectivo y genera un beneficio en la gestión y operativa del parque.
Esta revisión periódica es crucial para que el modelo detecte con alta probabilidad los ataques sin generar falsas alarmas que entorpezcan el funcionamiento de las instalaciones.

Un modelo que detecta todos los ataques pero genera demasiadas falsas alarmas— se conoce como un problema de precisión frente a sensibilidad (recall). En un entorno de alta seguridad como Jurassic Park, este equilibrio es vital para que el parque sea rentable. 💸

Factores falsas alarmas|Revisión mensual|Ajustes modelo
|---|---|---|
El Umbral de Decisión (Threshold)⚖️|Aumentar o reducir el umbral en función de los resultados obtenidos|Menos falsas alarmas, pero aumenta el riesgo de que un ataque real con probabilidad del 70% pase desapercibido.
Calidad y Representatividad de la Muestra 📊|Si el modelo se entrenó con datos confusos dará falsas alarmas.| Reentrenar con ejemplos de esos "casos confusos".
Variables de Contexto🛡️|El modelo actual solo mira al dinosaurio, pero no mira el entorno.|Introducción de una "Matriz de Riesgo" que combine la predicción del modelo con el estado de las instalaciones. 🏗️ Nueva variable: nivel_de_contencion (del 1 al 5, donde 5 es máxima seguridad). 

    Gestión de Falsas Alarmas y Acción 🛡️:
    
    - Intervención localizada de guardias y revisión de infraestructuras.

    - Mitigación de errores: En la revisión mensual, se cruza la predicción de la IA con  el Nivel de Contención del recinto. Si la seguridad de la infraestructura es máxima, se evita el cierre total del parque, transformando la alerta en una revisión de mantenimiento preventivo.
