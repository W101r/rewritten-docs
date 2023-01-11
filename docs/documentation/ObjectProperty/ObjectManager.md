### OID
An object identifier (OID) is an extensively used identification mechanism jointly developed by ITU-T and ISO/IEC for naming any type of object, concept or "thing" with a globally unambiguous name which requires a persistent name (long life-time). It is not intended to be used for transient naming. OIDs, once allocated, should not be re-used for a different object/thing.

Each `PropertyClass` and respective `Property` contains a uniquely created hash to serve as an identifier for deserializing of ObjectProperty. The OID for each object is generated at runtime using a homebrew algorithm.

#### Weak OID
The ObjectManager also contains an allocation method for generating a weak OID. It's currently unclear as to what defines an OID as "weak".