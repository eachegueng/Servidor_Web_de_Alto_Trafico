# Diseño de Jerarquía de Memoria

## Organización Multinivel

Para minimizar la latencia en el acceso a grandes bases de datos y contenido 
estático, implementamos la siguiente estructura de caché, basada en los 
principios de localidad temporal y espacial descritos por Stallings.

| Nivel  | Tamaño        | Tipo         | Latencia aprox. | Característica                        |
|--------|---------------|--------------|-----------------|---------------------------------------|
| L1     | 32KB – 64KB   | Privada/núcleo | 4 ciclos       | Dividida en instrucciones y datos     |
| L2     | 256KB – 512KB | Privada/núcleo | 12 ciclos      | Reduce accesos a L3 por proceso       |
| L3     | 8MB – 32MB    | Compartida   | 40 ciclos       | Comunicación entre hilos concurrentes |
| RAM    | 64GB – 128GB  | Principal    | ~200 ciclos     | Almacenamiento de sesiones activas    |
| SSD NVMe| 1TB+         | Secundario   | ~100,000 ciclos | Entrega de contenido estático         |

### Caché L1 (32KB – 64KB)
Dividida en caché de instrucciones y caché de datos para evitar conflictos 
durante el procesamiento paralelo de requests. Su reducido tamaño garantiza 
latencias mínimas de acceso.

### Caché L2 (256KB – 512KB)
Privada por núcleo, reduciendo el tiempo de acceso a datos locales de cada 
proceso o hilo de ejecución. Actúa como filtro antes de acceder a la L3 
compartida.

### Caché L3 (8MB – 32MB)
Compartida entre todos los núcleos. Es vital para la comunicación entre 
hilos concurrentes y para evitar accesos costosos a la RAM principal, 
especialmente durante picos de tráfico web.

### Almacenamiento SSD NVMe
Para la entrega rápida de contenido estático (HTML, CSS, imágenes), 
reduciendo la dependencia de la RAM para datos que no cambian frecuentemente.

## Política de Reemplazo: LRU (Least Recently Used)

Se selecciona *LRU* como la política de reemplazo principal para todos 
los niveles de caché.

LRU es la política con mejor comportamiento 
en cargas de trabajo con alta *localidad temporal*, reemplazando el bloque 
que lleva más tiempo sin ser referenciado. Para un servidor web de alto 
tráfico, los datos accedidos recientemente —como encabezados de página, 
tokens de sesión activos o respuestas cacheadas— tienen alta probabilidad 
de ser requeridos nuevamente en los siguientes ciclos de request.

### Justificación de LRU sobre otras políticas

| Política | Descripción                        | Desventaja para nuestro escenario         |
|----------|------------------------------------|-------------------------------------------|
| LRU      | Reemplaza el menos recientemente usado | Óptima para localidad temporal web    |
| FIFO     | Reemplaza el más antiguo           | Ignora frecuencia de acceso               |
| Aleatorio| Reemplaza un bloque al azar        | Impredecible, menor hit rate              |
| LFU      | Reemplaza el menos frecuente       | Costosa de implementar en hardware        |
