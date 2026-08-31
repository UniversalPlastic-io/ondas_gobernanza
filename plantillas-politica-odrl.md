# 

# 

# **CASO DE USO** 

## **ONDAs \= Ocean Notarised Digital Asset space** 

## Espacio de datos innovador destinado a monitorizar y analizar la transferencia de residuos plásticos en la cadena trófica 

# 

# **E1.Plantillas de política ODRL**

**Versión:** v1.0 — aprobadas por la AGED en el acta 1/2026, de 5 de junio de 2026

## 

## 

## 

## 

## 

## 

## 

# **Plantillas de política ODRL**

> **Alcance revisado — 31 de agosto de 2026.** Este documento conserva las **tres plantillas ODRL** comprometidas en el Rulebook §6 y en el Contrato de Adhesión §6.4, que siguen siendo válidas: la especificación OpenAPI del middleware de D-Spacer acredita que la plataforma es un **conector EDC** que admite políticas **ODRL completas** por API.
>
> Lo que se ha corregido es el apartado **7, Enforcement técnico**: la identidad no se basa en credenciales verificables sino en **Keycloak y BPN**, y no consta que el conector aplique las obligaciones y prohibiciones. Detalle en «E2.SQS.Documento de API.pdf» §1.5 y en «E2.SQS.Modelo real de D-Spacer.pdf» §5.

## **1\. Objeto**

Este documento recoge los **modelos de política de uso del dato** del ONDAs Dataspace. Son las tres políticas que el **Rulebook §6** declara como estándar del ecosistema:

> *"La compartición de datos dentro del ONDAs Dataspace se realiza mediante políticas digitales expresadas en ODRL (Open Digital Rights Language). El ecosistema contempla inicialmente las siguientes políticas estándar: **OPEN** — acceso libre con obligación de atribución; **RESEARCH-ONLY** — acceso restringido a entidades científicas acreditadas; **COMMERCIAL-WITH-OBLIGATIONS** — acceso sujeto a condiciones comerciales específicas. Cada Data Provider define las políticas aplicables a sus datasets y mantiene control sobre las condiciones de acceso y reutilización."* — Rulebook §6

Y son las que el **Contrato de Adhesión §6.4** compromete a poner a disposición de los participantes:

> *"El Promotor del Espacio pondrá a disposición plantillas de política estandarizadas: OPEN, RESEARCH-ONLY y COMMERCIAL-WITH-OBLIGATIONS."* — Contrato de Adhesión §6.4

Todo acceso o compartición de datos entre participantes debe formalizarse mediante un **contrato digital negociado a través del conector EDC**, que incorpora la política ODRL aplicable al asset.

## **2\. Catálogo de políticas**

| Política | URN | Quién accede | Prohibiciones | Obligaciones |
| :---- | :---- | :---- | :---- | :---- |
| OPEN | `urn:ondas:policy:open` | Cualquier participante adherido con credencial válida | — | Atribución · Registro de uso |
| RESEARCH-ONLY | `urn:ondas:policy:research-only` | Rol `ResearchOrg` | Redistribución | Atribución · Registro de uso |
| COMMERCIAL-WITH-OBLIGATIONS | `urn:ondas:policy:commercial-with-obligations` | Rol `Commercial` | Sublicencia | Contraprestación · Reporte de uso · No reidentificación · Límite de retención · Atribución · Registro de uso |

## **3\. Cómo se instancia una plantilla**

El Data Provider parte de la plantilla correspondiente y sustituye los marcadores por los valores del asset y del contrato:

| Marcador | Contenido | Presente en |
| :---- | :---- | :---- |
| `{{ASSET_ID}}` | Identificador del asset en el catálogo (`dct:identifier`) | Las tres |
| `{{DID_PROVEEDOR}}` | DID de la organización proveedora (`dct:publisher`) | Las tres |
| `{{IMPORTE}}` | Contraprestación económica en euros | COMMERCIAL |
| `{{PERIODICIDAD_REPORTE}}` | Periodicidad del reporte de uso (ISO 8601, p. ej. `P3M`) | COMMERCIAL |
| `{{PLAZO_RETENCION}}` | Plazo máximo de retención por el consumidor (ISO 8601, p. ej. `P2Y`) | COMMERCIAL |

La política instanciada se asocia al asset en el momento de la publicación y se incorpora al contrato digital negociado vía conector EDC.

## **4\. OPEN**

**URN:** `urn:ondas:policy:open`

Acceso libre al asset para cualquier participante adherido al ONDAs Dataspace que presente una credencial verificable válida. No impone restricción de rol. El uso queda sujeto a atribución de la organización proveedora y al registro de la operación en el Transaction Log Register del espacio.

**Cuándo usarla:** datasets ambientales de interés general cuya reutilización se quiere maximizar, manteniendo la trazabilidad del uso y el reconocimiento de la fuente.

{

  "@context": "http://www.w3.org/ns/odrl.jsonld",

  "@type": "Set",

  "uid": "urn:ondas:policy:open",

  "profile": "urn:ondas:profile:v1",

  "dct:title": "OPEN — Acceso libre con obligación de atribución",

  "dct:description": "Acceso libre al asset para cualquier participante adherido al ONDAs Dataspace con credencial verificable válida. El uso queda sujeto a atribución de la organización proveedora y al registro de la operación en el log de auditoría del espacio.",

  "permission": \[

    {

      "target": "{{ASSET\_ID}}",

      "assigner": "{{DID\_PROVEEDOR}}",

      "action": \["read", "use"\],

      "constraint": \[\],

      "duty": \[

        {

          "action": "attribute",

          "dct:description": "Citar a la organización proveedora (dct:publisher del asset) en cualquier publicación, informe o producto derivado."

        },

        {

          "action": "logUsage",

          "dct:description": "La operación queda registrada en el Transaction Log Register del espacio de datos."

        }

      \]

    }

  \],

  "prohibition": \[\]

}

## **5\. RESEARCH-ONLY**

**URN:** `urn:ondas:policy:research-only`

Acceso limitado a participantes cuyo rol acreditado en la credencial verificable sea `ResearchOrg`. Prohíbe la redistribución del dataset a terceros no adheridos al espacio.

**Cuándo usarla:** datasets científicos, datos de laboratorio o series de sensores cuya reutilización se quiere circunscribir a entidades investigadoras acreditadas.

{

  "@context": "http://www.w3.org/ns/odrl.jsonld",

  "@type": "Set",

  "uid": "urn:ondas:policy:research-only",

  "profile": "urn:ondas:profile:v1",

  "dct:title": "RESEARCH-ONLY — Acceso restringido a entidades científicas acreditadas",

  "dct:description": "Acceso limitado a participantes cuyo rol acreditado en la credencial verificable sea ResearchOrg. Prohíbe la redistribución del dataset a terceros.",

  "permission": \[

    {

      "target": "{{ASSET\_ID}}",

      "assigner": "{{DID\_PROVEEDOR}}",

      "action": \["read", "use"\],

      "constraint": \[

        {

          "leftOperand": "role",

          "operator": "eq",

          "rightOperand": "ResearchOrg"

        }

      \],

      "duty": \[

        {

          "action": "attribute",

          "dct:description": "Citar a la organización proveedora en publicaciones científicas y productos derivados."

        },

        {

          "action": "logUsage",

          "dct:description": "La operación queda registrada en el Transaction Log Register del espacio de datos."

        }

      \]

    }

  \],

  "prohibition": \[

    {

      "target": "{{ASSET\_ID}}",

      "action": "distribute",

      "dct:description": "No se permite redistribuir el dataset ni cederlo a terceros no adheridos al ONDAs Dataspace."

    }

  \]

}

## **6\. COMMERCIAL-WITH-OBLIGATIONS**

**URN:** `urn:ondas:policy:commercial-with-obligations`

Acceso para participantes con rol `Commercial`, sujeto a contraprestación económica, reporte periódico de uso, prohibición de reidentificación y límite de retención. Prohíbe la sublicencia.

Las obligaciones económicas y de reporte son de **cumplimiento contractual**, supervisado por la AGED: no se bloquean técnicamente en el momento del acceso.

**Cuándo usarla:** explotación comercial de datasets del ecosistema, en el marco del modelo de sostenibilidad económica del espacio.

{

  "@context": "http://www.w3.org/ns/odrl.jsonld",

  "@type": "Set",

  "uid": "urn:ondas:policy:commercial-with-obligations",

  "profile": "urn:ondas:profile:v1",

  "dct:title": "COMMERCIAL-WITH-OBLIGATIONS — Acceso sujeto a condiciones comerciales específicas",

  "dct:description": "Acceso para participantes con rol Commercial, sujeto a contraprestación económica, reporte de uso, prohibición de reidentificación y límite de retención. Las obligaciones económicas y de reporte son de cumplimiento contractual, supervisado por la AGED.",

  "permission": \[

    {

      "target": "{{ASSET\_ID}}",

      "assigner": "{{DID\_PROVEEDOR}}",

      "action": \["read", "use"\],

      "constraint": \[

        {

          "leftOperand": "role",

          "operator": "eq",

          "rightOperand": "Commercial"

        }

      \],

      "duty": \[

        {

          "action": "compensate",

          "dct:description": "Contraprestación económica según las condiciones pactadas en el contrato digital negociado vía conector EDC.",

          "constraint": \[

            {

              "leftOperand": "payAmount",

              "operator": "eq",

              "rightOperand": "{{IMPORTE}}",

              "unit": "http://dbpedia.org/resource/Euro"

            }

          \]

        },

        {

          "action": "reportUsage",

          "dct:description": "Reportar periódicamente a la organización proveedora y a la AGED el uso efectivo del dataset.",

          "constraint": \[

            {

              "leftOperand": "recurrence",

              "operator": "eq",

              "rightOperand": "{{PERIODICIDAD\_REPORTE}}"

            }

          \]

        },

        {

          "action": "anonymize",

          "dct:description": "No reidentificar personas ni organizaciones a partir de datos anonimizados o agregados (Política de Seguridad y Privacidad §10)."

        },

        {

          "action": "delete",

          "dct:description": "Eliminar el dataset al vencer el plazo de retención acordado.",

          "constraint": \[

            {

              "leftOperand": "elapsedTime",

              "operator": "lteq",

              "rightOperand": "{{PLAZO\_RETENCION}}"

            }

          \]

        },

        {

          "action": "attribute",

          "dct:description": "Citar a la organización proveedora en cualquier producto o servicio derivado."

        },

        {

          "action": "logUsage",

          "dct:description": "La operación queda registrada en el Transaction Log Register del espacio de datos."

        }

      \]

    }

  \],

  "prohibition": \[

    {

      "target": "{{ASSET\_ID}}",

      "action": "sublicense",

      "dct:description": "No se permite sublicenciar el dataset ni cederlo a terceros bajo condiciones propias."

    }

  \]

}

## **7\. Enforcement técnico**

Verificado contra la especificación OpenAPI del middleware de D-Spacer (31/08/2026). Hay que distinguir **tres planos que suelen confundirse**:

| Plano | Qué ocurre | Estado |
| :---- | :---- | :---- |
| **Expresable en la política** | ODRL completo: `permission`, `constraint`, `LogicalConstraint`, `prohibition` y `obligation`, admitidos por `POST /policies/create` | Disponible por API |
| **Asignable desde el panel** | Tres modalidades preconstruidas —sin restricción, por lista de BPN, por fecha— que corresponden a los endpoints de atajo del conector | Limitado |
| **Aplicado en tiempo de ejecución** | Qué motor evalúa y hace cumplir cada elemento | **Sin confirmar por el proveedor** |

| Elemento ODRL | Cómo se aplica realmente |
| :---- | :---- |
| `constraint` sobre BPN | **Control de acceso efectivo.** Se evalúa en la negociación del contrato, sobre el **BPN** del participante. No intervienen credenciales verificables: la identidad es **Keycloak**, realm `connector-realm`, con token *bearer* |
| `constraint` sobre fecha | **Control de acceso efectivo.** Caducidad del acceso, disponible también desde el panel |
| `constraint` sobre grupo o caso de uso | **Control de acceso efectivo.** Se corresponde con el **KIT** del conector y con los grupos de socios (`tx:groups`) |
| `constraint` sobre `role` | **No disponible como tal.** El modelo no evalúa roles ni tipos de organización; se aproxima mediante lista de BPN o grupo de socios |
| `prohibition` (`distribute`, `sublicense`) | **Expresable, aplicación sin confirmar.** Cumplimiento contractual supervisado por la AGED y sancionable conforme al «E1.Protocolo de Gestión de Incidencias y Conflictos.pdf» §9 |
| `duty: logUsage` | El conector aporta **estadísticas de actividad por periodo, exportación a CSV** y un endpoint de telemetría por fecha. Queda por confirmar si equivale al *Transaction Log Register* del «E2.Documento de Cumplimiento y Auditoría.pdf» §5 |
| `duty: compensate`, `reportUsage` | **Expresables, aplicación sin confirmar.** Obligaciones contractuales supervisadas por la AGED |
| `duty: anonymize` (no reidentificación) | Obligación de conducta, recogida en «E1.Código Ético y de Conducta.pdf» §3.6 y §5.2 |
| `duty: delete` (plazo de retención) | **Expresable, aplicación sin confirmar.** Obligación contractual del consumidor, alineada con «E1.Políticas de gestión del ciclo de vida del dato.pdf» §8 |

**Consecuencia.** El respaldo contractual sigue siendo necesario, pero no porque la plataforma sea incapaz de expresar estas condiciones —sí lo es— sino porque **no está acreditado que las aplique**, y porque las obligaciones de uso posterior a la entrega son difíciles de imponer por medios técnicos en cualquier espacio de datos.

> **Constancia.** No está acreditado que el conector aplique `odrl:obligation` y `odrl:prohibition`, ni con qué motor. La AGED tomó conocimiento de este hecho en el **acuerdo 1.b** del acta 2/2026 y, mientras no se confirme, estas condiciones se sostienen como **obligación contractual bajo su supervisión**; el traslado de la pregunta al proveedor tecnológico queda encomendado en el **acuerdo 2** de la misma acta. Si se acreditara la aplicación automática, parte del control que hoy descansa en la supervisión de la AGED podría automatizarse y este catálogo se ampliaría en consecuencia.

## **8\. Ampliación del catálogo**

El Rulebook §6 indica que el ecosistema contempla **"inicialmente"** estas tres políticas, por lo que el catálogo es ampliable. Toda política nueva debe:

1. Ser **aprobada por la AGED**.  
2. Recibir un **URN** bajo el espacio de nombres `urn:ondas:policy:`.  
3. Documentar su **mapeo a constraints** del conector en el mapeo ODRL → conector.  
4. **Comunicarse a los participantes** conforme al «E1.Plan de Comunicación a Participantes.pdf», que clasifica el alta o modificación de una plantilla ODRL como cambio **sustancial** (30 días de preaviso).

---

## **Anexo — Trazabilidad**

| Contenido | Fundamento |
| :---- | :---- |
| Las tres políticas estándar | Rulebook §6 |
| Compromiso de poner las plantillas a disposición | Contrato de Adhesión §6.4 |
| Obligatoriedad del contrato digital vía EDC | Contrato de Adhesión §6.4 · Documento de Transferencia y Trazabilidad §7 |
| Enforcement de políticas | Documento de Transferencia y Trazabilidad §8 |
| Evaluación del rol en el acceso | Documento de Identidad y Control de Acceso §9, §11 |
| Registro de uso | Documento de Cumplimiento y Auditoría §4, §5 |
| No reidentificación | Política de Seguridad y Privacidad §10 |
| Mapeo ODRL → EDC / adapters | el mapeo ODRL → conector |

