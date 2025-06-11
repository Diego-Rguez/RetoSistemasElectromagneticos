# Reto Modelación Computacional de Sistemas Electromagneticos
"En este repositorio se encuentra tanto el código como la explicación física del reto correspondiente a la materia de Modelación Computacional de Sistemas Electromagnéticos."
## Equipo 4
## 👥 Integrantes del equipo:
- **Diego Rodríguez Sánchez** - A0174208  
- **María Fernanda Martínez Presa** - A01647132  
- **Iker Sebastián Rojo Ponce** - A01647099  
- **Ana Sofía López Martínez** - A01646849  
- **Gael Adrián Cervantes López** - A01641482  

## 🧲 RETO
Cálculo y simulación de la desaceleración por frenado magnético en una torre de caída en parques de diversiones

## 🧰 Herramientas utilizadas

Este proyecto es desarrollado utilizando **MATLAB** como entorno de programación y simulación.

## Aclaraciones
En cuanto a los archivos de runge kutta y el del calculo de aceleracion, estos no se incluyeron al repositorio ya que las funciones las creamos en el mismo archivo mlx que toda la demas parte del codigo. De igual manera las graficas generadas estan dentro del archivo pdf que se encuentra en el repositorio.
## Explicacion
### Resumen del fenomeno fisico
Cuando un imán (dipolo magnético) cae dentro de un solenoide por acción de la fuerza gravitatoria, el campo magnético del imán interacciona con el solenoide. La interacción resultante genera una fuerza de frenado magnético que ralentiza la caída del imán. El fenómeno que ocurre aquí puede ser aprovechado de muchas formas como se aprovecha en el frenado magnético sin contacto.
### Explicación general del Código
Para la simulación de nuestro freno magnético primero se definieron los parámetros de nuestro solenoide. Posteriormente se creó la malla 2D para el cálculo del campo magnético, para el cálculo del campo magnético se utilizó la formula siguiente:
  #### Ley de Biot-Savart

La Ley de Biot-Savart describe el campo magnético **𝐁** generado por un elemento de corriente **𝐈** a lo largo de un conductor:

$$
\mathbf{B}(\mathbf{r}) = \frac{\mu_0 I}{4\pi} \int \frac{d\mathbf{l} \times \mathbf{r}}{|\mathbf{r}|^3}
$$

donde:

- μ₀ es la **permeabilidad del vacío** (μ₀ = 4π × 10⁻⁷ N·A⁻²),
- I es la **corriente eléctrica** en el conductor,
- dl es el **vector diferencial de longitud** del conductor,
- r es el **vector posición** desde el elemento de corriente al punto de observación,
- × denota el **producto vectorial**.

Esta expresión permite calcular el campo magnético en un punto debido a una distribución de corriente en el espacio.
Gracias a esta fórmula pudimos calcular la contribución de cada segmento del solenoide para posteriormente hacer la sumatoria de estas contribuciones y obtener el campo magnético en cada punto.
Teniendo terminado el cálculo del campo magnético procedimos a hacer la visualización del campo magnético con mapa de colores y las líneas de flujo del mismo.

En cuanto a la simulación del dipolo comenzamos de igual manear definiendo los parámetros del mismo y haciendo nuestras funciones de Runge Kutta de orden cuatro y del cálculo de la aceleración en donde se necesitaron las siguientes formulas:
**Fuerza magnética**:  
Fm = − **m** · ∇**B**  
(momento magnético por el gradiente del campo magnético)

**Fuerza de fricción**:  
Ff = −γ · v  
(resistencia viscosa proporcional a la velocidad)

**Fuerza neta**:  
F = Fm + Ff + w  
(suma de la fuerza magnética, fricción y peso)

**Aceleración**:  
a = F / m  
(según la segunda ley de Newton)

Ya que tenemos nuestras funciones listas, hicimos el cálculo de las posiciones del dipolo en caída libre para la comparación futura que se haría. En cuanto a la caída del dipolo con freno magnético, se realizó el cálculo del gradiente para determinar la fuerza magnética de nuestro dipolo y que este verdaderamente se frenara, ya que sin gradiente no hay frenado. Finalmente se realizó la gráfica comparativa del dipolo en caída libre vs el dipolo con freno magnético y posteriormente se realizó la simulación en formato video donde se ve que efectivamente nuestro dipolo se frena casi al entrar al solenoide.


