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

| Código NDVI |
| ----------- |
| //Imagen landsat (color verdadero)
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
Map.addLayer(with_ndvi.median().clip(Tempisque), {bands: "nd", min: 0, max: 1, palette: ndviPalette}, "NDVI"); |
