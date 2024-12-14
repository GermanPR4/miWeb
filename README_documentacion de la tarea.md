# Documentación - Pruebas de rendimiento y análisis

## Introducción

Este documento describe las pruebas de rendimiento realizadas en el servidor Apache de la máquina virtual configurada con Vagrant. Las pruebas fueron realizadas utilizando la herramienta ApacheBench para simular una carga de 100 y 1000 usuarios concurrentes, y evaluar el comportamiento del servidor bajo diferentes niveles de tráfico.

## Objetivo

El objetivo de estas pruebas es medir el rendimiento del servidor en condiciones de alta carga, analizar los resultados obtenidos y expresar una opinión sobre la capacidad del servidor para manejar múltiples peticiones simultáneas.

## Entorno de Pruebas

- **Servidor:** Apache/2.4.62
- **Sistema operativo:** Debian (Debian/bookworm64) en una máquina virtual configurada con Vagrant.
- **Herramienta utilizada para las pruebas:** ApacheBench (ab)
- **Ruta solicitada:** `/` (página principal)
- **Tamaño del documento:** 456 bytes

## Configuración de la prueba

Las pruebas se realizaron con dos configuraciones diferentes de carga de tráfico:

1. **Prueba 1:**
   - **Usuarios concurrentes:** 100
   - **Peticiones por usuario:** 1000

2. **Prueba 2:**
   - **Usuarios concurrentes:** 1000
   - **Peticiones por usuario:** 1000

## Resultados de las pruebas

### Prueba 1: 100 usuarios y 1000 peticiones

**Resumen:**
- **Tiempo total de pruebas:** 2.116 segundos
- **Peticiones completadas:** 1000
- **Peticiones fallidas:** 0
- **Respuesta no-2xx:** 1000
- **Solicitudes por segundo (promedio):** 472.61 solicitudes por segundo
- **Tiempo por solicitud (promedio):** 211.592 ms

**Detalles adicionales:**
- **Conexiones:**
  - Tiempo mínimo: 0 ms
  - Tiempo medio: 205 ms
  - Tiempo máximo: 324 ms

- **Porcentaje de solicitudes servidas en un tiempo específico:**
  - 50% en 213 ms
  - 99% en 317 ms

### Prueba 2: 1000 usuarios y 1000 peticiones

**Resumen:**
- **Tiempo total de pruebas:** 2.140 segundos
- **Peticiones completadas:** 1000
- **Peticiones fallidas:** 0
- **Respuesta no-2xx:** 1000
- **Solicitudes por segundo (promedio):** 467.19 solicitudes por segundo
- **Tiempo por solicitud (promedio):** 2140.474 ms

**Detalles adicionales:**
- **Conexiones:**
  - Tiempo mínimo: 0 ms
  - Tiempo medio: 1122 ms
  - Tiempo máximo: 2098 ms

- **Porcentaje de solicitudes servidas en un tiempo específico:**
  - 50% en 1158 ms
  - 99% en 2123 ms

## Análisis de los resultados

### Prueba 1 (100 usuarios y 1000 peticiones):

El servidor muestra una tasa de solicitudes de 472.61 solicitudes por segundo, lo que indica que puede manejar una carga moderada sin problemas. El tiempo de respuesta promedio por solicitud es de 211.592 ms, lo que es bastante eficiente bajo esta carga. La mayoría de las solicitudes (el 50%) fueron procesadas en menos de 213 ms.

### Prueba 2 (1000 usuarios y 1000 peticiones):

A medida que se incrementa el número de usuarios concurrentes, los resultados muestran un aumento en el tiempo de respuesta por solicitud (2140.474 ms). Aunque el servidor aún procesa las solicitudes sin fallos, el tiempo de respuesta se incrementa considerablemente debido al aumento de la carga. En esta prueba, el tiempo de respuesta para el 50% de las solicitudes fue de 1158 ms, y el 99% de las solicitudes fueron atendidas dentro de los 2123 ms.

## Conclusión

- **Rendimiento bajo carga moderada (100 usuarios y 1000 peticiones):** El servidor Apache muestra un buen rendimiento, con tiempos de respuesta bajos y sin fallos.
- **Rendimiento bajo alta carga (1000 usuarios y 1000 peticiones):** El servidor todavía maneja las solicitudes, pero los tiempos de respuesta aumentan significativamente, lo que podría afectar la experiencia del usuario en condiciones de alta carga.
  
Se recomienda optimizar la configuración de Apache y considerar la implementación de técnicas de balanceo de carga para manejar escenarios de alto tráfico de manera más eficiente.

## Opinión personal

En general, el rendimiento del servidor es adecuado para sitios web de tráfico moderado. Sin embargo, a medida que aumenta la carga, es necesario aplicar técnicas adicionales, como la optimización de caché, balanceo de carga y escalabilidad, para garantizar un rendimiento constante bajo condiciones más exigentes.

---

Este documento resume las pruebas realizadas y proporciona una evaluación crítica del rendimiento del servidor bajo diferentes niveles de carga.