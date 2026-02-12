# Capítulo 14.1 — Funciones de varias variables
### Stewart, Cálculo de Varias Variables (7ª ed.) — Resumen humano

---

## La idea central: salir del mundo de una sola variable

Todo el cálculo que estudié antes asumía que una función dependía de **una sola cosa**: `y = f(x)`. Pero el mundo real no funciona así. La temperatura que siento afuera depende de la temperatura del aire *y* de la velocidad del viento. El volumen de un cilindro depende del radio *y* de la altura. La producción de una empresa depende del trabajo *y* del capital invertido.

Ese es el salto que hace este capítulo: pasar de funciones de una variable a **funciones de dos o más variables**.

---

## 1. ¿Qué es una función de dos variables?

Una función `f` de dos variables es simplemente una regla que toma un par ordenado `(x, y)` y le asigna **un único número real** `z = f(x, y)`.

- `x` y `y` son las **variables independientes** (lo que controlo o conozco).
- `z` es la **variable dependiente** (lo que obtengo como resultado).

El **dominio** de `f` es el conjunto `D` de todos los pares `(x, y)` para los cuales la expresión tiene sentido (no hay raíces de negativos, no hay divisiones entre cero, etc.). El **rango** es el conjunto de todos los valores que puede tomar `z`.

### Ejemplo real: el cilindro

El volumen de un cilindro circular es:

```
V(r, h) = π r² h
```

Aquí `V` depende de dos cosas: del radio `r` y de la altura `h`. Si duplico el radio, el volumen se cuadruplica. Si duplico la altura, el volumen se duplica. Eso ya no lo captura una función de una sola variable.

---

## 2. Cuatro formas de ver la misma función

Stewart insiste en ver cada función desde **cuatro ángulos distintos**. Esto no es decoración: cada perspectiva ilumina algo que las otras no muestran bien.

### 📝 Verbal (con palabras)
La temperatura real que siente una persona depende de la temperatura del aire y de la velocidad del viento. Eso ya es una función de dos variables, descrita con palabras.

### 📊 Numérica (tabla de valores)
El **índice de temperatura de sensación** (wind chill) es un gran ejemplo. El National Weather Service lo modela como `W = f(T, v)`, donde `T` es la temperatura en °C y `v` es la velocidad del viento en km/h.

La tabla dice, por ejemplo, que si `T = -5°C` y `v = 50 km/h`, entonces:

```
f(-5, 50) = -15
```

Es decir, aunque el termómetro marque -5°C, el cuerpo lo percibe como -15°C. La tabla captura esta función sin necesidad de una fórmula.

### 🔣 Algebraica (fórmula)
Cuando sí tenemos una fórmula, podemos evaluar y determinar el dominio de forma exacta.

**Ejemplo:** sea `f(x, y) = √(x + y + 1) / (x - 1)`

Para evaluar `f(3, 2)`:

```
f(3, 2) = √(3 + 2 + 1) / (3 - 1) = √6 / 2
```

El dominio requiere dos condiciones simultáneas:
- Lo que está dentro de la raíz debe ser ≥ 0: `x + y + 1 ≥ 0`, o sea `y ≥ -x - 1`
- El denominador no puede ser cero: `x ≠ 1`

El dominio `D = {(x, y) | x + y + 1 ≥ 0, x ≠ 1}`.

### 🗺️ Visual (gráfica y curvas de nivel)
Las dos formas visuales son la **gráfica en 3D** y el **mapa de curvas de nivel**. Las explico a continuación.

---

## 3. La gráfica: una superficie en el espacio 3D

Si `f` es una función de dos variables con dominio `D`, su gráfica es el conjunto de todos los puntos `(x, y, z)` en ℝ³ tales que `z = f(x, y)`.

Dicho de otra manera: la gráfica de `f` ya no es una curva, es una **superficie** que flota en el espacio tridimensional, directamente encima (o debajo) de su dominio en el plano `xy`.

### Intuición geométrica
Pienso en esto así: el plano `xy` es el "suelo". Para cada punto del suelo `(x, y)`, la función `f` me dice a qué "altura" `z` está la superficie. La colección de todas esas alturas forma la superficie.

### Ejemplos concretos

**Plano:** `f(x, y) = 6 - 3x - 2y`  
La gráfica es un plano en 3D. Intercepta el eje `x` en 2, el eje `y` en 3 y el eje `z` en 6.

**Semiesfera:** `g(x, y) = √(9 - x² - y²)`  
Al elevar al cuadrado: `z² = 9 - x² - y²`, es decir `x² + y² + z² = 9`. Eso es una esfera de radio 3 centrada en el origen. Pero como `z ≥ 0` (raíz cuadrada), la gráfica es solo el **hemisferio superior**.

> **Truco:** no toda esfera puede representarse como una función. La esfera completa no pasa la "prueba de la línea vertical" generalizada: para cada `(x, y)` habría dos valores de `z` (uno arriba y uno abajo). Por eso necesito dos funciones separadas para los dos hemisferios.

**Paraboloide elíptico:** `h(x, y) = 4x² + y²`  
Las trazas horizontales (cortes con planos `z = k`) son elipses. Las trazas verticales son parábolas.

---

## 4. La función de producción de Cobb-Douglas: un caso real de dos variables

En 1928, los economistas Cobb y Douglas modelaron la producción de la economía estadounidense entre 1899 y 1922 con la función:

```
P(L, K) = b · L^α · K^(1-α)
```

donde `P` es la producción total, `L` es la cantidad de trabajo (horas-hombre) y `K` es el capital invertido (maquinaria, edificios, etc.).

Usando mínimos cuadrados sobre los datos reales del gobierno, encontraron:

```
P(L, K) = 1.01 · L^0.75 · K^0.25
```

**Prueba de fuego del modelo:** para 1910, `L = 147` y `K = 208`:

```
P(147, 208) = 1.01 · (147)^0.75 · (208)^0.25 ≈ 161.9
```

El valor real fue 159. Para 1920 (`L = 194`, `K = 407`): el modelo da ≈ 235.8, el real fue 231. Nada mal para una fórmula de solo dos variables.

> **Punto de aprendizaje:** las funciones de varias variables no son abstractas. Esta función describe algo tan concreto como el crecimiento económico de un país. El dominio es `{(L, K) | L > 0, K > 0}` porque tanto el trabajo como el capital son cantidades positivas en la realidad.

---

## 5. Curvas de nivel: ver una superficie en 2D

Una **curva de nivel** de `f` es el conjunto de puntos donde la función toma un valor constante `k`:

```
f(x, y) = k
```

Geométricamente, es la proyección al plano `xy` del corte horizontal de la superficie a la altura `z = k`.

La analogía perfecta es un **mapa topográfico**: cada línea del mapa une puntos del terreno que están a la misma altitud. Si camino a lo largo de una de esas líneas, no subo ni bajo.

### Cómo leer un mapa de curvas de nivel

- Donde las curvas están **muy juntas**: la superficie tiene una pendiente pronunciada (el terreno sube rápido).
- Donde las curvas están **muy separadas**: la superficie es casi plana.

### Ejemplo: función lineal

Para `f(x, y) = 6 - 3x - 2y`, las curvas de nivel `f(x, y) = k` son:

```
6 - 3x - 2y = k  →  3x + 2y = 6 - k
```

Estas son **rectas paralelas** con pendiente `-3/2`. Eso tiene sentido porque la gráfica de `f` es un plano, y los cortes horizontales de un plano siempre son rectas paralelas entre sí.

### Ejemplo: semiesfera

Para `g(x, y) = √(9 - x² - y²)`, las curvas de nivel son:

```
√(9 - x² - y²) = k  →  x² + y² = 9 - k²
```

Estas son **círculos concéntricos** centrados en el origen con radio `√(9 - k²)`. Cuando `k` crece (me acerco al polo de la esfera), el radio disminuye. Cuando `k = 3`, el círculo colapsa a un punto: el tope de la semiesfera.

### Curvas de nivel en economía

Para la función de Cobb-Douglas `P(L, K) = 1.01 L^0.75 K^0.25`, una curva de nivel es:

```
1.01 L^0.75 K^0.25 = P₀
```

Fijando un nivel de producción `P₀`, la curva muestra todas las combinaciones de trabajo `L` y capital `K` que producen exactamente ese nivel. En economía estas curvas se llaman **isocuantas**. Si `L` sube, `K` baja para mantener la producción constante, y viceversa.

---

## 6. Funciones de tres o más variables

La extensión natural es `z = f(x, y, z)` o incluso más variables. Una función de tres variables asigna un número real a cada terna ordenada `(x, y, z)` en su dominio `D ⊆ ℝ³`.

**Ejemplo:** `f(x, y, z) = ln(z - y) + xy · sen(z)`

El dominio es el conjunto de ternas donde `z - y > 0`, es decir `z > y`. Geométricamente, son todos los puntos por encima del plano `z = y`. Eso es un **semiespeacio** en ℝ³.

### El problema visual: cuatro dimensiones

Ya no puedo graficar `f(x, y, z)` porque necesitaría un eje adicional para el valor de `f`, y no tenemos percepción de cuatro dimensiones espaciales. El sustituto son las **superficies de nivel**:

```
f(x, y, z) = k
```

### Ejemplo: esferas concéntricas

Para `f(x, y, z) = x² + y² + z²`, las superficies de nivel son:

```
x² + y² + z² = k
```

Estas son **esferas concéntricas** centradas en el origen con radio `√k`. Cuando el punto `(x, y, z)` se mueve sobre cualquiera de estas esferas, el valor de `f` permanece constante.

> **Analogía clave:** la relación entre curvas de nivel y superficies de nivel es exactamente la misma que la relación entre las curvas en un mapa topográfico y la montaña real. Las curvas de nivel son la versión 2D, las superficies de nivel son la versión 3D.

---

## Resumen visual de los conceptos

| Dimensión de entrada | Nombre del conjunto | Cómo se visualiza |
|---|---|---|
| `f(x, y)` — 2 variables | Curvas de nivel `f(x,y) = k` | Curvas en el plano `xy` |
| `f(x, y, z)` — 3 variables | Superficies de nivel `f(x,y,z) = k` | Superficies en ℝ³ |

---

## Lo que hay que llevarse del capítulo

1. **Una función de dos variables** es una regla `z = f(x, y)` que acepta pares y devuelve un número. Su gráfica es una superficie en 3D.

2. **El dominio** es el conjunto de pares `(x, y)` donde la función está bien definida. Para encontrarlo, aplico las mismas restricciones de siempre: no dividir entre cero, no raíces de negativos, no logaritmos de no positivos.

3. **Las curvas de nivel** `f(x, y) = k` son la herramienta clave para visualizar funciones de dos variables en 2D. Curvas juntas = pendiente pronunciada. Curvas separadas = superficie plana.

4. **Las superficies de nivel** `f(x, y, z) = k` son el análogo para funciones de tres variables.

5. Las funciones de varias variables no son solo matemáticas abstractas: modelan temperatura, producción económica, volúmenes, índices climáticos, y prácticamente cualquier fenómeno real que depende de más de un factor.
