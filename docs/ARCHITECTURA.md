# Arquitectura integral de gobierno del Diplomado en BUK

## 1. Objetivo

Construir una arquitectura simple, modular y trazable que permita gobernar el diplomado en el tiempo, incorporar materiales producidos por diferentes formadores, capturar múltiples tipos de evidencia y conservar la interpretación histórica de cada experiencia.

La arquitectura debe soportar cuatro usuarios principales:

- **Formación y Desarrollo / administrador:** gobierna estructura, versiones, publicación y seguimiento.
- **Formador:** aporta conocimiento técnico, recursos, criterios y retroalimentación sin redefinir la arquitectura global.
- **Participante:** recorre una trayectoria clara, realiza acciones y deja trazas individuales aun en actividades grupales.
- **Evaluador/auditor externo:** accede a evidencia y resultados bajo permisos controlados, sin necesidad de editar el diseño.

## 2. Vista macro → micro

### Nivel 0 — Programa

**Objeto:** Diplomado.

**Entradas:** propósito institucional, perfil de egreso, capacidades rectoras, cronograma, reglas globales, población.

**Procesos:** gobierno curricular, definición de trayectoria, criterios globales, control de versiones.

**Salidas:** trayectoria publicada, catálogo de sesiones, reglas de seguimiento, indicadores globales.

### Nivel 1 — Trayectoria

**Objeto lógico:** ruta longitudinal.

**Entradas:** sesiones aprobadas, secuencia, dependencias, fechas/ventanas.

**Procesos:** ordenamiento, prerrequisitos solo donde agreguen valor, inscripción/activación, seguimiento global.

**Salidas:** secuencia comprensible, estado global por participante, lista de excepciones.

### Nivel 2 — Sesión

**Objeto operativo principal:** curso E-learning independiente asociado a un encuentro.

**Entradas:** problema, capacidad, acción, modalidad, evidencia, criterios, materiales del formador, fecha y responsables.

**Procesos:** validación pedagógica, configuración BUK, ejecución presencial/virtual, captura de evidencia, retroalimentación, cierre.

**Salidas:** trazas individuales, evidencia, criterio, estado del curso, observaciones, continuidad.

### Nivel 3 — Actividad

**Objeto:** unidad verificable de aprendizaje.

**Entradas:** propósito, recurso, instrucciones, contexto de ejecución.

**Proceso:** acción del participante.

**Salidas:** producto, respuesta, archivo, decisión, observación, participación u otra evidencia válida.

### Nivel 4 — Evidencia y criterio

**Objeto:** evidencia de ejecución + interpretación del logro.

**Entradas:** producto o traza producida.

**Procesos:** recepción, validación técnica, feedback, juicio contra criterio cuando corresponda.

**Salidas:** evidencia entregada, criterio alcanzado/no alcanzado/no evaluado, feedback, necesidad de refuerzo.

### Nivel 5 — Evento de trazabilidad

**Objeto lógico:** evento con fecha/hora que permite reconstruir qué ocurrió.

Ejemplos: inscripción, inicio, asistencia, entrega, feedback, criterio alcanzado, aprobación, reprobación, vencimiento, excepción abierta/cerrada.

## 3. Flujo end-to-end

**Necesidad institucional**
→ matriz curricular rectora
→ diseño de la sesión
→ recepción de materiales del formador
→ clasificación de estabilidad del contenido
→ validación pedagógica/riesgo
→ configuración/versionado
→ publicación en BUK
→ inscripción/activación
→ ejecución del encuentro
→ captura individual de evidencia
→ valoración/feedback
→ gestión por excepción
→ continuidad
→ cierre de sesión
→ exportación/analítica
→ aprendizaje del piloto
→ ajuste de la versión siguiente.

## 4. Entradas controladas por sesión

Toda sesión debe ingresar al sistema con estos mínimos:

1. `session_id` lógico estable.
2. Título.
3. Módulo/trayectoria.
4. Problema que aborda.
5. Capacidad que desarrolla.
6. Acción esperada.
7. Modalidad de ejecución.
8. Evidencia mínima.
9. Criterio de logro si aplica.
10. Formador/responsable técnico.
11. Fecha/ventana.
12. Recursos y su clasificación de estabilidad.
13. Riesgo y autorizaciones si aplica.
14. Regla de continuidad.

Si falta uno de los mínimos críticos, la sesión permanece en **borrador** y no se publica.

## 5. Salidas estándar por sesión

No todas las sesiones producirán todos los campos, pero la arquitectura debe poder representar:

- participación/asistencia;
- actividad ejecutada;
- evidencia entregada;
- criterio alcanzado/no alcanzado/no evaluado;
- curso aprobado/reprobado cuando aplique;
- feedback;
- excepción;
- continuidad/refuerzo;
- versión de contenido y de sesión utilizada;
- fecha/hora de los eventos relevantes.

## 6. Principio de separación de estados

Nunca colapsar en un único estado “completado”. Mantener conceptualmente separados:

- **actividad realizada**;
- **evidencia entregada**;
- **criterio alcanzado**;
- **curso aprobado**;
- **experiencia cerrada**.

Un participante puede estar en combinaciones distintas y cada combinación debe ser interpretable.

## 7. Frontera GitHub ↔ BUK

### GitHub conserva

- arquitectura;
- plantillas;
- IDs lógicos;
- especificaciones de sesión;
- criterios y reglas;
- control de cambios;
- decisiones de diseño;
- registro anónimo del piloto tecnológico.

### BUK conserva

- personas e identidad;
- contexto laboral;
- inscripciones;
- interacción operativa;
- evidencias;
- resultados;
- asistencia/progreso disponible;
- datos necesarios para seguimiento del participante.

### GitHub NO debe almacenar

- nombres de participantes;
- documentos de identidad;
- evidencia individual;
- información clínica;
- archivos asistenciales;
- datos sensibles o exportaciones sin anonimizar.
