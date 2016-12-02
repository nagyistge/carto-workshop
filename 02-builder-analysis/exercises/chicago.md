# Police Stations Location Demo

* *Degree of Difficulty*: **

* *Goal*: explore how far police stations locations are from crimes centroids per district in the city of Chicago.

* *Features Highlighted*:
  * Widgets: Category, Time Series & Formula.
  * Analysis: Find centroid from geometries & Connect with lines.

* *Datasests needed*:
  * Chicago Crimes (**`chicago_crimes`**): download it [from the `builder-demo` CARTO account](https://team.carto.com/u/builder-demo/tables/chicago_crimes/public) and import it into CARTO from your local machine as a csv file.
  * Chicago Police Stations (**`chicago_police_stations`**): download it [from the `builder-demo` CARTO account](https://team.carto.com/u/builder-demo/tables/chicago_police_stations/public) and import it into CARTO from your local machine as a csv file.

<br>

## Instructions

### 1. Import datasets and create a map

#### 1. 1. Import datasets into CARTO

* Show how easy is to import files into CARTO! Drag and drop in CARTO Datasets dashboard, first **`chicago_crimes`**, and then **`chicago_police_stations`** csv files. Explain the viewer the wide diversity of geodata supported in CARTO during the importing.

* Select `chicago_crimes` and `chicago_police_stations`, click on `NEW MAP`.

#### 1. 3. Rename map title and layers

* Rename map title to **`Police Stations Location Demo`**.
* Rename layers:
  1. `chicago_crimes` as `Crimes`,
  2. `chicago_police_stations` as `Police Stations`,

<br>

### 2. Layers and widgets

#### 2. 1. Show the different options layers have

* Click on the `Positron` basemap and select `Dark Matter Lite`.
* Comment that each layer has 5 options: `DATA`, `ANALYSES`, `STYLE`, `POP-UPS` and `LEGENDS`.

#### 2. 2. Add widgets in order to explore crimes layer

* Back to the main menu, click on `Crimes` layer.
* In the `DATA` view. Activate the checkbox options on `point count`, `date` and `primary_type`.
* Rename them as "Number of Crimes", "Date" and "Type of Crime" respectively.

<br>

### 3. Add Analysis and styles

#### 3. 1. Create crimes centroids for district

* Back to the main menu, click on `ADD ANALYSIS` just below `Analysis` layer.
* Select `Find centroid from geometries` analysis.
* Click on `ADD ANALYSIS`.
* Set the parameters as follows:
  * `CATEGORIZE...`: `district_char`.
* Click on `APPLY`.

#### 3. 2. Style crimes layer

* After applying the analysis, drag and drop out the original node layer. Rename the analysis node layer as `Centroids`.

> Now you should have a mess of points, three layers equally styled.

* In order to style the `Crimes` layer follow these steps:
  * Click on `Crimes` layer.
  * Click on `STYLE`:
    * `FILL`: set the marker size value to `1` and color to yellow (`#FFE95C`).
    * `STROKE`: set stroke width to `0`.
    * `BLENDING`: `multiply`.

![style](https://cloud.githubusercontent.com/assets/5215798/19149588/e38b427c-8bc2-11e6-8d2a-7b5f73bb658c.png)

#### 3. 3. Connect police stations with centroids and calculate distances

* Add a new analysis (to the `Centroids` layer).
* Select `Connect with lines`.
* Click on `ADD ANALYSIS`.
* Set the parameters as follows:
  * `TYPE`: `To Source`
  * Check the `GROUP BY` option:
    * `SOURCE COL.`: `category`.
    * `TARGET COL.`: `district_char`.

![lines](https://cloud.githubusercontent.com/assets/5215798/19149598/e81efc8e-8bc2-11e6-9a4b-ba709c3b480f.png)

> Show the viewer (click on `DATA` and change to table view) the new fields created from this analysis, especially the `length` column.

#### 3. 4. Style police stations, centroids and lines layers

* After applying the analysis, drag and drop out the "Connect..." analysis node layer, on top of Crimes but below `Police Stations` and `Centroids`. Rename the analysis node layer as `Lines`.

##### Lines style

* In order to style the `Lines` layer follow these steps:
  * Click on `Lines` layer.
  * Click on `STYLE`:
    * `FILL`: set the line width value to `3` and color to picton blue (`#40B4E5`).

##### Centroids style

* In order to style the `Police Stations` layer follow these steps:
  * Click on `Crimes` layer.
  * Click on `STYLE`:
    * `FILL`: set the marker size value to `20` and color to wageningen green (`#3FAE29`).
    * `STROKE`: set stroke width to `0`.
    * Check the `Labels` option:
      * `COLUMN`: `category`.
      * `SIZE`: `8`.
      * `HALO`: `0`.
      * `OFFSET`: `0`.

##### Police Stations style

* In order to style the `Police Stations` layer follow these steps:
  * Click on `Crimes` layer.
  * Click on `STYLE`:
    * `FILL`: set the marker size value to `20` and color to dark pink (`#EA526F`).
    * `STROKE`: set stroke width to `0`.
    * Check the `Labels` option:
      * `COLUMN`: `district_char`.
      * `SIZE`: `8`.
      * `HALO`: `0`.
      * `OFFSET`: `0`.

<br>

### 4. Add an histogram widget for filtering by distance

#### 4. 1. Add a widget for filtering by store id

* Back to the main menu, click on `Lines` layer.
* In the `DATA` view. Activate the checkbox option on `length`.
* Rename them as "Distance".

> This demo can be improved using filter by layer analysis and/or adding (centroids and police stations) AOIs and intersecting them with crimes.

![final](https://cloud.githubusercontent.com/assets/5215798/19149602/eb75be22-8bc2-11e6-9a8b-6ae267fd208b.png)

[Link](https://solutionscdb.carto.com/u/cdbsol-admin/builder/40adbc10-8adc-11e6-9d22-0ee66e2c9693/embed) to the embed map.

<br>