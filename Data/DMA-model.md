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
return getValue("ObjectURI")+"/credit"
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
return getValue("ProductionURI")+"/date"
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


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _Classification_ | `uri` | `crm:E55_Type1`|
| _ClassificationAssignmentURI_ | `uri` | `crm:E17_Type_Assignment1`|
| _ClassificationObject_ | `rdfs:label` | `crm:E55_Type1`|
| _Copyright_ | `crm:P3_has_note` | `crm:E30_Right1`|
| _CopyrightURI_ | `uri` | `crm:E30_Right1`|
| _CreditURI_ | `uri` | `crm:E33_Linguistic_Object1`|
| _DateURI_ | `uri` | `crm:E52_Time-Span1`|
| _ObjectNumber_ | `rdf:value` | `crm:E42_Identifier1`|
| _ObjectNumberLabel_ | `rdfs:label` | `crm:E42_Identifier1`|
| _ObjectNumberURI_ | `uri` | `crm:E42_Identifier1`|
| _ObjectURI_ | `uri` | `crm:E22_Man-Made_Object1`|
| _ProductionURI_ | `uri` | `crm:E12_Production1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `crm:E12_Production1` | `crm:P4_has_time-span` | `crm:E52_Time-Span1`|
| `crm:E17_Type_Assignment1` | `crm:P42_assigned` | `crm:E55_Type1`|
| `crm:E17_Type_Assignment1` | `crm:P21_had_general_purpose` | `xsd:http://vocab.getty.edu/aat/300179869`|
| `crm:E22_Man-Made_Object1` | `crm:P108i_was_produced_by` | `crm:E12_Production1`|
| `crm:E22_Man-Made_Object1` | `crm:P41i_was_classified_by` | `crm:E17_Type_Assignment1`|
| `crm:E22_Man-Made_Object1` | `crm:P104_is_subject_to` | `crm:E30_Right1`|
| `crm:E22_Man-Made_Object1` | `crm:P67i_is_referred_to_by` | `crm:E33_Linguistic_Object1`|
| `crm:E22_Man-Made_Object1` | `crm:P48_has_preferred_identifier` | `crm:E42_Identifier1`|
| `crm:E22_Man-Made_Object1` | `crm:P2_has_type` | `crm:E55_Type1`|
| `crm:E33_Linguistic_Object1` | `crm:P2_has_type` | `xsd:http://vocab.getty.edu/aat/300026687`|
