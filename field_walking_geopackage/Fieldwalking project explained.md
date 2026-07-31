# Layers
## Fieldwork recording — fieldwalking_find
Geometry = Point
CRS = 27700 British National Grid
### Symbology
The symbology for this layer is set as categorised based off of find type. This means that each unique artefact type is displayed as its own colour. *Note* if you add a new finds type you will need to reclassify the categorised symbology and push changes back to Qfield.
### Attributes
#### Find Number (integer)
This field is used to record a unique find number. It is possible to add a custom user expression to automatically number this field but I have intentionally left it blank so that the recorder can assign whatever unique number they wish. As a matter of good practise - each find should be given its own unique identifier so that any further specialist info may be related to the spatial layer. If operating a fieldwalking project with more than one Qfield project running - it would be a good idea for the qfield recorders to issue themselves blocks of numbers so that cross over in finds numbering cant occur.
This field is deliberately set to enforced no NULL values. This is to ensure that each record gets a unique finds number - the record wont save without it.
#### Find Type (Text from value relation table ("artefact_types"))
This field is deliberately set to a value relation. This is to ensure that terminology when describing artefact type is maintained for the categorised symbology to work correctly. *NOTE* if further artefact types are required then simply add them to the artefact_type table. This should ensure that the added value is available within the find type dropdown. The layer will need reclassifying in the offline QGIS project to make sure a unique colour is assigned to the point. However, this can be done at the end of a project and is not critical to the fieldwalking.
