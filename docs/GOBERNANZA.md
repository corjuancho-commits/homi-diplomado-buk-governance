# Gobierno, roles, permisos y control de cambios

## 1. Roles

### Propietario funcional — Formación y Desarrollo

Responsable de:

- arquitectura global;
- IDs y nomenclatura;
- validación pedagógica;
- configuración/publicación en BUK;
- control de cambios;
- definición de evidencias mínimas;
- seguimiento y gestión por excepción;
- cierre y archivo.

### Formador / experto técnico

Responsable de:

- conocimiento mínimo indispensable;
- materiales de apoyo;
- estándares técnicos;
- instrucciones específicas;
- errores críticos;
- feedback técnico durante la experiencia.

No modifica unilateralmente la estructura global, criterios de trazabilidad o estados.

### Participante

Responsable de:

- recorrer la secuencia aplicable;
- realizar la acción;
- dejar la evidencia individual requerida;
- atender feedback/refuerzo cuando corresponda.

### Evaluador/auditor externo

Acceso preferente de **solo lectura** a información curada para el propósito de evaluación. No requiere acceso de autoría.

Debe respetarse minimización de datos: mostrar solo la evidencia necesaria para la evaluación y el periodo correspondiente.

### Administrador de plataforma

Gestiona permisos, configuración técnica y soporte, sin sustituir la gobernanza curricular.

## 2. RACI resumido

| Actividad | Formación | Formador | Participante | Evaluador externo | Admin BUK |
|---|---|---|---|---|---|
| Definir arquitectura | A/R | C | I | C | C |
| Definir contenido técnico | A | R | I | C | I |
| Validar sesión | A/R | C | I | I | C |
| Configurar en BUK | A | C | I | I | R/C |
| Ejecutar formación | A/C | R | R | I | I |
| Entregar evidencia | I | C | R | I | I |
| Evaluar criterio | A | R/C | I | R/C cuando aplique | I |
| Gestionar excepción | A/R | C | C | I | C |
| Auditar | C | C | I | A/R | I |
| Versionar diseño | A/R | C | I | C | C |

A = accountable; R = responsible; C = consulted; I = informed.

## 3. Control de cambios

### Cambio PATCH `x.y.Z`

Corrección editorial, enlace, referencia o recurso sin modificar capacidad, acción, evidencia o criterio.

### Cambio MINOR `x.Y.z`

Cambio de instrucciones, recurso, modalidad o mejora didáctica que conserva el mismo resultado esperado y criterio esencial.

### Cambio MAJOR `X.y.z`

Cambia capacidad, acción principal, evidencia, criterio, lógica de aprobación o estructura que altera la interpretación histórica.

Un cambio MAJOR normalmente requiere nueva versión claramente separada en BUK; no debe sobrescribir silenciosamente experiencias anteriores.

## 4. Checklist de publicación

Antes de publicar una sesión:

- [ ] problema definido;
- [ ] capacidad definida;
- [ ] acción observable;
- [ ] modalidad acorde al riesgo;
- [ ] evidencia mínima pertinente;
- [ ] criterio explícito si aplica;
- [ ] materiales versionados/clasificados;
- [ ] permisos/autorizaciones revisados;
- [ ] ventana/fecha definida;
- [ ] continuidad definida;
- [ ] captura individual posible;
- [ ] trazabilidad BUK verificada;
- [ ] dueño de excepción definido.

## 5. Seguridad y datos

- GitHub no contiene PII ni evidencia de participantes.
- Datos clínicos no deben convertirse en material de práctica sin desidentificación y autorización.
- La evidencia debe ser proporcional al propósito pedagógico.
- Auditoría externa usa acceso mínimo necesario.
- Exportaciones para analítica deben gobernarse y, cuando sea posible, seudonimizarse.
