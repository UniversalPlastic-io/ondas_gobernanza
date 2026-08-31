# Registro de versiones del corpus normativo

Versiones del cuerpo normativo del ONDAs Dataspace publicado en este
repositorio. Cada versión se corresponde con una etiqueta de git.

El historial de git es el registro detallado: toda modificación de una norma
vigente queda con su fecha, su autor y su motivo. Este fichero recoge qué
cambió en cada versión del conjunto y en virtud de qué acuerdo de la AGED.

Formato basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/).

---

## [v1.0] — 2026-09-01

Primera publicación del cuerpo normativo en el repositorio documental oficial,
en cumplimiento del **acuerdo 5** del acta 1/2026 de la AGED, de 5 de junio de
2026, que designa la forja pública como repositorio oficial y exige índice y
numeración de versión.

Los documentos se publican tal como fueron aprobados. La única salvedad está
recogida abajo, en «Divergencias respecto a lo entregado».

### Normas publicadas

- Rulebook del ONDAs Dataspace
- Contrato de Adhesión
- Procedimiento de Adhesión, Permanencia y Baja
- Políticas de gestión del ciclo de vida del dato — v1.0
- Plan de Comunicación a Participantes — v1.0
- Protocolo de Gestión de Incidencias y Conflictos
- Plantillas de política ODRL
- Organigrama y Roles del Ecosistema ONDAs
- Modelo de Gobernanza

### Decisiones de la AGED incorporadas al texto de las normas

| Acuerdo | Norma afectada | Qué fija |
|---------|----------------|----------|
| 2 | Políticas del ciclo de vida del dato §8 | Retención general de 5 años, sin excepciones por tipo de dataset |
| 3 | Políticas del ciclo de vida del dato §9 | SLA de borrado de 30 días naturales; la purga de los registros de auditoría la autoriza la AGED |
| 4 | Plan de Comunicación §4 | Plazos mínimos de preaviso y efecto del rechazo de un cambio sustancial |
| 5 | Plan de Comunicación §5 | Repositorio documental oficial y canal de aviso |
| 6 | Plan de Comunicación §7 | Rol responsable de la ejecución del plan |

### Divergencias respecto a lo entregado

- **Modelo de Gobernanza.** La copia publicada omite el desglose presupuestario
  por actividad y la entidad ejecutora de cada una, así como el importe total del
  entregable. Son metadatos de gestión del proyecto, no contenido normativo, y su
  difusión corresponde a cada entidad ejecutora. La omisión está señalada en el
  propio documento, en la tabla de identificación y en «Actividades que lo
  producen». Ningún otro texto se ha modificado.

### Aprobada y no publicada

- **Código Ético y de Conducta** — v1.0. Aprobado en el acta 1/2026 con la
  publicación condicionada a la revisión jurídica encomendada en el acuerdo 9.
  Se incorporará al concluir esa revisión.

### Pendiente

- **Siete de las nueve normas no declaran versión interna.** La numeración del
  corpus las cubre mediante la etiqueta de git, pero conviene que cada documento
  lleve la suya.
- **Las dos que sí la declaran dicen «v1.0 — borrador para aprobación de la
  AGED»**, redacción anterior a la sesión que las aprobó. El estado real es el
  que consta en el índice y en el acta 1/2026; los textos no se han tocado al
  publicarlos, así que la corrección de esa línea queda pendiente.
