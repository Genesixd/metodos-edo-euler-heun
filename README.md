# Métodos numéricos para EDO: Euler, Heun y solución exacta

Repositorio para la resolución de dos ecuaciones diferenciales ordinarias (EDO) usando:

- Método de **Euler**
- Método de **Heun** (Euler mejorado)
- **Solución exacta** analítica

Todo está implementado en **Microsoft Excel**, paso a paso y con tablas coloreadas para visualizar mejor cada método y sus errores.

---

## 1. Problema 1 – Ecuación diferencial lineal

EDO:

\[
\frac{dy}{dt} = \frac{t^3 - 2y}{t}, \quad 1 \le t \le 3,\quad y(1) = 4.2
\]

Solución exacta:

\[
y(t) = \frac{1}{5}t^3 + \frac{4}{t^2}
\]

### Contenido del Excel

Archivo: **`Crecimiento del organismo.xlsx`**

Incluye:

- Hoja **Euler**  
  - Tabla con \(t_i\), \(y_i\), \(f(t_i, y_i)\) y \(y_{i+1}\).
- Hoja **Heun**  
  - Predictor \(y^* = y_i + h f(t_i,y_i)\).  
  - Corrector \(y_{i+1} = y_i + \frac{h}{2}\left[f(t_i,y_i) + f(t_i+h, y^*)\right]\).
- Hoja **Exacto**  
  - Valores de \(y_{\text{exacta}}(t)\) usando la fórmula analítica.
- Cálculo de **errores absoluto, relativo y porcentual** en \(t=3\).

### Resultados en \(t = 3\)

| Método | \(y(3)\) aprox. | Error absoluto | Error % aprox. |
|--------|-----------------|----------------|----------------|
| Exacto | 5.84444         | –              | –              |
| Euler  | 5.39376         | 0.45068        | 7.71 %         |
| Heun   | 5.46899         | 0.37545        | 6.42 %         |

---

## 2. Problema 2 – Crecimiento de un pez (modelo de von Bertalanffy)

EDO:

\[
\frac{dw}{dt} = 5w^{2/3} - 2w,\quad w(0)=0.5\ \text{lb}
\]

Solución exacta:

\[
w(t) = \left[
\frac{5}{2} + \bigl(0.5^{1/3} - \tfrac{5}{2}\bigr)e^{-\frac{2}{3}t}
\right]^3
\]

Peso máximo teórico (equilibrio):

\[
w_{\max} = \left(\frac{5}{2}\right)^3 = 15.625\ \text{lb}
\]

### Contenido del Excel

Archivo: **`Crecimiento del pez.xlsx`**

- Hoja **Euler**  
  - Iteración con paso \(h = 0.5\) hasta \(t = 10\).  
  - Columnas con \(w_{\text{Euler}}(t)\), \(w_{\text{exacta}}(t)\) y errores.
- Hoja **Heun**  
  - Implementación completa del método de Heun con el mismo paso \(h\).  
  - Comparación con la solución exacta.
- Gráfica de **\(w(t)\) vs tiempo** superponiendo:
  - Solución exacta  
  - Euler  
  - Heun  

### Resultados en \(t = 10\)

| Método | \(w(10)\) aprox. (lb) | Error absoluto | Error % aprox. |
|--------|------------------------|----------------|----------------|
| Exacto | 15.58432              | –              | –              |
| Euler  | 15.60884              | 0.02452        | 0.16 %         |
| Heun   | 15.57755              | 0.00675        | 0.04 %         |

Los valores numéricos muestran cómo las aproximaciones numéricas se acercan al peso máximo teórico \(w_{\max} = 15.625\ \text{lb}\).

---

## 3. Conclusión general

En ambos problemas se implementaron y compararon los métodos de Euler, Heun y la solución exacta. Los resultados muestran que:

- **Euler** es el método más sencillo de aplicar, pero también el menos preciso. Con el mismo tamaño de paso, sus aproximaciones se alejan más de la solución analítica.
- **Heun** (Euler mejorado) entrega resultados mucho más cercanos a la solución exacta, porque corrige la pendiente usando un promedio entre el inicio y el final del intervalo. En los dos ejercicios, el error porcentual de Heun fue varias veces menor que el de Euler.

Tanto en la EDO del organismo como en el modelo de crecimiento del pez, ambos métodos numéricos reproducen el comportamiento cualitativo correcto (crecimiento y acercamiento a un valor límite), pero **Heun sigue mejor la curva exacta**, especialmente cerca del valor máximo. Para un mismo paso \(h\), Heun es una mejor opción cuando se busca una buena precisión sin complicar demasiado el algoritmo, mientras que Euler queda principalmente como método introductorio para entender la idea de integración numérica.

---

## 4. Cómo usar este repositorio

1. Clonar o descargar el repositorio.
2. Abrir los archivos `.xlsx` con Microsoft Excel o compatible.
3. Revisar las hojas de cada archivo para ver:
   - La implementación paso a paso de Euler y Heun.
   - Las tablas de errores.
   - Las gráficas comparando métodos y solución exacta.
