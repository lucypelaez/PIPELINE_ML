## 📖 GLOSARIO DE BIOTECNOLOGÍA DIGITAL (InGen)
     AVISO DE SEGURIDAD: La comprensión de estos términos es obligatoria para todo el personal de la Sala de Control. El desconocimiento de un "Falso Negativo" puede invalidar su seguro de vida.

### 🧪 Fase de Datos: El ADN del Modelo
---
* **Dataset 📂:** Es nuestra materia prima. Imagina que es el ámbar que contiene el ADN; sin una buena muestra, no hay dinosaurio... ni modelo. En nuestro caso, es el historial de registros de los biosensores de los Velocirráptores.

* **Datos Sintéticos:** Datos generados mediante algoritmos que imitan el comportamiento real. Se utilizan cuando los datos reales son insuficientes o peligrosos de obtener.

* **Features (Atributos de Comportamiento) 🧬:** Son las pistas que nos da el espécimen. Las columnas de entrada que el modelo utiliza para aprender.

        Ejemplo InGen: Hambre, Vocalizaciones, Distancia_a_la_presa.

* **Target (Predicción Crítica) 🎯:** Lo que queremos predecir. En este proyecto es la columna Ataque (1 para "Sí", 0 para "No"). 

                            La respuesta que buscamos. ¿Ataca?

                        1 (SI): ¡Corred insensatos! (Ataque inminente).
                        0 (NO): Todo en orden. Nivel de seguridad máximo


### 🛠️ El Pipeline: La Cadena de Montaje
---
* **EDA (Observación de Campo) 🔍:** Antes de soltar al modelo, analizamos los datos con gráficos. Es como observar a los raptores desde el cristal de seguridad para entender sus patrones.

* **Preprocesamiento:** Limpiar y transformar los datos (como escalar las temperaturas o normalizar el hambre) para que el algoritmo pueda entenderlos mejor.

* **Train/Test Split (Protocolo de Simulación) ✂️:** Dividimos los datos. Técnica para evaluar el modelo. Entrenamos a la IA con una parte de los datos (70-80%) y guardamos el resto para ver si es capaz de predecir ataques que nunca ha visto.

* **Data Leakage:** Ocurre cuando el modelo recibe información que no debería conocer durante el entrenamiento, haciendo que las métricas parezcan mejores de lo que realmente serán en el mundo real.

* **Validación cruzada:** La validación cruzada consiste en dividir repetidamente los datos disponibles en subconjuntos, entrenar el modelo con algunos de ellos y validarlo con los subconjuntos restantes. La principal ventaja de la validación cruzada es que proporciona una estimación más sólida e imparcial del rendimiento del modelo en comparación con el método de validación tradicional.

* **GridSearchCV:** Método que prueba automáticamente distintas configuraciones del modelo utilizando validación cruzada.”

### 📊 Evaluación: El Semáforo de Peligro 
---
* **Semilla de Reproducibilidad (Random State):** Número fijo (generalmente 42) que asegura que el azar sea siempre el mismo, permitiendo que el experimento se repita con resultados idénticos.

* **Algoritmo de Clasificación:** Un tipo de ML que decide entre categorías (Ataque vs. No Ataque). Usamos Árboles de Decisión por su capacidad de mostrar reglas lógicas (ej: "SI Hambre > 80 ENTONCES Riesgo Alto").

* **Matriz de Confusión 🧩:** La herramienta definitiva para ver dónde se equivoca nuestra IA.

* **Falso Positivo (Alerta Innecesaria) 🔊:** La IA dice que el raptor va a atacar, pero solo estaba bostezando. Perdemos dinero cerrando el parque por nada.

* **Falso Negativo (Fallo Catastrófico) 💀:** La IA dice que el raptor está tranquilo, pero está rompiendo el cristal. Este es el error que queremos evitar a toda costa.

* **Recall (Capacidad de Detección) 🚨:** Es nuestra prioridad absoluta. Mide qué porcentaje de ataques reales somos capaces de detectar. Preferimos mil falsas alarmas antes que dejar pasar un ataque real.

* **Overfitting (Efecto "Raptor Domado") 🧠:** Cuando el modelo se aprende de memoria el comportamiento de un solo dinosaurio pero no sabe qué hacer cuando llega uno nuevo. El modelo es "demasiado listo" con los datos viejos, pero inútil con los nuevos.

### ⚖️ El Dilema de InGen: Seguridad vs. Rentabilidad
---
                "En Machine Learning, no existen los modelos perfectos, 
                            solo los modelos bien calibrados." 

Las siguientes tablas comparan los diferentes escenarios de riesgo que enfrentamos al configurar nuestra IA de contención.

### 📊 Tabla I: Prioridades Predictivas
| Métrica | ¿Qué mide en InGen? | Si fallamos... | Prioridad |
| :--- | :--- | :--- | :--- |
| **Recall** | Capacidad de detectar **todos** los ataques reales. | Un raptor escapa porque la IA dijo que estaba "tranquilo". | **CRÍTICA** 🚨 |
| **Precision** | Capacidad de no dar alarmas en vano. | Cerramos el parque y sedamos dinosaurios por un bostezo. | **Económica** 💸 |
| **Accuracy** | Aciertos totales (Ataques y No-Ataques). | Podemos tener un 99% de acierto y que el 1% de error sea una tragedia. | **Engañosa** ⚠️ |

### 🧪 Tabla II: Calibración del Umbral (Threshold)
| Configuración | Probabilidad para Alerta | Seguridad | Impacto Negocio |
| :--- | :--- | :--- | :--- |
| **Conservador** | > 10% | **Máxima** | Bajas por falsas alarmas |
| **Estándar** | > 50% | **Equilibrada** | Flujo operativo normal |
| **Arriesgado** | > 80% | **Peligrosa** | El parque nunca cierra por error |

---

### 🛠️ Protocolo de ImplementaciónNota para el Analista:

                Los conceptos anteriores se materializan en el código.
                Para ver cómo estas métricas afectan al rendimiento real del sistema,
                accede al archivo: 👉 notebooks/01_pipeline_raptores.ipynb