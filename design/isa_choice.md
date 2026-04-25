# Selección de la ISA – Servidor Web de Alto Tráfico

### Arquitectura Seleccionada: RISC (ARM / RISC-V)
Para un servidor web que prioriza la concurrencia y la ejecución de miles de hilos, se selecciona la arquitectura *RISC (ARM de clase servidor)*.

### Justificación Técnica
1. *Eficiencia en el Pipeline:* Según *Hennessy y Patterson*, los diseños RISC facilitan pipelines más profundos y eficientes. Al tener instrucciones de longitud fija, se reduce el tiempo de decodificación, permitiendo que el procesador dedique más ciclos a la ejecución real de solicitudes.
2. *Paralelismo Masivo:* La arquitectura ARM permite integrar una mayor densidad de núcleos por chip en comparación con CISC (x86), lo cual es crítico para manejar miles de hilos de ejecución en servidores como Nginx o Apache.
3. *Rendimiento/Consumo:* Se minimiza la generación de calor, permitiendo mantener frecuencias estables durante picos de tráfico.
