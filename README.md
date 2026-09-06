# HOMI · Diplomado en Liderazgo y Gestión de Unidades Funcionales de Enfermería
## Gobierno y arquitectura BUK

**Versión inicial:** 0.1.0  
**Fecha:** 2026-09-06  
**Propietario funcional:** Formación y Desarrollo  

Este repositorio define la arquitectura técnica, operativa y de datos para gobernar el Diplomado en BUK sin convertirlo en un megacurso rígido. La lógica pedagógica prevalece sobre la tecnología.

## Principio rector

**Problema → capacidad → recurso → acción → evidencia → criterio → retroalimentación → continuidad/transferencia**

BUK funciona como **orquestador y sistema operativo de ejecución/trazabilidad**. GitHub funciona como **fuente versionada de arquitectura, configuración, plantillas y decisiones de diseño**. GitHub **no almacena datos personales, evidencias de participantes ni información clínica**.

## Arquitectura de macro a micro

1. **Programa** — Diplomado completo y reglas globales.
2. **Trayectoria** — Secuencia longitudinal de módulos/sesiones y prerrequisitos necesarios.
3. **Sesión** — Unidad razonable de actualización; cada sesión tiene un curso E-learning independiente asociado.
4. **Actividad** — Acción verificable dentro de la sesión.
5. **Evidencia/Criterio** — Producto o traza mínima y regla para interpretar el logro.
6. **Evento de trazabilidad** — Registro de estados, entregas, evaluaciones, excepciones y continuidad.

## Repositorio

- `docs/ARCHITECTURA.md`: arquitectura integral, entradas, salidas y flujo end-to-end.
- `docs/MODELO_DATOS.md`: objetos, relaciones, estados y trazabilidad.
- `docs/GOBERNANZA.md`: roles, permisos, control de cambios y auditoría.
- `docs/MODELO_OPERATIVO_BUK.md`: patrón de configuración de cada sesión en BUK.
- `docs/REGISTRO_PILOTO_SOER.md`: cómo documentar patrones BUK probados sin mezclar ambos proyectos.
- `templates/sesion.yaml`: plantilla canónica de una sesión.
- `templates/registro_cambio.yaml`: control de cambios.
- `templates/patron_buk_piloto.yaml`: registro de un patrón tecnológico/operativo probado.
- `schemas/traza_evento.schema.json`: esquema mínimo de eventos de trazabilidad.

## Fuentes de verdad

| Dominio | Fuente de verdad |
|---|---|
| Arquitectura, plantillas, versiones y decisiones | GitHub |
| Identidad, cargo, área y contexto de persona | HCM/BUK |
| Inscripciones, progreso operativo, evidencias y resultados | BUK |
| Materiales de apoyo | BUK o fuente institucional controlada, referenciada por versión |
| Analítica longitudinal | Exportaciones gobernadas / entorno analítico seguro |
| Evidencia histórica de cambios del diseño | GitHub |

## Regla de mantenibilidad

No crear un objeto instruccional mayor que su unidad razonable de actualización. Un cambio significativo no debe borrar el significado histórico de las trazas anteriores.
