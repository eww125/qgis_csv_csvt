# qgis_csv_csvt
How to Specify Data Types of CSV Columns for Use in QGIS

Reference: https://anitagraser.com/2011/03/07/how-to-specify-data-types-of-csv-columns-for-use-in-qgis/

There are two main options to load .csv files into QGIS

“Add delimited text layer” will guess the column data types. Use the “no geometry” option to load CSVs without coordinates.
“Add vector layer” by default interprets all columns as strings.
The following post describes how to change the default behavior of “Add vector layer”.

If you load .csv files through “Add vector layer”, all columns are interpreted as strings. That’s most likely not what you want, but it’s OGR’s default behaviour:

The OGR CSV driver returns all attribute columns with a type of string if no field type information file (with .csvt extension) is available.

Let’s create a .csvt file then!

The .csvt file has to have the same name as the .csv file it describes. (The same concept is used for Shapefiles.) It enables definition of the following data types: Integer, Real, String, Date (YYYY-MM-DD), Time (HH:MM:SS+nn) and DateTime (YYYY-MM-DD HH:MM:SS+nn).

A .csvt file contains only one line and the types for each column have to be quoted and comma separated, e.g.

"Integer","Real","String"

You can even specify width and precision of each column, e.g.

"Integer(6)","Real(5.5)","String(22)"

Read more at: www.gdal.org/ogr/drv_csv.html

