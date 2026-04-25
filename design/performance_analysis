# Análisis Cuantitativo de Rendimiento

## 1. Ecuación Fundamental del Rendimiento
Basándonos en **Hennessy & Patterson (2025)**, calculamos el rendimiento del servidor mediante la ecuación de Tiempo de CPU:

$$Tiempo\ de\ CPU = IC \times CPI \times Periodo\ de\ Reloj$$

* **IC (Instruction Count):** Optimizado por la ISA RISC, permitiendo un flujo constante de instrucciones simples.
* **CPI (Cycles Per Instruction):** En nuestro escenario de alto tráfico, el CPI se ve afectado por las esperas de memoria (stalls). Proyectamos un **CPI efectivo de 1.2 a 1.5** considerando la jerarquía de memoria diseñada en la sección anterior.
* **Periodo de Reloj:** Ajustado para maximizar el throughput sin comprometer la estabilidad térmica.

## 2. Aplicación de la Ley de Amdahl
Utilizamos la Ley de Amdahl citada por **Stallings (2015)** para proyectar mejoras. 

**Escenario:** Si optimizamos el procesamiento de hilos de red (que representa el 70% del tiempo de ejecución, $f = 0.7$) para que sea 4 veces más rápido ($k = 4$):

$$Aceleración\ Global = \frac{1}{(1 - 0.7) + \frac{0.7}{4}} = \frac{1}{0.3 + 0.175} = 2.10$$

Esto demuestra que una mejora focalizada en la concurrencia duplica el rendimiento global del servidor.
