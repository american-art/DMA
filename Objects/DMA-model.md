# Dallas Museum of Art - LOD - UPDATED.csv

## Add Column

## Add Node/Literal
#### Literal Node: `http://vocab.getty.edu/aat/300179869`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300026687`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300080091`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300404670`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300266036`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`

#### Literal Node: `http://vocab.getty.edu/aat/300404621`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `true`


## PyTransforms
#### _ObjectURI_
From column: _ObjectID_
``` python
return "object/"+getValue("ObjectID")
```

#### _ClassificationAssignmentURI_
From column: _ObjectURI_
``` python
return getValue("ObjectURI")+"/classification_assignment"
```

#### _Classification_
From column: _ClassificationAssignmentURI_
``` python
return UM.uri_from_fields("thesauri/classification/",getValue("ClassificationObject"))
```

#### _CreditURI_
From column: _Copyright_
``` python
if getValue("CreditLine"):
    return getValue("ObjectURI")+"/credit"
else:
    return ""
```

#### _CopyrightURI_
From column: _ClassificationObject_
``` python
return getValue("ObjectURI")+"/copyright"
```

#### _ProductionURI_
From column: _DataDateStamp_
``` python
if getValue("DateBegin")!="0":
    return getValue("ObjectURI")+"/production"
else:
    return ""
```

#### _DateURI_
From column: _ProductionURI_
``` python
if getValue("ProductionURI"):
    return getValue("ProductionURI")+"/date"
else:
    return ""
```

#### _ObjectNumberLabel_
From column: _ObjectNumber_
``` python
return getValue("ObjectNumber")
```

#### _ObjectNumberURI_
From column: _ObjectOwned_
``` python
return getValue("ObjectURI")+"/object_number"
```

#### _MaterialURI_
From column: _ResourceURL_
``` python
return UM.uri_from_fields("thesauri/material/",getValue("Medium"))
```

#### _DescriptionURI_
From column: _ObjectNumberLabel_
``` python
if getValue("PublicDescription"):
    return getValue("ObjectURI")+"/description"
else:
    return ""
```

#### _DimensionURI_
From column: _Medium_
``` python
if getValue("DimensionsDisplayText"):
    return getValue("ObjectURI")+"/dimension"
else:
    return ""
```

#### _Role_
From column: _Role_
``` python
return getValue("Role")
```

#### _TitleURI_
From column: _Role_
``` python
return UM.uri_from_fields("thesauri/title/",getValue("Title"))
```

#### _TitleLabel_
From column: _Title_
``` python
return getValue("Title")
```

#### _ImageURLClean_
From column: _ImageURL_
``` python
if getValue("ImageURL"):
    return getValue("ImageURL")
else:
    return ""
```

#### _ObjectUrlURI_
From column: _PublicDescription_
``` python
if getValue("ResourceURL"):
    return getValue("ResourceURL")
else:
    return ""
```

#### _ArtistURI_
From column: _Role_
``` python
if getValue("Role") in ['Artist','Author','Engraver'] and getValue("DisplayName"):
    return "constituent/"+SM.fingerprint_string(getValue(("DisplayName")))
else:
    return ""
```

#### _SubjectURI_
From column: _Role_
``` python
if getValue("Role")=="Depicted individual":
    return "constituent/"+SM.fingerprint_string(getValue("DisplayName"))
else:
    return ""
```

#### _OwnerURI_
From column: _Image Display Order_
``` python
return "http://data.americanartcollaborative.org/dma"
```

#### _OwnerLabel_
From column: _OwnerURI_
``` python
return "Dallas Museum of Art"
```

#### _Medium_clean_
From column: _Medium_
``` python
return getValue("Medium").strip()
```

#### _ObjectIdLabel_
From column: _ObjectID_
``` python
return getValue("ObjectID")
```

#### _ObjectIdURI_
From column: _ObjectIdLabel_
``` python
return getValue("ObjectURI")+"/pref_id"
```

#### _DateBeginValid_
From column: _DateBegin_
``` python
if getValue("DateBegin")!="0":
    return getValue("DateBegin") + "-01-01"
else:
    ""
```

#### _DateEndValid_
From column: _DateEnd_
``` python
if getValue("DateEnd")!="0":
    return getValue("DateBegin") + "-01-01"
else:
    ""
```

#### _DateLabel_
From column: _Dated_
``` python
if getValue("DateBeginValid") or getValue("DateEndValid"):
    return getValue("DateBeginValid") + " to " + getValue("DateEndValid")
else:
    ""
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _ArtistURI_ | `uri` | `crm:E39_Actor1`|
| _Classification_ | `uri` | `crm:E55_Type1`|
| _ClassificationAssignmentURI_ | `uri` | `crm:E17_Type_Assignment1`|
| _ClassificationObject_ | `rdfs:label` | `crm:E55_Type1`|
| _Copyright_ | `crm:P3_has_note` | `crm:E30_Right1`|
| _CopyrightURI_ | `uri` | `crm:E30_Right1`|
| _CreditLine_ | `rdf:value` | `crm:E33_Linguistic_Object1`|
| _CreditURI_ | `uri` | `crm:E33_Linguistic_Object1`|
| _DateBeginValid_ | `crm:P82a_begin_of_the_begin` | `crm:E52_Time-Span1`|
| _DateEndValid_ | `crm:P82b_end_of_the_end` | `crm:E52_Time-Span1`|
| _DateLabel_ | `rdfs:label` | `crm:E52_Time-Span1`|
| _DateURI_ | `uri` | `crm:E52_Time-Span1`|
| _DescriptionURI_ | `uri` | `crm:E33_Linguistic_Object2`|
| _DimensionURI_ | `uri` | `crm:E33_Linguistic_Object3`|
| _DimensionsDisplayText_ | `rdf:value` | `crm:E33_Linguistic_Object3`|
| _ImageURLClean_ | `uri` | `crm:E38_Image1`|
| _MaterialURI_ | `uri` | `crm:E57_Material1`|
| _Medium_clean_ | `skos:prefLabel` | `crm:E57_Material1`|
| _ObjectID_ | `rdf:value` | `crm:E42_Identifier2`|
| _ObjectIdLabel_ | `rdfs:label` | `crm:E42_Identifier2`|
| _ObjectIdURI_ | `uri` | `crm:E42_Identifier2`|
| _ObjectNumber_ | `rdf:value` | `crm:E42_Identifier1`|
| _ObjectNumberURI_ | `uri` | `crm:E42_Identifier1`|
| _ObjectURI_ | `uri` | `crm:E22_Man-Made_Object1`|
| _ObjectUrlURI_ | `uri` | `foaf:Document1`|
| _OwnerLabel_ | `rdfs:label` | `crm:E40_Legal_Body1`|
| _OwnerURI_ | `uri` | `crm:E40_Legal_Body1`|
| _ProductionURI_ | `uri` | `crm:E12_Production1`|
| _PublicDescription_ | `rdf:value` | `crm:E33_Linguistic_Object2`|
| _ResourceURL_ | `rdfs:label` | `foaf:Document1`|
| _SubjectURI_ | `uri` | `crm:E39_Actor2`|
| _Title_ | `rdf:value` | `crm:E35_Title1`|
| _TitleLabel_ | `rdfs:label` | `crm:E22_Man-Made_Object1`|
| _TitleURI_ | `uri` | `crm:E35_Title1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `crm:E12_Production1` | `crm:P14_carried_out_by` | `crm:E39_Actor1`|
| `crm:E12_Production1` | `crm:P4_has_time-span` | `crm:E52_Time-Span1`|
| `crm:E17_Type_Assignment1` | `crm:P42_assigned` | `crm:E55_Type1`|
| `crm:E17_Type_Assignment1` | `crm:P21_had_general_purpose` | `http://vocab.getty.edu/aat/300179869`|
| `crm:E22_Man-Made_Object1` | `crm:P108i_was_produced_by` | `crm:E12_Production1`|
| `crm:E22_Man-Made_Object1` | `crm:P41i_was_classified_by` | `crm:E17_Type_Assignment1`|
| `crm:E22_Man-Made_Object1` | `crm:P104_is_subject_to` | `crm:E30_Right1`|
| `crm:E22_Man-Made_Object1` | `crm:P67i_is_referred_to_by` | `crm:E33_Linguistic_Object1`|
| `crm:E22_Man-Made_Object1` | `crm:P129i_is_subject_of` | `crm:E33_Linguistic_Object2`|
| `crm:E22_Man-Made_Object1` | `crm:P67i_is_referred_to_by` | `crm:E33_Linguistic_Object3`|
| `crm:E22_Man-Made_Object1` | `crm:P102_has_title` | `crm:E35_Title1`|
| `crm:E22_Man-Made_Object1` | `crm:P138i_has_representation` | `crm:E38_Image1`|
| `crm:E22_Man-Made_Object1` | `crm:P62_depicts` | `crm:E39_Actor2`|
| `crm:E22_Man-Made_Object1` | `crm:P52_has_current_owner` | `crm:E40_Legal_Body1`|
| `crm:E22_Man-Made_Object1` | `crm:P1_is_identified_by` | `crm:E42_Identifier1`|
| `crm:E22_Man-Made_Object1` | `crm:P1_is_identified_by` | `crm:E42_Identifier2`|
| `crm:E22_Man-Made_Object1` | `crm:P45_consists_of` | `crm:E57_Material1`|
| `crm:E22_Man-Made_Object1` | `foaf:homepage` | `foaf:Document1`|
| `crm:E22_Man-Made_Object1` | `crm:P2_has_type` | `crm:E55_Type1`|
| `crm:E33_Linguistic_Object1` | `crm:P2_has_type` | `http://vocab.getty.edu/aat/300026687`|
| `crm:E33_Linguistic_Object2` | `crm:P2_has_type` | `http://vocab.getty.edu/aat/300404670`|
| `crm:E33_Linguistic_Object2` | `crm:P2_has_type` | `http://vocab.getty.edu/aat/300080091`|
| `crm:E33_Linguistic_Object3` | `crm:P2_has_type` | `http://vocab.getty.edu/aat/300266036`|
| `crm:E35_Title1` | `crm:P2_has_type` | `http://vocab.getty.edu/aat/300404670`|
| `crm:E42_Identifier1` | `crm:P2_has_type` | `http://vocab.getty.edu/aat/300404621`|
| `crm:E42_Identifier2` | `crm:P2_has_type` | `http://vocab.getty.edu/aat/300404670`|
