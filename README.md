# TP3 Fotogrametría
## Elaborado por Daniela Amador, B50415 y Marget Martínez, B74477

**Área de estudio:** Región Chorotega

**Cuenca hidrográfica:** Tempisque

![cuenca tempisque](https://github.com/margetmartinez/TP3-fotogrametr-a/blob/main/tem.PNG)

###### Figura 1. Cuenca del río Tempisque

## Índices de vegetación

### **NDVI**: Índice Normalizado de Vegetación

![NDVI](https://github.com/margetmartinez/TP3-fotogrametr-a/blob/main/ndvi.PNG)

###### Figura 2. NDVI

**Código NDVI** 

//Imagen landsat (color verdadero)

var rgb_vis = {min: 0, max: 0.3, bands: ['B4', 'B3', 'B2']};

//Función NDVI

function addNDVI (image){
  var ndvi = image.normalizedDifference (["B5", "B4"]);
  return image.addBands (ndvi);
}

//Filtros

var filtered = L8.filterDate("2018-04-01", "2019-04-15")
  .filterBounds(roi);
  var with_ndvi = filtered.map (addNDVI);
  var image = ee.Image(filtered.first());
  var ndvi = addNDVI (image);
  
//Visualizar el NDVI 

var ndviPalette = ["FFFFFF", "CE7E45", "DF923D", "F1B555", "FCD163", "99B718",
                  "74A901", "66A000", "529400", "3E8601", "207401", "056201",
                  "004C00", "023B01", "012E01", "011D01", "011301"];

Map.addLayer(filtered.median(), rgb_vis, "RGB");

Map.addLayer(with_ndvi.median().clip(Tempisque), {bands: "nd", min: 0, max: 1, palette: ndviPalette}, "NDVI"); 

**Explicación de NDVI con respecto a la cuenca**

El índice NDVI (Índice Normalizado de Vegetación), es uno de los índices que más se utiliza en el campo de la teledetección. En la actualidad es utilizado en el campo de la agricultura de precisión. Este índice es un indicador simple de biomasa fotosintética activa o sea, es el cálculo de qué tan saludable está la vegetación. Este compara la cantidad de luz roja visible absorbida (B4) y la luz infrarroja cercana reflejada (B5). Esto porque el pigmento de la clorofila en una planta sana absorbe la mayor cantidad de la luz roja visible y la estructura celular de una planta refleja la mayor parte de la luz infrarroja cercana. Lo que indica que una alta actividad fotosintética, que normalmente se asocia con vegetación densa, va a tener menor reflectancia en la banda roja y mayor reflectancia en el infrarrojo cercano (Toribio, 2019). 

Para la cuenca del Tempisque en las zonas verde oscuro los valores de las bandas se encuentran entre 0,34 a 1 lo que indica una vegetación de medianamente sana a muy sana. Para las zonas amarillas y rojas los valores se encuentran entre 0 a 0.33 lo que indica una vegetación muerta o enferma. En esta cuenca, los colores amarillentos coinciden con suelos descubiertos o cultivos y las más rojizas coinciden con los centros urbanos como por ejemplo el centro de Liberia. También, estas zonas rojizas coinciden con cuerpos de agua. 

### **EVI**: Índice de Vegetación Mejorado

![EVI]()

###### Figura 3. EVI

**Código EVI**
