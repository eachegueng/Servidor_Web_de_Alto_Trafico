# Diseño de Jerarquía de Memoria

### Organización Multinivel
Para minimizar la latencia en el acceso a grandes bases de datos, implementamos la siguiente estructura:

* *Caché L1 (32KB - 64KB):* Dividida en Instrucciones y Datos para evitar conflictos durante el procesamiento de requests.
* *Caché L2 (256KB - 512KB):* Privada por núcleo, reduciendo el tiempo de acceso a datos locales de cada proceso.
* *Caché L3 (8MB - 32MB):* Compartida entre todos los núcleos. Es vital para la comunicación entre hilos concurrentes y evitar accesos costosos a la RAM.
* *Almacenamiento SSD NVMe:* Para la entrega rápida de contenido estático (HTML/CSS).

### Política de Reemplazo: LRU (Least Recently Used)
Se selecciona *LRU* como la política principal. Para un servidor web, los datos accedidos recientemente (como encabezados de página o sesiones activas) tienen alta probabilidad de ser requeridos nuevamente.
