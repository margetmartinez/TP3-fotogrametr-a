TP3 Fotogrametría, Códigos de los índices
Elaborado por Daniela Amador, B50415 y Marget Martínez, B74477

NDVI:

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



EVI:

//Imagen landsat (color verdadero)
var rgb_vis = {min: 0, max: 0.3, bands: ['B4', 'B3', 'B2']};

//Filtros
var filtered = L8.filterDate('2019-04-01', '2019-04-15')
  .filterBounds(roi);
var image = ee.Image(filtered.first());
var evi = addEVI (image);

//Función EVI
function addEVI (Image){
var evi = image.expression(
'2.5 * ((NIR - RED) / (NIR + 6 * RED - 7.5 * BLUE + 1))', {
'NIR': image.select('B5'),
'RED': image.select('B4'),
'BLUE': image.select('B2')
}); 
return image.addBands (evi);
}

//Visualizar EVI
var eviPalette = ["FFFFFF", "CE7E45", "DF923D", "F1B555", "FCD163", "99B718",
                  "74A901", "66A000", "529400", "3E8601", "207401", "056201",
                  "004C00", "023B01", "012E01", "011D01", "011301"];

Map.addLayer(image, rgb_vis, "RGB");
Map.addLayer(evi.clip(Tempisque), {bands: "constant", min: -1, max: 1, palette: eviPalette}, 'EVI');




NDWI:

//Imagen landsat (color verdadero)
var rgb_vis = {min: 0, max: 0.3, bands: ['B4', 'B3', 'B2']};

//Filtros
var filtered = L8.filterDate('2019-04-01', '2019-04-15')
  .filterBounds(roi);
var image = ee.Image(filtered.first());

//Función NDWI
var ndwi = image.normalizedDifference(['B5', 'B6']);

//Visualizar NDWI
var waterPalette = ['white', 'blue'];
Map.addLayer(image, rgb_vis, "RGB");
Map.addLayer(ndwi.clip(Tempisque), {bands: "nd", min: -0.5, max: 1, palette: waterPalette}, 'NDWI');



NDWBI: 

//Imagen landsat (color verdadero)
var rgb_vis = {min: 0, max: 0.3, bands: ['B4', 'B3', 'B2']};

//Filtros
var filtered = L8.filterDate('2019-04-01', '2019-04-15')
.filterBounds(roi);
var image = ee.Image(filtered.first());

//Función NDWBI
var ndwbi = image.normalizedDifference(['B3', 'B5']);

//Visualizar NDWBI
var waterPalette = ['white', 'blue'];
Map.addLayer(image, rgb_vis, "RGB");
Map.addLayer(ndwbi.clip(Tempisque), {min: -1, max: 0.5, palette: waterPalette}, 'NDWBI');



NDBI: 

//Imagen landsat (color verdadero)
var rgb_vis = {min: 0, max: 0.3, bands: ['B4', 'B3', 'B2']};

//Filtros
var filtered = L8.filterDate('2019-04-01', '2019-04-15')
  .filterBounds(roi);
var image = ee.Image(filtered.first());

//Función NDBI
var waterPalette = ['white', 'blue'];
var ndbi = image.normalizedDifference(['B6', 'B5']);
var barePalette = waterPalette.slice().reverse();

//Visualizar NDBI
var barePalette = ['white', 'blue'];
Map.addLayer(image, rgb_vis, "RGB");
Map.addLayer(ndbi.clip(Tempisque), {min: -1, max: 0.5, palette: barePalette}, 'NDBI');




BAI: 

//Imagen landsat
var rgb_vis = {min: 0, max: 0.3, bands: ['B4', 'B3', 'B2']};

//Filtros e imagen color verdadero
var burnImage = ee.Image(L8
.filterBounds(ee.Geometry.Point(-85.40, 10.39))
.filterDate('2019-04-01', '2019-04-15')
.sort('CLOUD_COVER')
.first());

//Visualización
Map.addLayer(burnImage, rgb_vis, 'burn image');

//Función BAI
var bai = burnImage.expression(
'1.0 / ((0.1 - RED)**2 + (0.06 - NIR)**2)', {
'NIR': burnImage.select('B5'),
'RED': burnImage.select('B4'),
});

//Visualización del BAI
var burnPalette = ['green', 'blue', 'yellow', 'red'];
Map.addLayer(bai.clip(Tempisque), {min: 0, max: 400, palette: burnPalette}, 'BAI');
