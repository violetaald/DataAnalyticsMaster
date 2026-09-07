# DataAnalyticsMaster

# 📊 Análisis del Catálogo de Netflix: Limpieza, Exploración y Dashboard Interactivo

## 📖 Descripción del proyecto

Este proyecto tiene como objetivo analizar el catálogo de contenidos de **Netflix** a partir de una base de datos que recoge información sobre películas y series disponibles en la plataforma.

El trabajo se ha desarrollado íntegramente en **Microsoft Excel**, partiendo de una base de datos original que posteriormente ha sido revisada, limpiada y transformada para facilitar su análisis.

El resultado final es un **Dashboard interactivo** que permite explorar de forma visual las principales características del catálogo, identificar patrones y comparar la distribución de contenidos según diferentes variables como el tipo de contenido, la clasificación por edades, el género, el país o la década de estreno.

Para desarrollar el proyecto se han utilizado principalmente:

- Limpieza y depuración de datos.
- Tratamiento de valores nulos.
- Creación de nuevas variables derivadas.
- Estructuración de los datos mediante una tabla de Excel.
- Tablas dinámicas para resumir la información.
- Gráficos vinculados a los resultados del análisis.
- Segmentaciones de datos o **slicers** para aportar interactividad.
- Creación de indicadores KPI para resumir las métricas principales.
- Diseño de un Dashboard final orientado a facilitar la interpretación de los datos.

---

# 🔎 Metodología y pasos seguidos

## 1. Importación y conservación de los datos originales

El primer paso consistió en trabajar con la base de datos original del catálogo de Netflix.

Para mantener una referencia de los datos de partida, se conservó una hoja denominada **`RAW DATA`**, que contiene la información sin transformar.

La base original contiene **8.807 registros** y 12 variables:

- `show_id`
- `type`
- `title`
- `director`
- `cast`
- `country`
- `date_added`
- `release_year`
- `rating`
- `duration`
- `listed_in`
- `description`

Mantener los datos originales separados de los datos procesados permite conservar la trazabilidad del análisis y comparar posteriormente la información inicial con el resultado de la limpieza.

---

## 2. Exploración inicial de la base de datos

Antes de comenzar el análisis se realizó una revisión de las variables para detectar posibles problemas de calidad.

Durante esta exploración se identificaron principalmente:

- Valores vacíos en `director`.
- Valores vacíos en `cast`.
- Países sin información.
- Registros sin fecha de incorporación a Netflix.
- Registros sin clasificación `rating`.
- Registros sin información de duración.

Los campos con mayor número de valores ausentes eran:

- **Director:** 2.634 valores vacíos.
- **País:** 831 valores vacíos.
- **Reparto:** 825 valores vacíos.
- **Fecha de incorporación:** 10 valores vacíos.
- **Rating:** 4 valores vacíos.
- **Duración:** 3 valores vacíos.

Esta revisión permitió decidir qué datos podían completarse con una categoría genérica y qué registros no disponían de información suficiente para poder formar parte correctamente del análisis.

---

## 3. Limpieza y tratamiento de los datos

Una vez identificados los principales problemas de calidad, se creó la hoja **`DATOS LIMPIOS`**.

El objetivo fue generar una base preparada específicamente para realizar cálculos, tablas dinámicas y visualizaciones.

### Tratamiento de valores ausentes

En aquellas variables descriptivas donde la ausencia de información no impedía realizar el análisis, los valores vacíos se sustituyeron por:

**`No especificado`**

Este tratamiento se aplicó, entre otros, a campos como:

- Director.
- Reparto.
- País.

De esta manera se evita perder registros únicamente porque alguna característica descriptiva no esté disponible y, al mismo tiempo, se puede identificar claramente esta ausencia dentro del análisis.

### Eliminación de registros incompletos

Se eliminaron **17 registros** que no disponían de información necesaria para las transformaciones posteriores:

- 10 registros sin `date_added`.
- 4 registros sin `rating`.
- 3 registros sin `duration`.

Después de este proceso, la base utilizada para el análisis quedó formada por:

**8.790 títulos.**

---

## 4. Creación de nuevas variables

A partir de los campos originales se generaron nuevas columnas para facilitar la segmentación y el análisis de la información.

La tabla final pasó de las 12 variables originales a **23 variables**.

### Año de incorporación

A partir de `date_added` se generó:

**`year_added`**

Permite conocer en qué año fue incorporado cada título al catálogo de Netflix.

### Mes de incorporación

También se extrajo:

- `month_added`
- `month_name`

Estas variables permiten analizar posibles patrones temporales de incorporación de contenido.

### Década de estreno

A partir de `release_year` se generaron:

- `decade`
- `decade_label`

Por ejemplo:

- 1980 → `1980s`
- 1997 → `1990s`
- 2021 → `2020s`

Esta transformación permite analizar de forma más sencilla cómo se distribuye el catálogo según la época de estreno de los contenidos.

### Tratamiento de la duración

La variable original `duration` contiene dos tipos diferentes de información:

- Minutos para las películas.
- Número de temporadas para las series.

Para poder analizarlas correctamente se separó esta información en varias columnas:

- `duration_value`
- `duration_unit`
- `duration_minutes`
- `duration_seasons`

Así, las películas pueden analizarse mediante su duración media en minutos y las series mediante su número de temporadas.

### País principal

La variable `country` puede contener más de un país por título.

Para simplificar determinadas visualizaciones se creó:

**`primary_country`**

Esta variable permite asignar un país principal a cada registro y realizar rankings y comparaciones de forma más clara.

### Género principal

Del mismo modo, `listed_in` puede contener varios géneros asociados al mismo contenido.

Se creó por tanto:

**`primary_genre`**

Esta variable permite clasificar cada título según su género principal y construir posteriormente rankings de géneros.

---

## 5. Conversión de la base limpia en una tabla estructurada

Una vez finalizada la limpieza y las transformaciones, la base se convirtió en una **Tabla de Excel**.

Esta decisión permite trabajar con un rango de datos estructurado y facilita:

- La actualización de las tablas dinámicas.
- La aplicación de filtros.
- La identificación automática de los campos.
- La organización de las diferentes variables.
- Una estructura más robusta para el Dashboard.

La tabla contiene finalmente **8.790 registros y 23 variables**.

---

## 6. Creación de las tablas dinámicas

A partir de los datos limpios se creó la hoja **`RESUMEN GENERAL`**.

Esta hoja funciona principalmente como capa intermedia entre la base de datos y el Dashboard.

Se construyeron diferentes **tablas dinámicas** para obtener los principales indicadores y distribuciones del catálogo.

Entre los análisis realizados se encuentran:

- Número de títulos por tipo de contenido.
- Distribución por década.
- Distribución por países.
- Distribución por géneros.
- Distribución según `rating`.
- Análisis temporal.
- Duración de las películas.
- Número de temporadas de las series.

En total, el libro contiene **10 tablas dinámicas**, utilizadas como fuente para los distintos elementos analíticos del proyecto.

Separar esta capa de cálculo del Dashboard permite mantener la visualización final más limpia y facilita la actualización de los datos.

---

## 7. Definición de los principales KPI

Se seleccionaron varios indicadores para ofrecer una visión rápida del catálogo desde la parte superior del Dashboard.

Entre ellos se encuentran:

### 🎬 Total de títulos

El catálogo analizado contiene:

**8.790 títulos**

### 🎥 Películas

Se identificaron:

**6.126 películas**

Las películas representan aproximadamente el **69,7 %** de los contenidos analizados.

### 📺 Series

Se identificaron:

**2.664 series**

Las series representan aproximadamente el **30,3 %** del catálogo.

### ⏱ Duración media de las películas

A partir de `duration_minutes` se calculó una duración media aproximada de:

**99,6 minutos**

### 📚 Número medio de temporadas

Para las series, el promedio se sitúa aproximadamente en:

**1,75 temporadas**

Estos KPI permiten comprender rápidamente la dimensión y composición general del catálogo antes de profundizar en las diferentes visualizaciones.

---

## 8. Creación de las visualizaciones

A continuación se construyeron diferentes gráficos para representar las principales dimensiones del análisis.

### Mix de contenido

Se creó un gráfico para comparar la proporción de:

- Movies.
- TV Shows.

El análisis muestra un claro predominio de las películas dentro de la base de datos.

### Distribución por país

Se desarrolló un ranking que permite visualizar los países con mayor presencia en el catálogo.

Entre los países con mayor número de títulos destacan:

1. Estados Unidos.
2. India.
3. Reino Unido.
4. Canadá.
5. Japón.

Estados Unidos es claramente el país con mayor representación dentro de los datos.

### Distribución por género

Se analizaron los géneros principales utilizando `primary_genre`.

Entre los géneros con mayor presencia aparecen:

- Dramas.
- Comedies.
- Action & Adventure.
- Documentaries.
- International TV Shows.

El género **Dramas** es el que presenta el mayor número de títulos dentro de la clasificación principal utilizada.

### Distribución por rating

También se analizó la clasificación de los contenidos según su `rating`.

Las categorías con mayor presencia son:

- TV-MA.
- TV-14.
- TV-PG.
- R.
- PG-13.

La categoría **TV-MA** es la más frecuente de todo el catálogo analizado.

### Distribución por décadas

Mediante la variable `decade_label` se desarrolló una visualización para estudiar de qué décadas proceden los contenidos disponibles en la plataforma.

El rango de años de estreno presente en la base va desde **1925 hasta 2021**, aunque el catálogo se concentra especialmente en producciones recientes.

---

## 9. Incorporación de filtros interactivos

Para transformar el informe en una herramienta de análisis y no únicamente en una visualización estática, se incorporaron **segmentaciones de datos o slicers de Excel**.

El Dashboard incluye slicers para:

- **TYPE**
- **RATING**
- **GENRE**
- **COUNTRY**
- **DECADE**

Estos filtros están vinculados a las tablas dinámicas correspondientes y permiten modificar la información mostrada en el Dashboard de forma interactiva.

Por ejemplo, es posible seleccionar únicamente:

- Series.
- Una clasificación concreta.
- Un género determinado.
- Un país.
- Una década específica.

Esto permite realizar múltiples combinaciones y explorar diferentes segmentos del catálogo sin modificar manualmente la base de datos.

---

## 10. Construcción del Dashboard final

Finalmente se creó la hoja **`DASHBOARD`**, cuyo objetivo es concentrar los resultados más relevantes en una única vista.

El Dashboard combina:

- Indicadores KPI.
- Gráficos.
- Rankings.
- Tablas dinámicas.
- Segmentaciones de datos.
- Diseño visual unificado.

Para mejorar la lectura del informe se aplicó una identidad gráfica común, utilizando el color **#FF9999** como tono predominante.

El diseño busca proporcionar una interfaz limpia y sencilla que permita comenzar por una visión general del catálogo y posteriormente profundizar mediante los diferentes slicers.

---

# 🗂️ Estructura del proyecto

El archivo de Excel se organiza en cuatro hojas principales:

```text
Netflix_Analisis_Dashboard_VioletaAldrey.xlsx
│
├── RAW DATA
│   └── Base de datos original sin transformar.
│
├── DATOS LIMPIOS
│   └── Base depurada y enriquecida con variables adicionales.
│
├── RESUMEN GENERAL
│   └── Tablas dinámicas y cálculos utilizados para el análisis.
│
└── DASHBOARD
    └── KPIs, gráficos y slicers interactivos.
```

Esta organización sigue un flujo lógico:

**Datos originales → Limpieza y transformación → Análisis → Visualización**

De esta manera se mantiene separada cada fase del proyecto y resulta más sencillo revisar o actualizar el análisis.

---

# 🛠️ Instalación y requisitos

Para consultar el proyecto no es necesario instalar librerías de programación ni ejecutar código adicional.

### Requisitos

Se recomienda utilizar:

- **Microsoft Excel**.
- Una versión compatible con tablas dinámicas.
- Compatibilidad con gráficos de Excel.
- Compatibilidad con segmentaciones de datos o slicers.

Para disfrutar de toda la interactividad del Dashboard es recomendable abrir el archivo directamente en **Microsoft Excel de escritorio**.

### Uso

1. Abrir el archivo `Netflix_Analisis_Dashboard_VioletaAldrey.xlsx`.
2. Acceder a la hoja `DASHBOARD`.
3. Utilizar los slicers para seleccionar los segmentos que se quieran analizar.
4. Observar cómo se actualizan los indicadores y visualizaciones asociados.
5. Limpiar los filtros de los slicers para volver a visualizar el catálogo completo.

---

# 📊 Resultados y conclusiones

A partir del análisis realizado se pueden extraer varias conclusiones principales.

### 1. Predominio de las películas

De los **8.790 títulos** analizados:

- 6.126 son películas.
- 2.664 son series.

Por tanto, aproximadamente siete de cada diez contenidos de la base son películas.

### 2. Estados Unidos lidera la producción representada

Estados Unidos presenta la mayor cantidad de títulos asociados como país principal, seguido por mercados como India y Reino Unido.

Esto refleja una fuerte presencia de producciones estadounidenses, aunque el catálogo presenta una diversidad geográfica considerable.

### 3. Los dramas son el género principal más frecuente

El análisis de `primary_genre` sitúa a **Dramas** como la categoría con mayor representación, seguida por Comedies y Action & Adventure.

### 4. Predominio de las clasificaciones TV-MA y TV-14

Las clasificaciones con más registros son **TV-MA** y **TV-14**, lo que indica una elevada presencia de contenido dirigido principalmente a público adolescente y adulto.

### 5. El catálogo está orientado a contenido relativamente reciente

Aunque el conjunto de datos contiene producciones desde **1925**, existe una concentración importante de títulos pertenecientes a décadas recientes.

### 6. Las películas tienen una duración cercana a 100 minutos

La duración media de las películas se sitúa alrededor de los **99,6 minutos**, lo que proporciona una referencia sobre la extensión habitual del contenido cinematográfico disponible en la base.

### 7. Las series presentan generalmente pocas temporadas

El número medio de temporadas es aproximadamente **1,75**, indicando una alta presencia de series con una o dos temporadas dentro del conjunto de datos.

---

# 🔄 Próximos pasos

El proyecto puede ampliarse en futuras versiones mediante diferentes líneas de análisis.

Algunas posibilidades serían:

- Analizar la evolución de incorporaciones al catálogo por año y mes.
- Comparar géneros entre países.
- Estudiar por separado películas y series.
- Analizar la relación entre década, país y género.
- Examinar qué directores aparecen con mayor frecuencia.
- Analizar actores y actrices con mayor presencia en el catálogo.
- Crear indicadores adicionales sobre duración.
- Incorporar nuevas versiones de la base de datos para comprobar cómo evoluciona el catálogo con el tiempo.
- Automatizar la actualización de los datos mediante Power Query.
- Incorporar métricas externas, como popularidad, valoraciones o rendimiento de cada contenido, si estuvieran disponibles.

Estas ampliaciones permitirían convertir el Dashboard actual en una herramienta todavía más completa para estudiar la evolución y composición de la oferta de Netflix.

---

# 🤝 Contribuciones

Este proyecto puede seguir ampliándose mediante nuevas métricas, visualizaciones o fuentes de datos.

Cualquier mejora debería mantener la estructura utilizada durante el proyecto:

**datos originales → limpieza → transformación → análisis → visualización**

De esta forma se garantiza que las modificaciones sean trazables y no afecten a la integridad de la base original.

---

# ✒️ Autora

**Violeta Aldrey**

Proyecto de análisis de datos y creación de Dashboard interactivo en Microsoft Excel.
