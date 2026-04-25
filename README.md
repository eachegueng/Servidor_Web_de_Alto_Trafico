# Curso: Arquitectura de Computadoras - Grupo A
## Escenario: Servidor Web de Alto Tráfico

Este repositorio contiene la documentación técnica para el diseño de una 
infraestructura orientada a un **Servidor Web de Alto Tráfico**. Nuestra 
prioridad principal es el **rendimiento y la concurrencia**, optimizando el 
sistema para manejar miles de hilos simultáneos y reducir la latencia de 
memoria en grandes bases de datos.

## Estructura del Repositorio

<pre>
Servidor_Web_de_Alto_Trafico/
├── README.md
├── design/
│   ├── isa_choice.md
│   ├── memory_hierarchy.md
│   └── performance_analysis.md
└── references/
    └── bibliography.md
</pre>

## Decisiones Clave de Diseño

1. **ISA Seleccionada:** Arquitectura RISC (ARM de clase servidor) por su 
   eficiencia en pipelines y densidad de núcleos para manejo de concurrencia masiva.
2. **Jerarquía de Memoria:** Caché multinivel L1/L2/L3 con política de 
   reemplazo LRU, optimizada para localidad temporal en cargas de trabajo web.
3. **Rendimiento Cuantitativo:** CPI efectivo de 1.75, rendimiento de 
   1,714 MIPS, y aceleración global de 2.10x aplicando la Ley de Amdahl 
   sobre el 70% del tiempo de ejecución en red.

## Integrantes del Grupo:

- Sharon Marroquin
- Eddy Cheguen
- David Escobar
- Ismael Liquez
- Gustavo Ortiz
- Wesley López
- Luis Franco
- Daniela López
