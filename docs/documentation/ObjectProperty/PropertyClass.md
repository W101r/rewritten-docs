!!! Warning
    The following information is still being reverse engineered. Take as a general idea instead of practical documenatation.

## PropertyClass
`PropertyClass` is an abstract type used to signify which internal complex types are capable of being subjected to [binary serialization](PropertyClass.md#serialization). Each field of the following class will contain another nested attribute, labeled simply as `Property`. A major (possibly only) usage case for Property Classes is for communication through the [data management layer](../DML/dml.md).

### Property
Each field of the PropertyClass contains an attribute known simply as `Property`. This serves as specific field elaboration to the binary serialization process with relevant information. 

Each property class contains the minimum set of information needed for serialization in the repesentation of two more classes: `Type` and `Value`.

#### Type
The `Type` class (or enum?) serves as a handler for the property's largest concern as a C++ field: it's memory footprint. This list is **separate** from the DML [data types](../DML/dml-data-types.md).

#### Value
Still unclear, but pretty self-explainatory from the name.

## Serialization


## Finding Property Classes
Finding these property classes is trivial. Simply pass a launch argument `-x` with a following file name (which you can represent as a `.xml`) to the `WizardGraphicalClient.exe`. However, this dump does _not_ include their hash. You may use [WizWalker](https://github.com/wizwalker/wizwalker)'s type dump tool for a more verbose dump of the PropertyClasses and their respective hashes.