# BUSINESS INTELLIGENCE Y BIG DATA

## 1. Introducción

Business Intelligence (BI) y Big Data son áreas relacionadas con la recopilación, transformación, análisis y utilización de datos para apoyar la toma de decisiones.

- **Business Intelligence (BI):** se enfoca en convertir datos en información útil para analizar el estado y desempeño de una organización.
- **Big Data:** se enfoca en trabajar con grandes volúmenes de datos, que pueden ser generados a gran velocidad y en diferentes formatos.

---

# 2. CRISP-DM

## 2.1 ¿Qué es CRISP-DM?

**CRISP-DM** significa **Cross-Industry Standard Process for Data Mining** (Proceso Estándar Intersectorial para Minería de Datos).

Es un modelo de proceso utilizado para organizar proyectos de minería de datos y análisis de datos. Su objetivo es proporcionar una metodología estructurada para pasar desde la comprensión de un problema de negocio hasta la obtención y evaluación de resultados.

CRISP-DM se divide tradicionalmente en **6 fases**.

# 3. ETL

## 3.1 ¿Qué es ETL?

**ETL** significa:

- **Extract (Extraer)**
- **Transform (Transformar)**
- **Load (Cargar)**

Es un proceso utilizado para obtener datos desde diferentes fuentes, transformarlos y posteriormente cargarlos en un sistema de destino, normalmente un **Data Warehouse**.

Flujo:

**Fuentes de datos → Extracción → Transformación → Carga → Data Warehouse**

---

## 3.2 Extract - Extracción

Consiste en obtener los datos desde diferentes fuentes.

Ejemplos:

- Bases de datos SQL.
- Archivos CSV.
- Excel.
- APIs.
- Sistemas empresariales.
- Aplicaciones.
- Sensores.

**Ejemplo:**

Una empresa obtiene:

- Clientes desde PostgreSQL.
- Ventas desde MySQL.
- Productos desde un archivo Excel.

---

## 3.3 Transform - Transformación

Los datos obtenidos se limpian y modifican para que tengan una estructura adecuada.

Operaciones comunes:

- Eliminar duplicados.
- Corregir valores.
- Convertir tipos de datos.
- Normalizar formatos.
- Combinar información.
- Calcular nuevas variables.
- Filtrar registros.

**Ejemplo:**

Un sistema almacena:

`2026/09/05`

y otro:

`05-09-2026`

Durante la transformación ambos pueden convertirse a un formato estándar.

---

## 3.4 Load - Carga

Los datos transformados se cargan en el sistema de destino.

Por ejemplo:

**Base de datos → ETL → Data Warehouse**

Una vez cargados, los datos pueden utilizarse para:

- Reportes.
- Dashboards.
- Análisis.
- Indicadores KPI.
- Business Intelligence.

---

## 3.5 Ejemplo completo de ETL

Una tienda tiene tres fuentes:

- Ventas en PostgreSQL.
- Clientes en MySQL.
- Productos en Excel.

El proceso sería:

1. **Extract:** obtener los datos de las tres fuentes.
2. **Transform:** limpiar nombres, fechas, precios y registros duplicados.
3. **Load:** cargar los datos preparados en un Data Warehouse.
4. **BI:** utilizar los datos para generar reportes y dashboards.

---

# 4. ELT

## 4.1 ¿Qué es ELT?

**ELT** significa:

- **Extract (Extraer)**
- **Load (Cargar)**
- **Transform (Transformar)**

A diferencia de ETL, primero se cargan los datos en el sistema de destino y después se transforman.

Flujo:

**Fuentes de datos → Extracción → Carga → Transformación → Data Warehouse / Data Lake**

---

## 4.2 ¿Cómo funciona ELT?

### 1. Extract

Se extraen los datos desde diferentes fuentes.

### 2. Load

Los datos se cargan inicialmente en el sistema de destino, incluso si todavía no están completamente limpios o transformados.

### 3. Transform

Las transformaciones se realizan dentro del sistema de destino utilizando su capacidad de procesamiento.

Esto es especialmente útil cuando se trabaja con plataformas modernas de almacenamiento y procesamiento de grandes cantidades de datos.

---

# 5. ETL vs ELT

| Característica | ETL | ELT |
|---|---|---|
| Orden | Extraer → Transformar → Cargar | Extraer → Cargar → Transformar |
| Transformación | Antes de cargar | Después de cargar |
| Datos originales | Normalmente se carga el resultado transformado | Puede conservarse el dato original |
| Uso tradicional | Data Warehouses tradicionales | Plataformas modernas, Data Lakes y arquitecturas Big Data |
| Procesamiento | Se realiza principalmente antes de la carga | Se aprovecha el procesamiento del destino |
| Flexibilidad | Menor para datos que cambian frecuentemente | Mayor flexibilidad |
| Idea principal | Preparar antes de almacenar | Almacenar primero y transformar después |

### Regla sencilla para recordar

**ETL:** primero transformo, después cargo.

**ELT:** primero cargo, después transformo.

---

# 6. Estadística descriptiva

## 6.1 ¿Qué es?

La **estadística descriptiva** se utiliza para organizar, resumir y describir los datos que ya tenemos.

Busca responder:

**¿Qué ocurrió?**

Ejemplos:

- Promedio de ventas.
- Venta máxima.
- Venta mínima.
- Cantidad de clientes.
- Porcentaje de productos vendidos.
- Distribución de edades.

---

## 6.2 Medidas importantes

### Media

Representa el promedio de un conjunto de valores.

Ejemplo:

Ventas:

`10, 20, 30`

Media:

`(10 + 20 + 30) / 3 = 20`

---

### Mediana

Es el valor que queda en el centro cuando los datos están ordenados.

Ejemplo:

`10, 20, 30`

Mediana = `20`

---

### Moda

Es el valor que aparece con mayor frecuencia.

Ejemplo:

`10, 20, 20, 30`

Moda = `20`

---

### Mínimo y máximo

Indican el valor menor y mayor de un conjunto de datos.

Ejemplo:

`10, 20, 30, 40`

- Mínimo = 10
- Máximo = 40

---

### Desviación estándar

Indica qué tan dispersos están los datos respecto a su media.

Una desviación estándar pequeña indica que los valores están relativamente cerca de la media.

Una desviación estándar grande indica mayor dispersión.

---

# 7. Estadística prescriptiva

## 7.1 ¿Qué es?

La **estadística prescriptiva** busca determinar **qué acción debería realizarse** utilizando los datos y los resultados del análisis.

La pregunta principal es:

**¿Qué deberíamos hacer?**

En la práctica, el análisis prescriptivo suele apoyarse también en técnicas de optimización, simulación, modelos predictivos y reglas de decisión.

---

## 7.2 Ejemplo

Una empresa analiza sus ventas.

### Estadística descriptiva

Pregunta:

**¿Cuánto vendimos?**

Resultado:

> Las ventas promedio fueron de 50.000 Bs durante el último mes.

### Análisis predictivo

Pregunta:

**¿Cuánto probablemente venderemos?**

Resultado:

> Se estima que las ventas del próximo mes serán de 55.000 Bs.

### Análisis prescriptivo

Pregunta:

**¿Qué deberíamos hacer para aumentar las ventas?**

Resultado:

> Se recomienda aumentar el inventario de los productos con mayor demanda y aplicar promociones en los productos con menor rotación.

---

# 8. Descriptiva vs Prescriptiva

| Aspecto | Descriptiva | Prescriptiva |
|---|---|---|
| Pregunta | ¿Qué ocurrió? | ¿Qué deberíamos hacer? |
| Objetivo | Describir datos | Recomendar acciones |
| Utiliza | Datos históricos y actuales | Datos + modelos + restricciones + objetivos |
| Resultado | Información y estadísticas | Recomendaciones o decisiones |
| Ejemplo | Ventas promedio = 50.000 Bs | Aumentar inventario de productos de alta demanda |

---

# 9. Relación entre los conceptos

Estos conceptos pueden formar parte de un mismo proyecto de Business Intelligence y Big Data.

Ejemplo:

Una empresa quiere mejorar sus ventas.

**1. CRISP-DM**

Permite organizar el proyecto completo:

Negocio → Datos → Preparación → Modelado → Evaluación → Despliegue

**2. ETL / ELT**

Permiten preparar y mover los datos:

Fuentes → ETL/ELT → Almacenamiento → Datos disponibles para análisis

**3. Estadística descriptiva**

Permite conocer qué está ocurriendo:

Ventas, promedios, máximos, mínimos, tendencias, etc.

**4. Análisis prescriptivo**

Permite recomendar qué hacer:

Modificar precios, aumentar inventario, realizar promociones, cambiar recursos, etc.

---

# 10. Ejemplo integrador

Supongamos una empresa que vende productos por Internet.

Tiene información almacenada en:

- Base de datos de clientes.
- Base de datos de ventas.
- Archivo Excel de productos.
- Datos de navegación de la página web.

### Paso 1: CRISP-DM

Se define el objetivo:

> Aumentar las ventas y reducir el abandono de clientes.

### Paso 2: ETL o ELT

Se recopilan los datos de las diferentes fuentes.

Se limpian, integran y almacenan para su análisis.

### Paso 3: Estadística descriptiva

Se obtiene:

- Venta promedio.
- Producto más vendido.
- Producto menos vendido.
- Clientes con mayor número de compras.
- Ventas por mes.
- Ventas por región.

### Paso 4: Análisis avanzado

Se pueden crear modelos para identificar:

- Clientes con riesgo de abandonar.
- Productos que tendrán mayor demanda.
- Clientes que probablemente comprarán determinados productos.

### Paso 5: Análisis prescriptivo

Finalmente se pueden generar recomendaciones:

- Ofrecer promociones a determinados clientes.
- Aumentar el inventario de productos con alta demanda.
- Reducir el inventario de productos con baja rotación.
- Recomendar productos personalizados.

### Resultado

Los datos pasan de ser simples registros a convertirse en información y posteriormente en decisiones para el negocio.

---

# 11. Conceptos clave para recordar

## CRISP-DM

**Proceso para desarrollar proyectos de minería de datos.**

6 fases:

**Negocio → Datos → Preparación → Modelado → Evaluación → Despliegue**

## ETL

**Extract → Transform → Load**

**Extraer → Transformar → Cargar**

## ELT

**Extract → Load → Transform**

**Extraer → Cargar → Transformar**

## Estadística descriptiva

**¿Qué ocurrió?**

Describe y resume los datos.

## Análisis prescriptivo

**¿Qué deberíamos hacer?**

Utiliza los resultados del análisis para recomendar acciones.

---

# 12. Preguntas típicas de examen

### 1. ¿Qué significa CRISP-DM?

Cross-Industry Standard Process for Data Mining.

### 2. ¿Cuáles son las fases de CRISP-DM?

1. Comprensión del negocio.
2. Comprensión de los datos.
3. Preparación de los datos.
4. Modelado.
5. Evaluación.
6. Despliegue.

### 3. ¿Qué diferencia existe entre ETL y ELT?

En ETL los datos se transforman antes de cargarlos; en ELT primero se cargan y posteriormente se transforman.

### 4. ¿Qué significa ETL?

Extract, Transform, Load.

### 5. ¿Qué significa ELT?

Extract, Load, Transform.

### 6. ¿Qué hace la estadística descriptiva?

Resume y describe los datos disponibles.

### 7. ¿Qué pregunta responde la estadística descriptiva?

**¿Qué ocurrió?**

### 8. ¿Qué pregunta responde el análisis prescriptivo?

**¿Qué deberíamos hacer?**

### 9. ¿Cuál es la diferencia principal entre descriptiva y prescriptiva?

La descriptiva describe lo ocurrido mediante los datos; la prescriptiva busca recomendar acciones para tomar decisiones.

---

# 13. Resumen final

| Concepto | Idea principal | Pregunta |
|---|---|---|
| CRISP-DM | Organiza un proyecto de minería de datos | ¿Cómo desarrollamos el proyecto? |
| ETL | Extrae, transforma y carga datos | ¿Cómo preparamos los datos antes de almacenarlos? |
| ELT | Extrae, carga y transforma datos | ¿Cómo aprovechamos el procesamiento del destino? |
| Descriptiva | Resume los datos existentes | ¿Qué ocurrió? |
| Prescriptiva | Recomienda acciones | ¿Qué deberíamos hacer? |

> **Idea general:** En Business Intelligence y Big Data, primero necesitamos obtener y preparar los datos (ETL/ELT), podemos organizar el proyecto mediante CRISP-DM, analizar los datos mediante técnicas estadísticas y finalmente utilizar los resultados para apoyar la toma de decisiones, incluyendo recomendaciones prescriptivas.
