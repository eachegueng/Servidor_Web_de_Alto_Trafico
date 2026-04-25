# Análisis Cuantitativo de Rendimiento

## 1. Ecuación Fundamental del Rendimiento

Basándonos en Hennessy & Patterson (2025, Cap. 1), calculamos el rendimiento 
del servidor mediante la ecuación de Tiempo de CPU:

$$Tiempo\ de\ CPU = IC \times CPI \times Periodo\ de\ Reloj$$

## 2. Cálculo de CPI y MIPS

Asumimos los siguientes parámetros para un procesador ARM de servidor 
operando a **3.0 GHz**:

- **Frecuencia de reloj:** f = 3.0 GHz → Periodo de reloj = 0.333 ns  
- **IC estimado por request HTTP:** 1,500 instrucciones

### Distribución de instrucciones y CPI por tipo

| Tipo de Instrucción | Frecuencia | CPI individual | Contribución al CPI |
|---------------------|------------|----------------|----------------------|
| ALU / Lógica        | 45%        | 1              | 0.45                 |
| Load / Store        | 35%        | 2              | 0.70                 |
| Control (branches)  | 20%        | 3              | 0.60                 |
| **TOTAL**           | **100%**   | —              | **1.75**             |

**CPI efectivo = 0.45 + 0.70 + 0.60 = 1.75**

### Tiempo de CPU por request

$$Tiempo\ de\ CPU = 1{,}500 \times 1.75 \times \frac{1}{3{,}000{,}000{,}000} \approx 875\ ns\ por\ request$$

### Cálculo de MIPS

$$MIPS = \frac{Frecuencia\ de\ Reloj}{CPI} = \frac{3{,}000\ MHz}{1.75} \approx 1{,}714\ MIPS$$

Esto indica que el procesador ARM seleccionado puede ejecutar aproximadamente 
**1,714 millones de instrucciones por segundo**, lo que respalda su capacidad 
para manejar miles de requests concurrentes.

## 3. Aplicación de la Ley de Amdahl

Utilizamos la Ley de Amdahl citada por Stallings (2015, Cap. 2) para 
proyectar mejoras de optimización.

**Escenario:** Si optimizamos el procesamiento de hilos de red (que representa 
el **70%** del tiempo de ejecución, $f = 0.7$) para que sea **4 veces más 
rápido** ($k = 4$):

$$Aceleración\ Global = \frac{1}{(1 - f) + \frac{f}{k}} = \frac{1}{(1 - 0.7) + \frac{0.7}{4}} = \frac{1}{0.3 + 0.175} = \frac{1}{0.475} \approx 2.10$$

### Interpretación

Una mejora focalizada en el módulo de concurrencia de red produce una 
**aceleración global de 2.10x** sobre el sistema completo. Esto demuestra 
que aun optimizando únicamente el componente más crítico, el rendimiento 
general no puede duplicarse infinitamente — validando la importancia de 
un diseño balanceado entre ISA, jerarquía de memoria y red.

## 4. Resumen de Métricas

| Métrica             | Valor calculado       |
|---------------------|-----------------------|
| CPI efectivo        | 1.75                  |
| Tiempo por request  | ≈ 875 ns              |
| MIPS                | ≈ 1,714 MIPS          |
| Aceleración (Amdahl)| 2.10x                 |
| Frecuencia de reloj | 3.0 GHz               |
