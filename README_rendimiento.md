# Documentación de Pruebas de Rendimiento

## Resumen de las Pruebas

Se realizaron dos pruebas de rendimiento utilizando ApacheBench (ab) para medir el comportamiento de un servidor Apache configurado en una máquina virtual.

### 1. Prueba con 100 usuarios concurrentes y 1000 peticiones
- **Usuarios Concurrentes**: 100
- **Peticiones Completas**: 1000
- **Tiempo Total de las Pruebas**: 2.116 segundos
- **Solicitudes por segundo**: 472.61 [#/sec] (media)
- **Tiempo por Solicitud (media)**: 211.592 ms
- **Tiempo de Transferencia**: 317.53 KB/s
- **Conexión más lenta**: 324 ms

#### Detalles de la Conexión
- **Conexión mínima**: 0 ms
- **Conexión media**: 1 ms
- **Conexión máxima**: 6 ms

- **Tiempo de procesamiento mínimo**: 6 ms
- **Tiempo de procesamiento medio**: 205 ms
- **Tiempo de procesamiento máximo**: 324 ms

#### Porcentaje de solicitudes servidas en un tiempo determinado
- 50% en 213 ms
- 66% en 226 ms
- 75% en 235 ms
- 80% en 239 ms
- 90% en 257 ms
- 95% en 290 ms
- 98% en 312 ms
- 99% en 317 ms

### 2. Prueba con 1000 usuarios concurrentes y 1000 peticiones
- **Usuarios Concurrentes**: 1000
- **Peticiones Completas**: 1000
- **Tiempo Total de las Pruebas**: 2.140 segundos
- **Solicitudes por segundo**: 467.19 [#/sec] (media)
- **Tiempo por Solicitud (media)**: 2140.474 ms
- **Tiempo de Transferencia**: 313.89 KB/s
- **Conexión más lenta**: 2129 ms

#### Detalles de la Conexión
- **Conexión mínima**: 0 ms
- **Conexión media**: 25 ms
- **Conexión máxima**: 37 ms

- **Tiempo de procesamiento mínimo**: 19 ms
- **Tiempo de procesamiento medio**: 1122 ms
- **Tiempo de procesamiento máximo**: 2098 ms

#### Porcentaje de solicitudes servidas en un tiempo determinado
- 50% en 1158 ms
- 66% en 1480 ms
- 75% en 1737 ms
- 80% en 1826 ms
- 90% en 2028 ms
- 95% en 2099 ms
- 98% en 2117 ms
- 99% en 2123 ms

## Opinión sobre los Resultados

1. **Prueba con 100 usuarios concurrentes y 1000 peticiones**: El servidor respondió de manera eficiente con un tiempo medio de solicitud relativamente bajo (211.592 ms) y una tasa de solicitudes por segundo de 472.61. Sin embargo, es evidente que la eficiencia mejora a medida que el número de usuarios disminuye.

2. **Prueba con 1000 usuarios concurrentes y 1000 peticiones**: Aunque el servidor sigue siendo capaz de manejar las solicitudes, el tiempo de procesamiento aumenta significativamente (1122 ms en promedio) y la tasa de solicitudes por segundo disminuye. Esto muestra que la infraestructura tiene limitaciones al manejar una mayor carga simultánea de usuarios.

En general, los resultados indican que, aunque el servidor maneja una carga razonable de usuarios, el rendimiento podría verse afectado cuando se aumentan demasiado los usuarios concurrentes y las peticiones. Se recomienda optimizar la configuración del servidor y considerar un balanceo de carga para aplicaciones de alto tráfico.