---
layout: default
---

# Key Project Features
So this fieldwalking project has been setup with a few unique features which aim to address key metadata and paradata data collection that is often missed.

## Horizontal accuracy indicator within fieldwalking finds layer
This is a key feature of the project setup, included for several reasons.

In commercial field archaeology, it's standard practice to geolocate each find spot using survey-grade GPS equipment which is typically accurate to within a few centimetres. Most professional field units have access to this equipment, but volunteer and community groups often don't, and may also lack the training needed to operate it.

As a result, many community groups fall back on older techniques: logging finds within transects or stints, where finds are recorded as belonging to a linear corridor rather than a precise point. While this approach has its uses, the technology now freely available to us lets go one better.

QField allows us to use a phone's internal GPS to record find spot locations directly — with one important caveat: phone GPS accuracy is, at best, around 1 metre. To account for this, the QField project supplied in the GeoPackage records each point's GPS accuracy in the haccuracy field. This value is then used to generate a buffer radius around each point, giving a visual indication of the likely area in which the true find spot sits.

While this doesn't match survey-grade GPS precision, it provides genuinely useful information when carrying out spatial analysis on find spot data.

The default user expression in the `haccuracy` field is
> @position_horizontal_accuracy

## Non-Spatial Layers

### Paradata Tables

Within the project I have included several Paradata tables. These are non-spatial layers but contain fields that can be used to record valuable paradata.

Paradata in the sense of the fieldwalking project is essentially data on how the data was collected, which can be extremeley useful in how we interpret our findings. For example was a particular day wet or bright sunshine? These bits of data matter and can be really useful in the long term.

#### `field_observations`

This paradata table contains four fields and is used to record general site conditions on a given day. Capturing this kind of contextual data is essential for understanding conditions that may have influenced or skewed the collected data.

Table structure: 

| Field | Description |
| :---        |    ---   | 
| `Date` | Used to record the date of the observation. This is deliberately not auto-filled to allow for retrospective data entry as the date can be picked from a calendar view. |
| `Weather` | To record the weather conditions during the survey |
| `Ground Conditions` | To record the condition of the ground when survey was undertaken. (Dry, waterlogged etc) |
| `General Description` | To record any general information not already covered. |

The fields in this table are not linked to any of the spatial layers via value relations. This means that this table is not mandatory to the function of the fieldwalking project.

#### `field_operatives`

The field operatives table is a non-spatial paradata table used to record the names of field operatives during the survey. The aim of this table is two-fold:
1. to record the names of the operatives so that spatial patterning of find type by finder may be produced. This is useful paradata to collect as an operative who is skilled at one type of artefact identification may miss other types of artefacts. If this data is collected within the findspot data then it can be interogated more closely 
2. to provide a value relation table within the fieldwalking findspot spatial layer from which to record the finder of each object.

the table is relatively simple by design but can be adapted if you wish to record further details on field operatives - for example you could add further fields to record experience levels if necessary

Table structure: 

| Field | Description |
| :---        |    ---   | 
| `Name` | Used to record the full name of the operative |

### Value Relation Tables

As described above, the `field_operatives` table falls under paradata table and value relation table categories. The only non-spatial table within the project which is purely a value relation table is the `artefact_types` table.

#### `artefact_types`

As a default I have pre-populated this table with several common artefact types that you will come across in the UK such as lithic, pottery etc. The purpose of this table is to create a value relation in the `Fieldwork recording — fieldwalking_find` layer so that a consistent terminology can be used. This consistency will aid in processing and visualisation of the spatial data. For example if "Pot", "Pottery", "pot" were all used in the artefact type field, then when the data is categorised QGIS would create three separate categories for each version of artefact type. Please see the Symbology section in the `Fieldwork recording — fieldwalking_find` for an important caveat when adding new artefact types into this table.

Table structure:

| Field | Description |
| :---        |    ---   | 
| `Artefact Type` | Used to record the type of artefact recorded |


# Spatial Layers
## `Fieldwork recording — fieldwalking_find` (point layer)
This is a point geometry layer used to pinpoint a find recorded during fieldwalking.
### Symbology
The symbology for this layer is set as categorised based off of the Find Type value which is controlled by a value relation table (discussed above). This means that each unique artefact type is displayed as its own colour. *Note* if you add a new finds type you will need to reclassify the categorised symbology and push changes back to Qfield.
### Attributes

| Field | Description |
| :---        |    ---   | 
|   `Find Number` (integer)    | This field is used to record a unique find number. It is possible to add a custom user expression to automatically number this field but I have intentionally left it blank so that the recorder can assign whatever unique number they wish. As a matter of good practise - each find should be given its own unique identifier so that any further specialist info may be related to the spatial layer. If operating a fieldwalking project with more than one Qfield project running - it would be a good idea for the qfield recorders to issue themselves blocks of numbers so that cross over in finds numbering cant occur. This field is deliberately set to enforced no NULL values. This is to ensure that each record gets a unique finds number - the record wont save without it.   | 
|    `Find Type` (Text from value relation table ("artefact_types")    |  This field is deliberately set to a value relation. This is to ensure that terminology when describing artefact type is maintained for the categorised symbology to work correctly. *NOTE* if further artefact types are required then simply add them to the artefact_type table. This should ensure that the added value is available within the find type dropdown. The layer will need reclassifying in the offline QGIS project to make sure a unique colour is assigned to the point. However, this can be done at the end of a project and is not critical to the fieldwalking.  | 
|   `Finder Name` (text from value relation table (field_operatives)    |  This is a controlled drop down menu populated by entries into the field_operatives value relation table. Recording finder name can be a useful piece of paradata to understand the types of artefacts certain people are finding. For example you may be able to scrutinise this data to find out that a particular person is only finding pottery and no lithics. You can use this information to target further artefact identification training.  | 
|    `Photo` (text)    | This field is set so that Qfield can open its camera function which allows a photograph to be attached to the recorded point. This can be a really useful documentation tool.   | 
|    `Date` (date/time format)    | This attribute is hidden from the user but has a user expression "now()" to automatically record the date/time that a point was taken. It was decidded to hide this field from the user to avoid cluttering the screen as it can be automatically calculated from Qfield   | 
|     `haccuracy` (decimal double)   | This field is set with a default user expression (@position_horizontal_accuracy) to automatically record the horizontal accuracy of the recorded point. This value is then tied to a buffer in the Fieldwork recording — fieldwalking_find to visually represent the horizontal accuracy of each recorded point to indicate the radium in which this point may fall. This is a hidden field that does not require user input.   | 
|  `easting`, `northing`, `height` (decimal double)  |  Automatically populates easting, northings and height from the phone device and are controlled by default user expressions x(@geometry), y(@geometry) and z(@geometry). These fields are deliberately hidden from the user as they are generated fields and require no user input.  | 

## `areas_covered` (polygon layer)
This layer can be used to visually depict the area covered by fieldwalking. This is especially useful when analysing finds distribution to note any gaps in the area surveyed.
### Attributes

| Field | Description |
| :---        |    ---   | 
| `Date` (date/time) | Hidden from the user and automatically populated using a now() default user expression. This allows for spatial analysis of coverage areas over time. |

## `areas_unavailable` (polygon layer)
This layer can be used to visualise areas that are not availbale for fieldwalking. Useful again in spatial distribution analysis and as a record of which areas still need covering.

| Field | Description |
| :---        |    ---   | 
| `Date` (date/time) | Hidden from the user and automatically populated using a now() default user expression. This allows for spatial analysis of coverage areas over time. |
|`Description` |Free text description of the particular constraint (for example "Area flooded during survey" etc) This attribute is displayed as a label for ease of viewing. |
