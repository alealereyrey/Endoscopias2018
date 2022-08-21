# Endoscopy quality indicators in a terciary referral hospita

To evaluate the performance of a GI endoscopy department there are several indicators that reflect the quality of the processes and procedures of healthcare delivery.  Monitoring and periodically analyzing the data allows us to estimate its current state and to develop measures regarding its constant improvement.

> **The main objective of this work is to measure the polyp detection rate of a digestive endoscopy service in a university hospital in the Autonomous City of Buenos Aires.**

The secondary objectives are:
- To measure the number and type of studies carried out at each site.
- To measure the number of diagnostic and therapeutic colonoscopies in colorectal screening studies, their distribution by site and by endoscopist.
- To investigate whether there is an association between the number of procedures performed and the number of polyps detected.
- To investigate whether there is an association between the number of procedures performed and the polyp detection rate.
- To calculate the studies completion rate
- To Assess the quality of bowel cleansing.
- To investigate if there is an association between the quality of the preparation and the type of laxative used.


A cross-sectional study was carried out. Statystical analysis was performed with RStudio 1.1463.

## **Libraries used**
```
library(tidyverse)
library(dplyr)
library(gapminder)
library(readxl)
library(RUMBA)
library(sf)
library(osmdata)
library(ggmap)
library(janitor)
```

## **Polyp detection rate by endoscopist**

<p align="center">
<img src= "https://user-images.githubusercontent.com/60556106/185814660-1e57bc0e-702e-4ae0-b82a-06bd381c78d3.PNG" width="80%">

## **Polypectomies by number of studies & endoscopyst polyp detection rate by number of studies**

<img align="left" img src= "https://user-images.githubusercontent.com/60556106/185814876-060fac8b-fae0-4b7f-9aff-a1fb71e492ad.PNG" width="45%"> <img src= "https://user-images.githubusercontent.com/60556106/185814879-0b170eda-65c0-4dd1-9f85-2954154a7d5a.PNG" width="45%">
</pre>

## **Confirming there is correlation for polypectomies but not for polyp detection rate**
```
cor(tabla_deteccion$Estudios, tabla_deteccion$Polipectomias)
## [1] 0.9853041
cor(tabla_deteccion$Estudios, tabla_deteccion$Tasa)
## [1] -0.1780102
```

## **Performing and plotting a linear regression between polypectomies and number of studies**

```
regresion_lineal_simple <-  lm(Polipectomias ~ Estudios,
               tabla_deteccion)

regresion_lineal_simple

Call:
lm(formula = Polipectomias ~ Estudios, data = tabla_deteccion) 

Coefficients:
(Intercept)     Estudios  
    9.9600       0.4196
```
<p align="center">
<img src= "https://user-images.githubusercontent.com/60556106/185815852-ac35a9fc-59ca-4ce6-a35f-451caea9b1e8.PNG" width="80%">

## **Colonoscopy completition rates**
  
<p align="center">
<img src= "https://user-images.githubusercontent.com/60556106/185815951-faa899e4-3210-43ef-81d4-ada199131e73.PNG" width="70%">

## **Assessment of bowel cleansing by laxative**

<p align="center">
<img src= "https://user-images.githubusercontent.com/60556106/185816021-34820941-f8df-4e10-84a2-b23d01fda4b3.PNG" width="80%">

## **Conclusions**

We found that the polyp detection rate in our hospital was significantly over the minimum standard recommendations. As expected in good quality colonoscopies, there is a linear association between the number of polypectomies and the number of studies performed. There was no correlation observed between the number of studies and the polyp detection rate. 
  
</pre>

The proportion of studies completed (called cecal intubation rate) and the quality of bowel cleansing were in line with the standard recommendations for screening colonoscopies. 

