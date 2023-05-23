# remote sensing

# MSI

#### vegetation indices:
* LAI estimation
	→ WDVI (Weighted Difference VI)
* LCC estimation
	→ TCARI/OSAVI, 
	→  CVI [(R870/R550)/(R550/R670)]
* CCC estimation = LCC * LAI
	→ CI rededge
	→ CI green

#### parameters for crop monitoring:
* LAI – Leaf Area Index [m²/m²]
* LCC Leaf Chlorophyll Content [g/m²]
* CCC Canopy chlorophyll content [g/m²]

## classification

### segmentation

useful algorythms for segmation:
* Watershed algorithm
* Region growing algorithm

### feature extraction

feature categories
* Radiometric 
* temporal
* object features 

### unsupervised classification

* k-means
* isodata

### supervised classification

![supervised classification algorythms](pics/supervised_class.png)

# SAR

Radarrückstreuung wird beinflusst durch:
* Bodenparameter
    * geometrische Eigenschaften
        * Oberflächenrauigkeit
        * Topographie
        * Objektgeometrie
        * Objektaisrichtung
    * dielektrische Eigenschaften (Wassergehalt)
* Sensorparameter
    * Wellenlänge & Frequenz
    * Polarisation
    * Zellgröße
    * Sensorgeometrie (Einfallswinkel, etc)
