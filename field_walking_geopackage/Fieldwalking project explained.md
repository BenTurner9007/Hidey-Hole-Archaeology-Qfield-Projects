# Layers
## Fieldwork recording — fieldwalking_find
Geometry = Point
CRS = 27700 British National Grid
### Symbology
The symbology for this layer is set as categorised based off of the Find Type value which is controlled by a value relation table (discussed below). This means that each unique artefact type is displayed as its own colour. *Note* if you add a new finds type you will need to reclassify the categorised symbology and push changes back to Qfield.
### Attributes
### *Find Number (integer)*
This field is used to record a unique find number. It is possible to add a custom user expression to automatically number this field but I have intentionally left it blank so that the recorder can assign whatever unique number they wish. As a matter of good practise - each find should be given its own unique identifier so that any further specialist info may be related to the spatial layer. If operating a fieldwalking project with more than one Qfield project running - it would be a good idea for the qfield recorders to issue themselves blocks of numbers so that cross over in finds numbering cant occur.
This field is deliberately set to enforced no NULL values. This is to ensure that each record gets a unique finds number - the record wont save without it.
### *Find Type (Text from value relation table ("artefact_types"))*
This field is deliberately set to a value relation. This is to ensure that terminology when describing artefact type is maintained for the categorised symbology to work correctly. *NOTE* if further artefact types are required then simply add them to the artefact_type table. This should ensure that the added value is available within the find type dropdown. The layer will need reclassifying in the offline QGIS project to make sure a unique colour is assigned to the point. However, this can be done at the end of a project and is not critical to the fieldwalking.
### *Finder Name* (text from value relation table (field_operatives))
This is a controlled drop down menu populated by entries into the field_operatives value relation table. Recording finder name can be a useful piece of paradata to understand the types of artefacts certain people are finding. For example you may be able to scrutinise this data to find out that a particular person is only finding pottery and no lithics. You can use this information to target further artefact identification training.
### *Photo* (text)
This field is set so that Qfield can open its camera function which allows a photograph to be attached to the recorded point. This can be a really useful documentation tool.
### *Date* (date/time format)
This attribute is hidden from the user but has a user expression "now()" to automatically record the date/time that a point was taken. It was decidded to hide this field from the user to avoid cluttering the screen as it can be automatically calculated from Qfield
### *haccuracy* (decimal double)
This field is set with a default user expression (@position_horizontal_accuracy) to automatically record the horizontal accuracy of the recorded point. This value is then tied to a buffer in the Fieldwork recording — fieldwalking_find to visually represent the horizontal accuracy of each recorded point to indicate the radium in which this point may fall. This is a hidden field that does not require user input.
### *easting, northing, height* (decimal double)
Automatically populates easting, northings and height from the phone device and are controlled by default user expressions x(@geometry), y(@geometery) and z(@geometry). These fields are deliberately hidden from the user as they are generated fields and require no user input.

