# Modelo lógico de datos y trazabilidad

## 1. Objetos principales

### Program
Representa el diplomado como unidad longitudinal.

Campos mínimos: `program_id`, `name`, `version`, `status`, `owner`.

### Module
Agrupador curricular lógico.

Campos: `module_id`, `program_id`, `name`, `order`.

### Session
Unidad operativa/versionable. Corresponde normalmente a un curso E-learning asociado a un encuentro.

Campos: `session_id`, `module_id`, `title`, `version`, `status`, `buk_course_id`, `scheduled_at`, `trainer_role`, `problem`, `capacity`, `expected_action`, `execution_mode`, `risk_level`.

### ResourceVersion
Recurso utilizado por una sesión/actividad.

Campos: `resource_id`, `session_id`, `title`, `uri_or_buk_ref`, `stability_class`, `version`, `valid_from`, `valid_to`.

`stability_class`: `stable | moderate | volatile`.

### Activity
Unidad verificable dentro de una sesión.

Campos: `activity_id`, `session_id`, `purpose`, `instructions`, `action_type`, `required`, `sequence`.

### EvidenceDefinition
Define qué evidencia se espera y por qué.

Campos: `evidence_definition_id`, `activity_id`, `evidence_type`, `minimum_requirements`, `criterion_required`, `retention_class`.

### ParticipantEnrollment
Relación persona-programa.

Campos operativos en BUK/entorno analítico seguro: `participant_id`, `program_id`, `enrollment_date`, `status`.

### ParticipantSession
Relación persona-sesión. Debe conservar dimensiones separadas:

- `enrollment_status`;
- `attendance_status`;
- `execution_status`;
- `evidence_status`;
- `criterion_status`;
- `course_status`;
- `closure_status`.

### EvidenceSubmission
Instancia de evidencia enviada por un participante.

Campos: `submission_id`, `participant_id`, `evidence_definition_id`, `session_version`, `submitted_at`, `evidence_ref`, `evaluator_id`, `criterion_status`, `feedback_at`.

### TraceEvent
Evento longitudinal que permite reconstruir el proceso.

Campos: `event_id`, `participant_id`, `program_id`, `session_id`, `activity_id`, `event_type`, `event_at`, `actor_role`, `source_system`, `version_context`, `payload_ref`.

## 2. Relaciones

```text
Program 1 ─── N Module
Module 1 ─── N Session
Session 1 ─── N Activity
Session 1 ─── N ResourceVersion
Activity 1 ─── N EvidenceDefinition
Participant N ─── N Program   (ParticipantEnrollment)
Participant N ─── N Session   (ParticipantSession)
ParticipantSession 1 ─── N EvidenceSubmission
Participant/Session/Activity 1 ─── N TraceEvent
```

## 3. Estados recomendados

### Ciclo de vida de la sesión

`draft → technical_review → pedagogically_validated → configured → published → executed → closed → retired`

No confundir este estado con el estado del participante.

### Dimensiones del participante

**Ejecución:** `not_started | started | executed | not_executed`

**Evidencia:** `not_required | pending | submitted | rejected_for_format | accepted`

**Criterio:** `not_applicable | not_assessed | met | not_met | pending_review`

**Curso BUK:** usar el valor real disponible en BUK sin reinterpretarlo (`approved`, `failed`, etc.).

**Cierre:** `open | follow_up_required | closed`.

## 4. Eventos mínimos deseables

- `enrolled`
- `session_opened`
- `attendance_recorded`
- `activity_executed`
- `evidence_submitted`
- `evidence_reviewed`
- `feedback_issued`
- `criterion_met`
- `criterion_not_met`
- `course_approved`
- `course_failed`
- `due_date_missed`
- `exception_opened`
- `exception_closed`
- `session_closed`

No todos tienen que existir como eventos nativos en BUK. Algunos pueden derivarse de exportaciones; el modelo lógico evita depender de una implementación específica.

## 5. Identificadores lógicos

Los IDs de diseño no deben depender de IDs internos de BUK.

Ejemplo:

`DLGUFE-M03-S02-A01-E01`

- `DLGUFE`: programa.
- `M03`: módulo.
- `S02`: sesión.
- `A01`: actividad.
- `E01`: evidencia.

BUK conserva sus identificadores internos en campos de mapeo (`buk_course_id`, etc.).

## 6. Regla de histórico

Nunca editar una sesión de forma que el resultado histórico de participantes anteriores cambie de significado. Si cambia capacidad, evidencia, criterio o lógica de aprobación, crear una nueva versión mayor o una nueva sesión lógica según el impacto.
