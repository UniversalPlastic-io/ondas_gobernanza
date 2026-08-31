# 

# 

# **CASO DE USO** 

## **ONDAs \= Ocean Notarised Digital Asset space** 

## Espacio de datos innovador destinado a monitorizar y analizar la transferencia de residuos plásticos en la cadena trófica 

# 

# **E1.Plan de Comunicación a Participantes**

# 

**Entregable:** componente de «E1.Modelo de Gobernanza.pdf» (PT1), actividad **A1.2 — Gestión y Supervisión del marco de Gobernanza**
**Órgano responsable:** Autoridad de Gobernanza del Espacio de Datos (AGED)
**Versión:** v1.0 — aprobado por la AGED en el acta 1/2026, de 7 de abril de 2026

> **Alcance.** Este documento regula la comunicación **hacia los participantes adheridos** sobre el funcionamiento y las reglas del espacio de datos. No es el plan de comunicación externa ni de captación, que corresponde al entregable E3.1.

---

## 1. Objeto

La actividad A1.2 del plan de proyecto exige *"procedimientos para mantener informados a los participantes de cambios en normas y reglamentos"*. El Rulebook §14 establece la obligación pero no el mecanismo:

> *"Las modificaciones sustanciales deberán ser comunicadas previamente a los participantes."* — Rulebook §14

Este plan desarrolla ese mandato: define qué se comunica, por qué canal, con cuánta antelación y quién responde de hacerlo.

---

## 2. Principios

Derivados del Rulebook §3:

- **Transparencia** (§3.3) — las reglas, políticas y procedimientos deben ser **accesibles y comprensibles** para todos los participantes. La comunicación es el mecanismo que hace efectivo este principio.
- **Previsibilidad** — ningún cambio sustancial sorprende a un participante: existe preaviso y ventana de consulta.
- **Trazabilidad** — toda comunicación de gobernanza queda registrada, igual que las operaciones del ecosistema.
- **Proporcionalidad** — la antelación y la formalidad del canal se ajustan al impacto del cambio.

---

## 3. Qué se comunica

| Tipo | Ejemplos | Clasificación |
|------|----------|---------------|
| **Cambios normativos sustanciales** | Modificación del Rulebook, del Código Ético o del Contrato de Adhesión; cambios en las políticas de ciclo de vida del dato | Sustancial |
| **Cambios en el catálogo de políticas** | Alta, modificación o retirada de un modelo de política de acceso | Sustancial |
| **Cambios en requisitos técnicos** | Nuevos estándares de interoperabilidad, cambios en el modelo de metadatos, cambios en los mecanismos de autenticación | Sustancial o menor, según impacto |
| **Cambios operativos** | Ventanas de mantenimiento, actualizaciones de la plataforma, cambios de versión | Menor |
| **Incidencias de seguridad** | Brechas, vulnerabilidades explotadas, accesos no autorizados | Urgente |
| **Decisiones de gobernanza** | Resoluciones de la AGED, altas y bajas de participantes, medidas disciplinarias con efecto en el ecosistema | Según afectación |
| **Información periódica** | Estado del ecosistema, métricas operativas, nuevos assets publicados | Informativa |

---

## 4. Antelación mínima

| Clasificación | Antelación | Ventana de consulta |
|---------------|-----------|---------------------|
| **Sustancial** | 30 días naturales antes de la entrada en vigor | 15 días para alegaciones de los participantes |
| **Menor** | 7 días naturales | — |
| **Urgente** (seguridad) | Inmediata, sin preaviso | — |
| **Informativa** | Periodicidad establecida en §6 | — |

**Cambios sustanciales.** Requieren además que la AGED publique la versión anterior y la nueva, de forma que el participante pueda identificar qué ha cambiado. Si un cambio sustancial altera las obligaciones del Contrato de Adhesión, puede requerir **re-adhesión** o addenda firmada.

> **Plazos de preaviso: 30 días** para cambios sustanciales, **15** para menores y **7** para operativos. El participante que **rechace un cambio sustancial puede causar baja sin penalización** dentro del plazo de preaviso, porque un cambio sustancial altera las condiciones bajo las que se adhirió. Adoptado por la AGED en el **acuerdo 4** del «E1.Acta 1-2026 de la AGED.pdf», de 7 de abril de 2026.

---

## 5. Canales

| Canal | Uso | Carácter |
|-------|-----|----------|
| **Correo electrónico al contacto designado** | Comunicaciones sustanciales y urgentes | Oficial y fehaciente |
| **Repositorio documental del espacio** | Publicación de las versiones vigentes de Rulebook, Código Ético, políticas y procedimientos | Fuente de verdad |
| **Panel de la plataforma** | Avisos operativos, mantenimiento, estado del servicio | Operativo |
| **Sesión informativa con participantes** | Cambios sustanciales de alto impacto; presentación de la evolución del ecosistema | Complementario |

**Contacto designado.** Cada participante designa en el proceso de adhesión una persona de contacto para comunicaciones de gobernanza y se obliga a mantener ese dato actualizado. Las comunicaciones dirigidas a ese contacto se consideran válidamente efectuadas.

> **Repositorio documental oficial: la forja pública del proyecto**, en `https://github.com/UniversalPlastic-io/ondas_gobernanza`, donde el árbol del repositorio es el índice y las etiquetas de versión con su registro de cambios son la numeración exigida. **Canal de aviso: correo al contacto designado** en el proceso de adhesión. El sitio web del proyecto (E3.3), cuando exista, remitirá a la forja. La capacidad de la plataforma D-Spacer para emitir avisos a todos los participantes **no se da por supuesta**: el canal oficial es el correo. Adoptado por la AGED en el **acuerdo 5** del «E1.Acta 1-2026 de la AGED.pdf», de 7 de abril de 2026.

---

## 6. Comunicación periódica

| Comunicación | Periodicidad | Contenido |
|--------------|-------------|-----------|
| **Boletín del ecosistema** | Trimestral | Nuevos participantes, nuevos assets publicados, cambios normativos del período, métricas de uso |
| **Informe anual de gobernanza** | Anual | Auditorías realizadas, incidencias gestionadas, evolución del catálogo, revisión del Rulebook, roadmap |

---

## 7. Responsabilidades

| Actor | Responsabilidad |
|-------|-----------------|
| **AGED** | Aprobar el contenido de toda comunicación normativa. Decidir la clasificación de cada cambio. Convocar sesiones informativas. |
| **Operador funcional (Universal Plastic)** | Ejecutar la comunicación: envío, publicación en el repositorio, mantenimiento del censo de contactos. |
| **Operador tecnológico (SQS)** | Comunicar ventanas de mantenimiento, cambios de versión de la plataforma e incidencias técnicas al operador funcional para su difusión. |
| **Participante** | Mantener actualizado su contacto designado. Acusar recibo de comunicaciones sustanciales. Comunicar a la AGED cualquier incumplimiento del que tenga conocimiento en **5 días hábiles** (Contrato de Adhesión). |

> **Responsable de la ejecución: el rol «Responsable de Gobernanza del Espacio de Datos»**, ocupado por **Adrià González Copado** (Universal Plastic). El nombre de la persona se comunica a los participantes y puede actualizarse sin modificar este plan. Adoptado por la AGED en el **acuerdo 6** del «E1.Acta 1-2026 de la AGED.pdf», de 7 de abril de 2026.

---

## 8. Comunicación en incidencias y conflictos

El Protocolo de Gestión de Incidencias y Conflictos regula el tratamiento de la incidencia; este plan regula su comunicación:

- **Incidencia de seguridad con impacto en datos de participantes:** comunicación inmediata a los afectados, sin esperar a la resolución. Si hay datos personales comprometidos, se activan además los plazos de notificación del RGPD.
- **Incidencia operativa:** aviso en el panel de la plataforma y, si la indisponibilidad supera el umbral acordado, comunicación por correo.
- **Conflicto entre participantes:** la comunicación se limita a las partes implicadas y a la AGED, salvo que la resolución siente precedente aplicable al ecosistema.
- **Medidas disciplinarias:** se notifican al participante afectado de forma motivada. La comunicación al resto del ecosistema se produce solo cuando la medida afecta a la disponibilidad de assets publicados por ese participante.

---

## 9. Registro y trazabilidad

Toda comunicación de gobernanza queda registrada con: fecha de emisión, tipo y clasificación, destinatarios, canal, contenido o enlace a la versión publicada, y acuses de recibo cuando se requieran.

Este registro forma parte de las evidencias de gobernanza disponibles para auditorías internas y externas, y permite acreditar el cumplimiento de la obligación de preaviso del Rulebook §14.

---

## 10. Revisión

Este plan se revisa anualmente por la AGED, o antes si un cambio regulatorio o una incidencia relevante lo justifica. Las modificaciones siguen el mismo procedimiento de comunicación que regulan.

---

## Anexo — Trazabilidad

| Elemento del plan | Fundamento documental |
|-------------------|--------------------------------------|
| Obligación de preaviso | Rulebook §14 |
| Principio de transparencia | Rulebook §3.3 |
| Funciones de la AGED | Documento de Constitución de la AGED §5.2, §5.5 |
| Reparto operador funcional / tecnológico | Organigrama y Roles §5, §6 |
| Comunicación de incidencias | Protocolo de Gestión de Incidencias y Conflictos §5, §8, §9 |
| Deber de comunicar incumplimientos en 5 días hábiles | Contrato de Adhesión, obligaciones del Participante |
| Registro y evidencias | Documento de Cumplimiento y Auditoría §4, §12 |
