# CyL_ITEAF

Este repositorio contiene el conjunto de datos unificado y georreferenciado de las **Inspecciones Técnicas de Equipos de Aplicación de Fitosanitarios (ITEAF)** en las provincias de **Ávila** y **Segovia**.

El dataset transforma los informes operativos (Memorias Quincenales) en un recurso de datos geoespaciales listo para su integración en **Espacios de Datos Agrícolas** o análisis en **SIG (QGIS/ArcGIS)**.

---

## 📊 Origen de los Datos
Los datos provienen de las memorias de actuación de la **Junta de Castilla y León** (Dirección General de Producción Agropecuaria). Recogen la actividad de las estaciones ITEAF encargadas de verificar la maquinaria agrícola para el cumplimiento del **RD 1702/2011**.

---

## 🛠️ Proceso de Transformación (ETL)
Para garantizar la calidad del dato y el cumplimiento de normativas de interoperabilidad, se han aplicado los siguientes procesos mediante **Python**:

* **Unificación:** Consolidación de múltiples archivos Excel dispersos en estructuras de carpetas quincenales.
* **Normalización:** Limpieza de nombres de municipios y provincias (unificación de mayúsculas y eliminación de tildes para evitar duplicados).
* **Georreferenciación:** Vinculación de datos al centroide de cada municipio mediante *Fuzzy Matching* (búsqueda difusa) para corregir discrepancias en los nombres administrativos.
* **Tipado de Datos:**
    * **Fechas:** Formato `Date` real para permitir filtros cronológicos.
    * **Métricas:** Valores enteros (`Integer`) para conteos precisos de equipos.

---

## 📁 Estructura del Dataset (Atributos del SHP)

| Atributo | Tipo | Descripción |
| :--- | :--- | :--- |
| **FECHA_INS** | `Date` | Fecha de la inspección técnica (formato YYYY-MM-DD). |
| **PROVINCIA** | `String` | Nombre de la provincia (Normalizado: AVILA, SEGOVIA). |
| **MUNICIPIO** | `String` | Nombre del municipio donde se realizó la actuación. |
| **INS_1_PRI** | `Integer` | Equipos presentados a primera inspección. |
| **INS_2_SEG** | `Integer` | Equipos presentados a segunda inspección (repesca). |
| **FAV_NUM** | `Integer` | Cantidad de equipos con resultado **FAVORABLE**. |
| **DESFAV_NUM** | `Integer` | Cantidad de equipos con resultado **DESFAVORABLE**. |

---


