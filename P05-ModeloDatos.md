---
marp: true
theme:  gaia
size: 16:9
class: lead
style: |
    header, footer {
        text-align: center;
        color: #7c7c7c;
        font-size: 12px;
    }
    .logo {            
        text-align: right !important;        
    }
    .cc-img {    
        padding: 0px;
    }
    .cc-text {
        font-size: 14px;
        text-align: left;        
        padding: 0px;
        margin: 0px;
    }
    .grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: min-content 1fr;
        gap: 0px 0px;
        grid-template-areas: ". ." "column column2";
        align-items: center;
    }
    .column {
        grid-area: column;
    }
    .column2 {
        grid-area: column2;
    }
    .footer-img {
        position: absolute;
        bottom: 0px;
        left: 0px;
        background: #fffff0e6;
        padding: 15px;
        border-radius: 0px 20px 0px 0px;
        box-shadow: 10px 0px 10px #000000;
        box-shadow: -5px 5px 15px 15px #00000099;
    }
paginate: true
author: Samuel Mesa <femesagi@unal.edu.co>
title: Modelo de datos SIG
description: Modelo y estructura dde datos SIG
header: Modelo de datos SIG
footer: UNAL . Samuel Mesa . 2021
url: https://aulageo.duckdns.org
progress: true
transition: fade
#inlineSVG: true
#backgroundImage: url('img/fondo01.svg')
#color: whit
---

<!-- _paginate: false -->

# Modelo y estructuras de datos SIG

<div class="grid">
<div class="column">
<p class="logo"><img src="img/logo.png" width="250px"></img></p>
</div>
<div class="column2" style="width:35%;padding-left: 50px !important;">
<p class="cc-img"><img src="img/cc.png"></img></p>
<p class="cc-text">Reconocimiento - Compartir Igual <a href="https://creativecommons.org/licenses/by-sa/4.0/legalcode">CC BY-SA</a></p>
</div>
</div>

<h3>Samuel Mesa</h3>
<small style="text-align:center;">femesagi@unal.edu.co</small>

Noviembre de 2021 
Ingeniería Civil y Agrícola


---

# Contenido

- El modelo de datos
- El modelo raster
- El modelo vectorial
    - El Modelo “Spaghetti”
    - El modelo topológico
- Ventajas y limitantes
- Conversión entre formatos

---
![bg right:39%](https://i.imgur.com/cdsnTB5.png)

##  Representación del mundo real en un SIG

<small>

- El mundo es infinitamente complejo 
- Los contenidos de un SIG representan una vista limitada de la realidad geográfica
- El usuario ve el mundo real a través de un SIG
- Los SIG organizan la información en forma de capas
- Representación de variables discretas y continuas

</small>

---

<!-- _class: none -->

### Estructuras de datos geográficos usados en SIG

| Modelo de datos      | Aplicaciones                                     |
|----------------------|--------------------------------------------------|
| CAD                  | Cartografía                                      |
| Imágenes             | Procesamiento digital de imágenes                |
| Raster/Grid/Malla          | Análisis espacial y modelado                     |
| Topológico vectorial | Operaciones en elementos geométricos vectoriales |
| Redes                | Análisis de redes                                |
| TIN                  | Análisis del terreno                             |
| Objectos             | Operaciones sobre todos los tipos de entidades   |


---

<!-- class: none -->

![bg left contain](https://i.imgur.com/jM7mjTh.png)

## El modelo de datos

En un computador es posible almacenar los  datos espaciales en tres estructuras básicas (QGIS):

- Raster
- Vector
- Malla

---
<!-- backgroundImage: "linear-gradient(to top, #67b8e3, #0288d1)" -->
<!-- color: white -->

![bg right contain](https://i.imgur.com/JrHo8p0.png)

##  El Modelo de Datos Raster

- Los elementos del paisaje son descriptos a través de celdas o píxeles
- Se centra en las propiedades del espacio y no en la representación exacta de los objetos

---

##  El Modelo de Datos Raster

![width:1160px](https://i.imgur.com/kzPRr9M.png)

---
<!--  backgroundImage: none -->
<!--  color: none -->
<!--  class: lead -->

![bg right contain](https://i.imgur.com/5F4d3Kr.png)

## El Modelo de Datos Vector

- Utiliza los conceptos de geometría vectorial mediante coordenadas cartesianas
- Las geometrías primitivas son punto, línea y polígono
- En SIG permite la generación de relaciones topológicas 

---

## El Modelo “Spaghetti”

- Se trata de una estructura de datos más simple, sin topología
- Se almacenan como coordenadas, puntos: como par de coordenadas, líneas como sucesión de puntos, polígonos.
- Elementos cartográficos CAD
Almacenamiento ineficiente en el sistema

--- 

![bg fit](https://i.imgur.com/yuxFuw6.png)

<div class="footer-img">Spaghetti</div>

---

## El Modelo topológico “Arco-nodo”

- Elementos geométricos estructurados usando reglas topológicas: contigüidad, conectividad.
- La topología es la ciencia y matemática de las relaciones
- En los SIG la topología es usada para validar la geometría
- Los elementos fundamentales son el arco, los segmentos (definidos por dos vértices), nodos. 
- Es la estructura más usada en la mayor parte de los SIG


---

![bg fit](https://i.imgur.com/PN8XkOf.png)

<div class="footer-img">Topológico</div>

---

<div class="grid">
<div class="column">

## Elementos puntos

- Un punto es un elemento que no tiene longitud ni área
- Se representa por un par de coordenadas X, Y y los atributos asociados de información

</div>
<div class="column2" style="width:35%;padding-left: 50px !important;">

![width:430px](https://i.imgur.com/nCTvezv.png)


| fid | x  | y | nombre           |
|-----|----|---|------------------|
| 1   | 10 | 1 | Las Auxiliadoras |
| 2   | 35 | 2 | José Mutis       |
| 3   | 30 | 3 | Gaitán           |


</div>
</div>

---


<div class="grid">
<div class="column">

## Elementos línea


- Un elemento línea o arco es aquel que tiene longitud pero no área
- Cada arco es almacenado como una serie de puntos (vértices)

</div>
<div class="column2" style="width:35%;padding-left: 50px !important;">

![width:450px](https://i.imgur.com/ZHOKO99.png)


| fid | nombre   | fnode | tnode | length |
|-----|----------|-------|-------|--------|
| 124 | Río uno  | 1     | 2     | 100    |
| 156 | Río dos  | 7     | 5     | 98     |
| 34  | Río tres | 8     | 4     | 220    |

</div>
</div>

---

## Elementos polígono

- Tiene área y perímetro
- Esta representado por una serie de arcos, cuyo vértices inicial es igual al final
- Tiene un polígono especial denominado polígono universal

---
<!-- backgroundImage: "linear-gradient(to top, #67b8e3, #0288d1)" -->
<!-- color: white -->

## Ventajas y limitantes

<center>
<small>

| Característica            | Vector   | Raster |
|---------------------------|----------|--------|
| Captura de datos          | Lenta  | Rápida      |
| Necesidad de memoria      | Poca  | Grande      |
| Representación            | Muy buena | Regular      |
| Estructura                |  Compleja   | Simple  |
| Exactitud de la Geometría | Muy alta  |  Baja |
| Análisis de redes         | Muy buena  |  Pobre  |
| Superposición             |  Regular | Buena |
| Análisis del terreno      |  Regular | Muy buena  |
| Reproyección              | Eficiente | Ineficiente |

</small>
</center>

---

## Selección de estructuras

- Depende de las intereses y necesidades específicas del trabajo a realizar:
- Vectores: límites de predios, cálculo de áreas, perímetros, análisis de redes
- Raster: zonas de estudio extensas, imágenes de sensores remotos
- Lo ideal es contar con herramientas que permitan trabajar con ambas estructuras

---

## Conversión de vector a raster

El proceso consiste en un "sorteo por casillas" donde todas las celdas cruzadas por una línea toman un valor de uno y van formando la secuencia de celdas.

<center>

![width:980px](https://i.imgur.com/dX4iPCm.png)

</center>

---

![bg fit](https://i.imgur.com/iYiwAhy.png)
