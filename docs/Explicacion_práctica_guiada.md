# PRIMERA PARTE:
🏋️‍♀️ CREACIÓN DATASET Y DEFINICIÓN TARGET DE PREDICCIÓN
---

## 1. Generación de las Características (Inputs) 📝

Las primeras líneas crean datos aleatorios para representar a nuestros dinosaurios. Fíjate en estas funciones de la librería numpy (abreviada como np):

    np.random.randint(min, max, n): Genera números enteros aleatorios.

    np.random.uniform(min, max, n): Genera números decimales aleatorios.

Por ejemplo, en hambre = np.random.randint(1, 11, n), estamos diciendo que cada uno de los 400 velocirraptores tiene un nivel de hambre del 1 al 10.



## 2. La "Fórmula Mágica" (Probabilidad de Ataque) 🧮
Aquí es donde ocurre lo más importante para el Machine Learning. El código crea una regla para decidir si el dinosaurio ataca o no. Observa esta parte:

    Python
    prob_ataque = (
    0.4 * (hambre / 10) +
    0.3 * (1 - distancia_presa / 50) +
    0.2 * en_manada +
    0.1 * (vocalizaciones / 20)
    )


Antes de pasar a cómo se decide el ataque final, miremos la fórmula.  
El hambre está multiplicada por 0.4, mientras que las vocalizaciones están multiplicadas por 0.1.  
Esto indica la importancia que adquiere cada una de las variables en que la probabilidad de ataque sea mayor o menor. 

    🎯 En Machine Learning, a esos números (0.4, 0.3, 0.2, 0.1) los llamamos **pesos (o weights)**, y determinan cuánta influencia tiene cada variable en el resultado final.

## 3. El toque de "realidad": El Ruido Aleatorio 🎲
Después de calcular esa probabilidad teórica, para decidir si el ataque ocurre (1) o no (0):

            ataca = (prob_ataque + np.random.normal(0, 0.1, n) > 0.45).astype(int)

La realidad es "sucia" y compleja. 🌪️

Si el modelo de Machine Learning aprendiera de datos perfectos (sin ruido), se convertiría en una simple calculadora de fórmulas. Al añadir ese pequeño error aleatorio con **np.random.normal**, obligamos al modelo a aprender a generalizar y a entender tendencias, en lugar de memorizar una regla exacta.

## 4. La Clasificación Final (Binaria) ⚖️

La última parte de esa línea es crucial para entender el resultado:

                        ataca = (prob_ataque + ruido > 0.45).astype(int)

Aquí estamos convirtiendo una probabilidad (un número entre 0 y 1) en una decisión de sí (1) o no (0).

- Si la suma es mayor a 0.45, el resultado es True (que al convertirlo a entero con .astype(int) se vuelve 1).
- Si es menor, es False (se vuelve 0).

                    A este valor (0.45) se le llama umbral o threshold.

Finalmente con esto generamos una nueva columna en nuestro Dataframe, que nos devuelve la probabilidad de ataque de cada velocirraptor:

Hambre|Distancia_presa|Ataca (Objetivo)|
|---|---|---|
8|	12	|1|
2|	45	|0|

En Machine Learning, llamamos a las primeras columnas características (features) y a la última etiqueta o variable objetivo (target).

---

### Resumen:

* **Entradas:** Datos aleatorios que simulan la realidad (hambre, distancia_presa, etc.).

* **Lógica:** Una fórmula matemática donde cada dato tiene un "peso" distinto.

* **Realismo:** Añadimos ruido para que no sea una ciencia exacta.

* **Decisión:** Un umbral que separa quién ataca de quién no.

---

Un repaso visual 🦖, vamos a resumir la anatomía de este dataset:
Concepto Técnico|Elemento en tu Código|Descripción para tu clase|
|---|---|---|
Features (Características)|hambre, distancia, temperatura, etc.|Los datos observados que el modelo usará para "pensar".
Weights (Pesos)|0.4, 0.3, 0.2, 0.1|La importancia que le damos a cada factor en la decisión.
Noise (Ruido)|np.random.normal(0, 0.1, n)|El factor de incertidumbre que hace que el modelo sea realista.
Target (Objetivo)|ataca|La respuesta correcta que el modelo intenta predecir.

## SEGUNDA PARTE:
🕵️‍♀️ VISUALIZACIÓN Y COMPRENSIÓN DEL DATASET
---

## 1. Análisis Estadístico 📊

* Método **.info():** Obtenemos la información general del dataset
* Método **.describe():** Obtenemos una tabla con el promedio (mean), la desviación estándar (std), los valores mínimos y máximos, y los cuartiles de cada columna numérica. 
* Método **.isnull().sum():** Obtenemos el número de nulos por columna.
* Método **.value.counts():** Obtenemos en este caso el número de ataques, que es la variable objetivo.


## 2. Visualización Gráfica 📈

Los números nos dan confianza, los gráficos nos ayudan a ver patrones.

- Para este ejercicio realizamos la visualización gráfica mediante varios **histogramas** en los que representamos las distintas variables de estudio (features) y como estas afectan a la probabilidad de ataque de los velociraptores. 
- También se añade una **matriz de correlación** en la que vemos la fuerza y la dirección entre unas variables y otras.
- Finalmente incorporamos un **Gráfico de Dispersión (Scatter Plot)** en el que enfrentamos las dos variables que más influyen en la probabilidad de ataque (hambre y distancia_presa). 

En este último gráfico vemos una nube de puntos verdes (No Ataca) y rojos (Ataca):

    La Zona de Peligro: concentración masiva de puntos rojos en la parte inferior derecha (mucho hambre, poca distancia). ¡Nuestra fórmula funciona!

    La Zona Segura: concentración de puntos verdes en la parte superior izquierda (poca hambre, mucha distancia).

    La "Frontera de Decisión": El modelo de Machine Learning intentará encontrar matemáticamente esa línea exacta.

    El Efecto del Ruido: Hay algunos puntos rojos que "se meten" en la zona verde o viceversa. Esto es vital para que el modelo aprenda a generalizar y no a memorizar.

## 3. Preprocesamiento de los datos 🧹

Este paso es fundamental porque es el momento en el que preparamos el "material de estudio" para el algoritmo de Machine Learning.

### 3.1 Separar features (X) de target (y) ✂
---

Los algoritmos de Machine Learning están diseñados para recibir dos piezas de información por separado:

- La entrada (X): ¿Qué está pasando?

- La salida esperada (y): ¿Qué queremos predecir?

Si no quitáramos la columna ataca de X, el modelo haría "trampa": vería la respuesta dentro de los datos de entrada y no aprendería la lógica de las otras variables, simplemente copiaría lo que ve en esa columna.

    Un detalle sobre X e y (Mayúsculas vs. Minúsculas) ✍️
    
    Es una convención matemática:
        
        X (Mayúscula): Representa una Matriz (una tabla con filas y columnas).

        y (Minúscula): Representa un Vector (una sola columna de datos).

### 3.2 Escalar o normalizar las variables numéricas 📐
---

La mayoría de los modelos (como los que usan distancias o gradientes) ven un "50" y un "10" y asumen que el 50 es cinco veces más importante que el 10.

Para que el modelo sea justo, solemos transformar los datos para que todos habiten en el mismo rango (por ejemplo, de 0 a 1).

    Sin escalar: Hambre (1 a 10) vs. Distancia (1 a 50).

    Escalado: Hambre (0.1 a 1.0) vs. Distancia (0.02 a 1.0).

Ahora que los dos llegan hasta el 1.0, el modelo puede comparar su influencia real sin dejarse engañar por el tamaño original de los números.
