# Mini-proyecto: Arquitectura de Computadores - Grupo A

## Escenario: Servidor Web de Alto Tráfico
Este repositorio contiene la documentación técnica para el diseño de una infraestructura orientada a un *Servidor Web de Alto Tráfico. Nuestra prioridad principal es el **rendimiento y la concurrencia*, optimizando el sistema para manejar miles de hilos simultáneos y reducir la latencia de memoria en grandes bases de datos.

## Estructura del Repositorio
La documentación se organiza de la siguiente manera, cumpliendo con los requisitos obligatorios:

```
Servidor_Web_de_Alto_Trafico/
├── README.md
├── design/
│   ├── isa_choice.md
│   ├── memory_hierarchy.md
│   └── performance_analysis.md
└── references/
    └── bibliography.md
```

## Decisiones Clave de Diseño
1.⁠ ⁠*Prioridad de Concurrencia: El sistema está diseñado para maximizar el *throughput mediante una ISA que favorezca la ejecución eficiente de múltiples hilos.
2.⁠ ⁠*Optimización de Memoria*: Se ha implementado una jerarquía de caché agresiva para combatir la latencia en el acceso a grandes volúmenes de datos.
3.⁠ ⁠*Análisis de Rendimiento*: Utilizamos métricas cuantitativas para asegurar que las mejoras en componentes críticos (como la red) se traduzcan en una aceleración global real del sistema.

## Integrantes del Grupo
