# Demo ogr2ogr geospatial operations

ogr2ogr is the swiss army knife in the world of geospatial analysis and data processing. It's main purpose is to convert geospatial data to different dataformats without the need of Geographic Information Systems such as QGIS or ArcPro. It also allows us to do various operations during this process. We can reproject our data; clip it; make a sub selection of data or attributes; intersect it; change column names and much more.

Repository contains used in commands below. Checkout <link> for a more in depth walk throogh.

#### Convert data from ESRI Shapefile to Geopackage

`ogr2ogr -f 'GPKG' project_extent.gpkg project_extent_wgs.shp`

- `ogr2ogr` basically tells the computer: get ready, I want to use ogr2ogr.
- `-f 'GPKG'` specify the format to which we want to convert our shapefile.
- `project_extent.gpkg` is the output file.
- `project_extent_wgs.shp` is our input file.

#### Reproject data

`ogr2ogr -f 'GPKG' project_extent_rdnew.gpkg project_extent_wgs.shp -t_srs EPSG:28992`

#### Clip data using another layer

`ogr2ogr -f 'GPKG' clipped/clip_buildings.gpkg buildings.gpkg -clipsrc project_extent_rdnew.gpkg -progress`

- `ogr2ogr` tell computer you are about to use ogr2ogr.
- `-f` 'GPKG' specify the output format.
- `clipped/clip_buildings.gpkg` specify output file and destination. In our case we wish to save result in a subfolder `clipped/`.
- `buildings.gpkg` is our input file.
- `-clipsrc` the clip operations we wish to apply using another file.
- `project_extent_rdnew.gpkg` the file containing the clip features. In our case our reprojected neighborhood.
- `-progress` and show us a progress bar.
