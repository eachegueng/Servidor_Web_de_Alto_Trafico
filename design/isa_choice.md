# Selección de la ISA – Servidor Web de Alto Tráfico

## Arquitectura Seleccionada: RISC (ARM de clase servidor)

Para un servidor web que prioriza la concurrencia y la ejecución de miles 
de hilos simultáneos, se selecciona la arquitectura **RISC (ARM de clase 
servidor / RISC-V)** por encima de CISC (x86), por las razones técnicas 
detalladas a continuación.

## Comparación RISC vs CISC

| Criterio               | RISC (ARM)                        | CISC (x86)                        |
|------------------------|-----------------------------------|-----------------------------------|
| Longitud de instrucción| Fija (32 bits)                    | Variable (1–15 bytes)             |
| Decodificación         | Simple y rápida                   | Compleja, mayor latencia          |
| Densidad de núcleos    | Alta (más núcleos por chip)       | Menor densidad térmica            |
| Consumo energético     | Bajo                              | Alto                              |
| Uso ideal              | Servidores concurrentes, IoT, HPC | Aplicaciones de escritorio legacy |

## Justificación Técnica

### 1. Eficiencia en el Pipeline
Según Hennessy & Patterson, los diseños RISC facilitan 
pipelines más profundos y eficientes. Al tener instrucciones de longitud 
fija, se reduce el tiempo de decodificación, permitiendo que el procesador 
dedique más ciclos a la ejecución real de solicitudes HTTP.

### 2. Paralelismo Masivo
La arquitectura ARM permite integrar una mayor densidad de núcleos por chip 
en comparación con CISC (x86), lo cual es crítico para manejar miles de 
hilos de ejecución concurrentes en servidores como Nginx o Apache.

### 3. Rendimiento por Watt
Se minimiza la generación de calor, permitiendo mantener frecuencias 
estables durante picos de tráfico sostenido, característica esencial en 
centros de datos de alta disponibilidad.

## Conclusión

La arquitectura RISC (ARM) es la elección óptima para el escenario de 
Servidor Web de Alto Tráfico, ya que maximiza la concurrencia, 
reduce la latencia de decodificación y permite escalar horizontalmente el 
número de núcleos sin comprometer la estabilidad térmica del sistema.
