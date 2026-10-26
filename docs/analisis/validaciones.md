# Sistematización de validaciones manuales

Este protocolo define los campos que debe tener cada registro sujeto a validación manual y los valores permitidos para la etiqueta de validación.

!!! warning "Borrador"
    Las definiciones de esta página son una propuesta inicial y deben ser revisadas por el equipo.

## Campos requeridos

| Campo | Descripción |
|---|---|
| `observationID` | Identificador único de la observación (detección) a validar. |
| Quién identifica | Origen de la identificación: BirdNET 2.4, Perch 2.0 o un validador humano (p. ej., Maria Paula Toro). |
| `scientificNameModel` | Especie propuesta por la detección automatizada. |
| `classificationProbability` | Probabilidad o puntaje de confianza asignado por el modelo. |
| `label` | Resultado de la validación (ver valores permitidos). |
| `scientificNameValidated` | Nombre científico final, después de la validación. |
| `favorite` | Marca para señalar registros destacados (p. ej., ejemplares de referencia para la CSA). |

## Valores permitidos para `label`

| Valor | Significado propuesto |
|---|---|
| `Positive` | La especie propuesta por el modelo es correcta. |
| `Negative` | La especie propuesta por el modelo es incorrecta y no se identifica otra. |
| `Uncertain` | No es posible confirmar ni descartar la identificación. |
| `Reassigned` | La identificación del modelo es incorrecta y se asigna otra especie en `scientificNameValidated`. |
| `Multitaxa` | El segmento contiene más de un taxón. |

## Procedimiento

1. Cargar el segmento con su `observationID`, `scientificNameModel` y `classificationProbability`.
2. Escuchar el segmento y revisar el espectrograma.
3. Asignar un valor de `label`.
4. Completar `scientificNameValidated` cuando el valor sea `Positive` o `Reassigned`.
5. Marcar `favorite` si el registro es un buen ejemplar de referencia.