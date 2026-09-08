# Requerimientos no funcionales

| # | Atributo | Metrica | Umbral | Condicion de carga | Verificacion | Consecuencia si no se cumple |
|---|---|---|---|---|---|---|
| 1 | Rendimiento | p95 de latencia | menor a 400 ms | 200 usuarios concurrentes | Prueba de carga | El usuario abandona la reserva |
| 2 | Disponibilidad | Tiempo de actividad | 99.9% | 24/7 | Monitoreo continuo | El servicio no cumple SLA |
| 3 | Seguridad | Tiempo de expiración de sesión | 30 minutos | Usuarios activos | Pruebas de seguridad | Riesgo de acceso no autorizado |
| 4 | Mantenibilidad | Tiempo de despliegue | < 15 minutos | Actualización de versión | Prueba de CI/CD | Tiempo de inactividad largo |
| 5 | Capacidad | Máximo de citas | 1000 citas/día | Demanda máxima | Prueba de estrés | El sistema no puede escalar |

## Escenarios completos

### Escenario 1: Reserva de cita en hora pico
- **Fuente:** Usuario final
- **Estímulo:** Solicitud de reserva de cita
- **Artefacto:** API de reservas
- **Entorno:** Horas de mayor demanda (8am - 10am)
- **Respuesta:** Confirmación de reserva en menos de 400ms
- **Medida:** p95 de latencia en pruebas de carga

### Escenario 2: Caída del servicio de base de datos
- **Fuente:** Base de datos
- **Estímulo:** Pérdida de conexión
- **Artefacto:** Servicio de citas
- **Entorno:** Producción
- **Respuesta:** Failover automático en menos de 60 segundos
- **Medida:** Tiempo de recuperación

### Escenario 3: Intento de acceso no autorizado
- **Fuente:** Atacante externo
- **Estímulo:** Múltiples intentos de login fallidos
- **Artefacto:** Sistema de autenticación
- **Entorno:** Producción
- **Respuesta:** Bloqueo de IP y notificación de seguridad
- **Medida:** Tiempo de detección y bloqueo