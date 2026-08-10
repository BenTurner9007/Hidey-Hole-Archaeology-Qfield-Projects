---
title: Fieldwalking Methodology
---
# Project Features
So this fieldwalking project has been setup with a few unique features worth discussing here.
## Horizontal accuracy indicator within fieldwalking finds layer
This is a key feature of the project setup and has been included for several reasons. In commercial field archaeology it is standard practise that each find spot is geolocated using survey grade GPS equipment - usually to within a few centimeter accuracy. Most field units will be setup to use this sort of equipment, but volunteer/community groups may not have access to this level of equipment, and will likely not have the skills required to use survey grade GPS equipment.
As a result of this, many community groups may result to older techniques of logging finds in transects and stints where finds are located within a linear corridor block. Although this is useful, with technology (free!) available to use today we can start to do one better. With Qfield we can use our internal phone gps to locate our find spots - with one very important caveat. Phone GPS accuracy is at best around 1m (ish). The Qfield project has been setup to record the internal phone gps accuracy within the haccuracy field for each point taken. This is then buffered out to produce a radius around each point. This gives us an indication of the likely radius in which each findspot sits. Although not as good as survey grade GPS accuracy - this infomation gives some useful insight when conducting spatial analysis on each findspot.

## Paradata Tables

Within the project I have also included several Paradata tables. These are non-spatial layers but contain fields that can be used to record valuable paradata

### What is Paradata?

Paradata in the sense of the fieldwalking project is essentially data on how the data was collected, which can be extremeley useful in how we interpret our findings. For example was a particular day wet or bright sunshine? These bits of data matter and can be really useful in the long term.



# Layers
## Fieldwork recording — fieldwalking_find
This is a point geometry layer used to pinpoint a find recorded during fieldwalking.
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

## areas_covered (polygon)
This layer can be used to visually depict the area covered by fieldwalking. This is especially useful when analysing finds distribution to note any gaps in the area surveyed.
### Attributes
### *Date (date/time)*
Hidden from the user and automatically populated using a now() default user expression. This allows for spatial analysis of coverage areas over time.

## areas_unavailable (polygon)
this layer can be used to visualise areas that are not availbale for fieldwalking. Useful again in spatial distribution analysis and as a record of which areas still need covering.
### *Date (date/time)*
Hidden from the user and automatically populated using a now() default user expression. This allows for spatial analysis of coverage areas over time.
### *Description*
Free text description of the particular constraint (for example "Area flooded during survey" etc) This attribute is displayed as a label for ease of viewing.
