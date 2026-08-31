# 

# 

# **CASO DE USO** 

## **ONDAs \= Ocean Notarised Digital Asset space** 

## Espacio de datos innovador destinado a monitorizar y analizar la transferencia de residuos plásticos en la cadena trófica 

# 

# **E1.Políticas de gestión del ciclo de vida del dato**

# 

> **Alcance tecnológico** *(revisado el 20/04/2026 con la especificación OpenAPI de D-Spacer)*. La plataforma es un **conector EDC** con **Dataspace Protocol** y **ODRL completo**; lo que difiere del diseño aprobado es la **identidad**, que es Keycloak y BPN en lugar de DID, credenciales verificables y DAPS. El panel asigna tres modalidades de política —grupo, lista de BPN y fecha—, pero el API admite políticas ODRL arbitrarias. **Lo que no consta es qué motor aplica las obligaciones y prohibiciones**, y por eso las condiciones de uso posterior siguen respaldándose por contrato. Ver «E1.Plantillas de política ODRL.pdf».


**Entregable:** componente de «E1.Modelo de Gobernanza.pdf» (PT1)
**Órgano responsable:** Autoridad de Gobernanza del Espacio de Datos (AGED)
**Versión:** v1.0 — aprobadas por la AGED en el acta 1/2026, de 7 de abril de 2026
**Documentos de referencia:** Rulebook del ONDAs Dataspace · Contrato de Adhesión · Política de Seguridad y Privacidad · Documento de Cumplimiento y Auditoría · Procedimiento de Adhesión, Permanencia y Baja · Documentación del Catálogo y Metadatos

---

## 1. Objeto y alcance

Este documento define las políticas que rigen el **dato** desde su generación hasta su eliminación o archivo dentro del ONDAs Dataspace. Complementa al Rulebook, que fija el marco normativo del ecosistema, y al Procedimiento de Adhesión, que regula el ciclo de vida de los **participantes** —no del dato.

Aplica a todos los datasets y activos digitales publicados en el catálogo del espacio, y a los registros de operación generados por su uso.

**Principio rector.** Conforme al Rulebook §3.1, cada participante mantiene la titularidad y el control sobre los datasets que publica. Estas políticas no transfieren titularidad: establecen las obligaciones mínimas comunes que todo participante asume al adherirse.

---

## 2. Fases del ciclo de vida

| Fase | Responsable principal | Supervisión |
|------|----------------------|-------------|
| 1. Origen y recolección | Participante proveedor | AGED |
| 2. Validación y control de calidad | Espacio de datos (proceso automático) | AGED |
| 3. Almacenamiento | Participante proveedor · Operador tecnológico | AGED |
| 4. Publicación en catálogo | Participante proveedor | AGED |
| 5. Uso e intercambio | Participante consumidor | AGED · estadísticas y exportación de actividad de la plataforma |
| 6. Retención | Ambos, según el contrato y la política de acceso aplicable | AGED |
| 7. Eliminación y archivo | Titular del dato · Operador tecnológico | AGED |

---

## 3. Fase 1 — Origen y recolección

**Política.** Todo dataset incorporado al espacio debe tener un origen declarado, verificable y lícito.

Obligaciones del participante proveedor, conforme al Contrato de Adhesión §6.3:

- **Declarar el origen y el método de obtención** mediante atributos de procedencia en los metadatos DCAT: `prov:wasGeneratedBy` y `prov:wasDerivedFrom`.
- **Declarar el grado de fiabilidad** de los datos.
- Para **datos de laboratorio, sensores o boyas**, aportar información verídica sobre el **proceso de calibración** y la soberanía del dato.
- **Contar con las autorizaciones** de los titulares de los datos para ponerlos a disposición de terceros dentro del espacio.
- **No introducir datos distorsionados ni deliberadamente incompletos** (Contrato §6.2).

**Datos personales.** Si el dataset contiene o puede contener datos personales, el participante es responsable de garantizar la base jurídica del tratamiento conforme al RGPD antes de la publicación (Política de Seguridad y Privacidad §9).

---

## 4. Fase 2 — Validación y control de calidad

**Política.** Ningún dataset se incorpora al catálogo sin superar la validación de interoperabilidad y calidad del espacio.

Conforme al Contrato de Adhesión §6.3, el espacio ejecuta un proceso de validación destinado a verificar que los datasets:

- están **completos**;
- están **libres de valores atípicos u otros errores**;
- cumplen los **criterios de interoperabilidad** definidos en el Rulebook.

**Los datos que no superen esta revisión no serán incorporados al catálogo.** La decisión de rechazo es notificada al participante proveedor, que puede corregir y reenviar.

Validaciones aplicadas:

| Validación | Qué comprueba |
|------------|---------------|
| Metadatos DCAT | Presencia y corrección de los campos obligatorios del modelo común |
| Formato y estructura | Conformidad con el esquema de referencia del tipo de dataset |
| Calidad por parámetro | Rangos, unidades y coherencia de los valores |
| Limpieza de datos | Valores atípicos, duplicados, campos vacíos |
| Política de acceso | Existencia de una política de acceso válida asociada al asset mediante contrato |

---

## 5. Fase 3 — Almacenamiento

**Política.** El dato permanece bajo control de su titular; la infraestructura del espacio garantiza confidencialidad e integridad.

- **Soberanía.** Cada participante mantiene sus datos en su propio entorno tecnológico y define las condiciones bajo las cuales pueden compartirse (Arquitectura Técnica §2). El espacio no centraliza los datasets: publica metadatos y media el acceso.
- **Cifrado en reposo** de los datos y activos gestionados por la infraestructura del espacio (Política de Seguridad y Privacidad §7.2).
- **Cifrado en tránsito** en toda transferencia (Política de Seguridad y Privacidad §7.1).
- **Control de acceso** verificado antes de servir cualquier dato: autenticación en Keycloak (realm `connector-realm`), identificación del participante por **BPN** y evaluación de la política del contrato — pertenencia al grupo, y en su caso lista de BPN o fecha límite («E1.Plantillas de política ODRL.pdf»).

---

## 6. Fase 4 — Publicación en catálogo

**Política.** La publicación expone metadatos, nunca datos en bruto sin política asociada.

Requisitos de publicación:

- **Metadatos obligatorios** conforme al modelo común DCAT: `dct:identifier`, `dct:title`, `dct:description`, `dct:publisher`, `dct:spatial`, `dct:temporal`, `dcat:distribution`, `dct:license`, `dct:theme` y `prov:wasGeneratedBy`.
- **Política de acceso asignada** al asset mediante un contrato, conforme a uno de los tres modelos que la plataforma implementa («E1.Plantillas de política ODRL.pdf») o a un modelo aprobado por la AGED.
- **Veracidad y actualización** de los metadatos publicados, obligación expresa del Contrato de Adhesión.
- **Asset semilla.** Todo participante debe publicar al menos un asset coherente con el ámbito del espacio —residuos, medio ambiente, zona costera y marina, microplásticos o servicios municipales— como condición para formalizar su adhesión (Contrato §6.1).

**Versionado.** Cuando un proveedor actualiza un dataset ya publicado se registra una nueva versión, conservando el histórico y la fecha de actualización, de forma que los consumidores puedan reproducir análisis anteriores y detectar cambios en las series temporales.

---

## 7. Fase 5 — Uso e intercambio

**Política.** Todo acceso se formaliza mediante contrato digital y queda registrado.

- **Contrato obligatorio.** Todo acceso o compartición entre participantes se formaliza mediante un **contrato que vincula el activo con una política de acceso** (Contrato §6.4). **Lo crea el participante proveedor** —esquema `minimalContractDefinition`: contrato, política y activo—. El consumidor inicia una negociación de contrato sobre **Dataspace Protocol** (`@type: ContractRequest`) en la que **acepta la oferta publicada**, sin proponer términos propios. Un mismo activo admite varios contratos con políticas distintas.
- **Limitación de finalidad.** El participante se obliga a utilizar los servicios del espacio *"exclusivamente para los fines declarados en la negociación de cada contrato de datos y conforme a las políticas ODRL aplicables"* (Contrato de Adhesión, obligaciones del Participante). La cita es literal del Contrato aprobado; la finalidad se declara hoy mediante el **grupo (caso de uso)** al que se asocia la política, y su cumplimiento es **exigible contractualmente**, no impuesto por la plataforma.
- **Registro de la operación.** La plataforma aporta **estadísticas de actividad por periodo y exportación a CSV** desde el conector, y un endpoint de **telemetría por fecha** (`POST /telemetry/request`). Queda por confirmar si equivale al *Transaction Log Register* descrito en el Documento de Cumplimiento y Auditoría §4.
- **Prohibiciones de uso** —redistribución, sublicencia— y **obligaciones** —atribución, reporte de uso— **son expresables** como `odrl:prohibition` y `odrl:obligation` en la política, pero **no consta que el conector las aplique**. Mientras no se confirme, se exigen por el Rulebook y el Contrato de Adhesión, bajo supervisión de la AGED (ver «E1.Plantillas de política ODRL.pdf»).

---

## 8. Fase 6 — Retención

**Política.** Se distingue entre la retención del **dataset** y la de los **registros de operación**.

| Elemento | Plazo | Fundamento |
|----------|-------|------------|
| **Registros de auditoría y trazabilidad** | **5 años** | Obligaciones legales y de auditoría del ecosistema |
| **Dataset en poder del consumidor** | El fijado en el contrato de datos | Obligación contractual; la plataforma solo puede fijar una **fecha límite de acceso**, no forzar el borrado |
| **Dataset en poder del proveedor** | Decisión del titular, conforme a su propia normativa | Soberanía del dato (Rulebook §3.1) |
| **Metadatos del catálogo** | Mientras el asset esté publicado, más el período de trazabilidad | Continuidad del catálogo |

> **Plazo general de retención: 5 años**, alineado con el de los registros de auditoría y **sin excepciones por tipo de dataset** —recogidas de playa, boyas de biomasa, microplásticos en agua y en peces, variables oceanográficas—. Una sola regla, coherente con lo ya aprobado y verificable. Adoptado por la AGED en el **acuerdo 2** del «E1.Acta 1-2026 de la AGED.pdf», de 7 de abril de 2026.

---

## 9. Fase 7 — Eliminación y archivo

**Política.** La eliminación de un dataset no elimina la trazabilidad de las operaciones ya realizadas sobre él.

- **Retirada del catálogo.** El proveedor puede retirar un asset publicado. La retirada impide nuevas negociaciones, pero no afecta a los contratos ya ejecutados.
- **Eliminación por el consumidor.** Al vencer el plazo de retención acordado, el consumidor debe eliminar el dataset. La obligación es **expresable** como `odrl:obligation`, pero mientras no se confirme que el conector la aplica se sostiene como **obligación contractual**; lo que la plataforma sí garantiza por sí sola es la **caducidad del acceso** mediante la restricción por fecha.
- **Baja del participante.** Conforme al Procedimiento de Adhesión §9, la baja implica desactivación de acceso, finalización de la participación activa y cierre operativo, pero **no elimina**: registros históricos, contratos previamente ejecutados ni evidencias de trazabilidad necesarias para auditoría o cumplimiento normativo.
- **Datos personales.** El ejercicio de derechos RGPD sobre datos personales contenidos en un dataset se dirige al participante responsable del tratamiento, no al espacio de datos. El espacio colabora facilitando la trazabilidad de las transferencias realizadas.

> **SLA de borrado: 30 días naturales** desde la solicitud, alineado con el plazo que el RGPD concede para atender el ejercicio de derechos. **La purga de los registros de auditoría al vencer los 5 años la autoriza la AGED**, mediante acuerdo expreso y previo informe del operador funcional. Adoptado por la AGED en el **acuerdo 3** del «E1.Acta 1-2026 de la AGED.pdf», de 7 de abril de 2026.

---

## 10. Protección de datos personales a lo largo del ciclo

Medidas aplicables en cualquier fase, conforme a la Política de Seguridad y Privacidad §9 y §10 y al Documento de Cumplimiento y Auditoría §10:

- **Minimización de datos** — publicar únicamente los campos necesarios para la finalidad declarada.
- **Limitación del tratamiento** — al fin declarado en la negociación del contrato.
- **Control de acceso** por rol y política.
- **Trazabilidad** de todo acceso.
- **Anonimización, pseudonimización, agregación o reducción de granularidad** cuando el dataset contenga información sensible o datos personales.
- **Prohibición de reidentificación** de personas u organizaciones a partir de datos anonimizados o agregados.

Los participantes deberán garantizar que los datasets publicados cumplen la normativa aplicable en materia de protección de datos.

---

## 11. Supervisión del cumplimiento

La AGED supervisa la aplicación de estas políticas mediante:

- **Logging y observabilidad** continuos del ecosistema.
- **Auditorías internas y externas** sobre las operaciones registradas.
- **Investigación de incidencias** conforme al Protocolo de Gestión de Incidencias y Conflictos.
- **Medidas correctivas y disciplinarias** —advertencia, suspensión temporal o revocación de acceso— ante incumplimientos acreditados.

Los participantes están obligados a comunicar a la AGED cualquier incumplimiento del Rulebook del que tengan conocimiento **en un plazo máximo de 5 días hábiles** desde su detección (Contrato de Adhesión, obligaciones del Participante).

---

## 12. Revisión

Estas políticas se revisan cuando lo requiera un cambio regulatorio, la incorporación de nuevos estándares técnicos o una mejora de los mecanismos de gobernanza. La AGED aprueba las modificaciones y las comunica previamente a los participantes conforme al «E1.Plan de Comunicación a Participantes.pdf».

---

## Anexo — Trazabilidad documental

| Fase | Documento que la fundamenta |
|------|--------------------------------------|
| Origen y recolección | Contrato de Adhesión §6.2, §6.3 · Detalles de los Assets Publicados §3 |
| Validación y calidad | Contrato de Adhesión §6.3 |
| Almacenamiento | Política de Seguridad y Privacidad §7 · Arquitectura Técnica §2 |
| Publicación | Documentación del Catálogo y Metadatos · Contrato de Adhesión §6.1, §6.5 |
| Uso e intercambio | Rulebook §6, §10 · Documento de Transferencia y Trazabilidad §7, §8 · Contrato §6.4 |
| Retención | Documento de Cumplimiento y Auditoría §4, §5 |
| Eliminación y archivo | Procedimiento de Adhesión §9, §10 |
| Protección de datos | Política de Seguridad y Privacidad §9, §10 · Cumplimiento y Auditoría §10 |
