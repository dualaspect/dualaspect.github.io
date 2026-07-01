---
title: Creando arte con matemáticas 
categories: [Personal, Science]
---

Las matemáticas y la programación son, a mi juicio, una forma de la poesía. La
programación se condice tanto con esta definición que incluso se escribe en
verso, aunque esta sea la similitud más superficial entre ambas. Lo
cierto es que la poesía, o al menos la buena poesía, satisface ciertas
propiedades que las matemáticas y el código también: $(a)$ es doblemente
susceptible a una apreciación abstracta y a una apreciación visual; $(b)$ aunque
cada unidad (variable, línea de código, verso) sirva a un único sentido, su
papel semántico nunca es del todo unívoco; $(c)$ en última instancia, el
contenido o la semántica sirve, por sobre todo, a revelar una forma o una
estructura, como expresó el propio Mallarmé en su poema *Salut*:

>Rien, cette écume, vierge vers<br>
>À ne désigner que la coupe

Esta lista no es exhaustiva, pero acaso baste para inspirar la idea de que una
matemática o una programación artística son posibles. Y eso es lo que deseo
exponer en este escrito con un ejemplo concreto.

Nuestra historia comienza con un concepto que me es ajeno desde una perspectiva
técnica: el de atractor. Matemáticamente hablando, dado un sistema dinámico $S$,
un atractor es el conjunto de estados a los cuales el sistema tiende a
evolucionar incluso partiendo desde condiciones iniciales muy diversas. La
definición formal de un atractor no es particularmente compleja, por ricas que
sean las propiedades del concepto. En general, si $f(t, \vec{x})$ describe un
sistema que en el tiempo $t$ está parametrizado en $\vec{x}$, un atractor es un
subconjunto $A$ del conjunto de estados posibles $S$ que satisface:

- Si $a \in A$, entonces $f(t, a) \in A$ para $t > 0$. En lenguaje humano, si el
sistema está en un estado atractor, seguirá estándolo en el futuro.
- Existe un entorno $B(A)$ de $A$ consistente de todos los puntos que conducen a
$A$ en el límite $t \to \infty$. En lenguaje humano, los estados cercanos pero
exteriores al atractor tienden a él en el tiempo.
- No existe ningún sub-espacio de $A$ (no vacío) que cumpla las dos propiedades
anteriores. Es decir, un atractor no tiene otros atractores dentro de él:
comprende *un* conjunto de estados de atracción y no más.

Existe un atractor en particular, descubierto y popularizado por [Clifford
Pickover](https://es.wikipedia.org/wiki/Clifford_Pickover), que tiene cierto
interés artístico. Se define como

$$
\begin{align}
    x_{n+1} &= \sin(a y_n) + c \cos(a x_n) \\\\
    y_{n+1} &= \sin(b x_n) + d \cos(b y_n)
\end{align}
$$

En rigor, estas ecuaciones no son un atractor, porque no son un conjunto de
estados. Más bien, son el sistema cuyo atractor es revelado cuando producimos
suficientes instancias de pares $(x, y)$. Implementar este sistema en Python es
sumamente simple, y podemos graficar los pares de puntos resultantes. Veremos
que los puntos generados no están dispersos aleatoriamente, sino que se agrupan
en un orden interesante. El conjunto de coordenadas en torno a las cuales los
puntos se agrupan conforman el atractor, y el patrón obtenido es hermoso. Por
ejemplo:

![Clifford](../Images/Clifford1.png)

Esta es la esencia de cómo los atractores nos permiten generar imágenes
hermosas: en un espacio bidimensional, la simulación de cualquier sistema
dinámico que posea atractores producirá patrones de interés. La riqueza visual
de los patrones producidos puede aumentarse si, por ejemplo, hacemos variar los
meta-parámetros del sistema (en este caso, $a, c, b$ y $d$) con el tiempo. La
forma más fácil de hacer esto es tomar un parámetro $\varphi$ arbitrario y
definirlo como $\varphi(t) = \alpha + \beta \sin(t)$, es decir hacer que el
parámetro fluctúe oscilatoriamente alrededor de un centro $\alpha$. El tiempo
$t$ puede hacerse avanzar de $0$ a $2\pi$ creando un bucle perfecto:

$$
t = (\text{frame}/k) \cdot 2\pi
$$

con $k$ la cantidad de frames en la animación. Para hacer la cosa todavía más
interesante, podemos hacer que el color de cada punto también varíe de manera
bonita, podemos asignar al punto $(x, y)$ en cada instante de tiempo el color

$$C_i = \sin(x_i \cdot a) + \cos(y_i \cdot b)$$

¿El resultado? Esta hermosura.

![CliffordAnimation](../Images/clifford_dynamic_colors.gif)

--- 

Este escrito ha sido esquemático y no ha pretendido ser más que eso. Existen
otros métodos matemáticos para generar patrones bellos, como por ejemplo
ilustrar las raíces de ciertos polinomios complejos. Baste este pequeño ejemplo
con las ecuaciones de Clifford para mostrar, una vez más, la poesía de las
matemáticas.







