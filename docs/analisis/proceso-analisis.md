# Proceso global de análisis y sistematización de datos para proyectos de monitoreo acústico pasivo

## 🗂️ Paso 1. Preparar datos

- [ ] **Completar la ficha de campo: [field deployments sheet](https://doi.org/10.5281/zenodo.16922848).** Se pueden agregar columnas adicionales según el proyecto, pero no modificar las existentes. Para un listado de mínimos, [ver documentación](https://pamflow.readthedocs.io/en/latest/data_standardization/data_exchange_format.html).

    !!! important
        Los nombres de los deploymentID deben seguir la convención `CODIGOGRABADORA-LOCATIONID-DEPLOYMENTSGROUP`.

- [ ] **Revisar manualmente los archivos de audio colectados: primeros y últimos archivos**
Eliminar el contenido que se encuentre fuera del periodo de muestreo. Esto incluye cualquier audio no deseado, como voces de personas que estuvieron en la instalación o ruidos provenientes del sensor. Eliminar archivos generados al configurar la grabadora con fechas de 1970 o 2106.

- [ ] **Nombrar las carpetas según el `deploymentID`** del la ficha de campo ([ver](https://pamflow.readthedocs.io/en/latest/data_standardization/data_exchange_format.html#file-organization)).
- [ ] **Renombrar los archivos de audio** usando el [siguiente script](https://github.com/pamflow-org/rename_audio_files).
- [ ] **Subir los audios al servidor compartido** (NAS ANH o NAS FPVA). Usar la convención `NúmeroProyecto_NombreCorto`, por ejemplo `25-203_FPVA`.

## 🐙 Paso 2. Crear nuevo repositorio

- [ ] Crear en el servidor de análisis una nueva subcarpeta de análisis `pamflow-all`. Nombrarla según la convención `NúmeroProyecto_NombreCorto`. Por ejemplo: `25-203_FPVA`.
- [ ] **Crear un repositorio independiente a partir de `pamflow`**, clonando la rama `dev` (la más actualizada):

  ```bash
  git clone https://github.com/pamflow-org/pamflow.git 25-203_FPVA
  cd 25-203_FPVA
  git checkout dev
  git remote remove origin
  ```
- [ ] **Solicitar la creación del repositorio** mediante el formulario de [repositorios DICO GitHub](https://docs.google.com/forms/d/e/1FAIpQLSe0qxu4h1gjcsnwOFC1t3dnQ6FHnORSSkqVKxXeS4RJ-w_vXw/viewform).
- [ ] **Conectar y publicar el código** en el nuevo repositorio, reemplazando `ORGANIZACION` por la organización correspondiente:

  ```bash
  git remote add origin https://github.com/ORGANIZACION/25-203_FPVA.git
  git push -u origin dev
  ```
## 📊 Paso 3. Analizar datos

- [ ] Seguir los análisis habituales de pamflow.
    - [ ] Ejecutar el paso a paso según la [documentación](https://pamflow.readthedocs.io/en/latest/documentation/pipeline_details.html).
    - [ ] Documentar un log de análisis donde se explique lo que se ha hecho hasta el momento ([template para log de análisis](https://docs.google.com/document/d/1H6zyFfu9CDPg9jEqwFeLbBUlxHaHT2yVquf-O1JyrPM/edit?tab=t.0#heading=h.twxt3imvtzwf)).
    - [ ] Documentar las grabadoras con fallas en `field_deployment_sheet.xlsx`, en la columna `deploymentTags`, con estos valores:
        - `deploymentQuality:valid`
        - `deploymentQuality:failed`
        - `failureCause:recorderStolen`
        - `failureCause:memoryCorrupted`

## 📤 Paso 4. Sistematizar información de análisis

- [ ] Sistematizar la información de especies en SiB Colombia (CEIBA + SiB).
- [ ] Diligenciar el [formulario I2D](https://docs.google.com/forms/d/e/1FAIpQLScVkQOoRugBoU_kbwDVtlRfmT-UzWV6_sLHnIY_ln4vKIINWQ/viewform).
- [ ] Sistematizar los audios en la CSA.
- [ ] Subir las salidas del proyecto a Zenodo.
