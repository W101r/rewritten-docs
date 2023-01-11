!!! Sharing
    Due to legality reasons, we ask that none of our developers upload these records to any repository. Keep them local only.

DML records serve as a written template for each of the requests the client is capable of sending, and all the expected replies from the server.

These records can be found in Wizard101's internals, and each record can be represented as XML. Every record _must_ fall under a [protocol](dml-protocols.md).


## DML Syntax
Each DML record starts as an XML node named as a short keyword or phrase, prefixed by `MSG_[...]`. The record is then elaborated with a single child node, named `RECORD`.

The `RECORD` node holds the child nodes exclusive to the DML record. These are labeled as _DML elements_. 

### DML Elements
_An example of a DML element_:
```xml
<UserID TYPE="GID" [NOXFER="TRUE"]></UserID>
```
Each DML element begins with a camel cased identifier. Each element _must_ contain an attribute of `TYPE=[...]`, signifying the data type used for serialization/deserialization purposes. 

!!! name ""
    You can view the table for DML element types [here](dml-data-types.md).

Optionally included is the `NOXFER` (no-transfer) attribute, signifying metadata nodes that are not included in serialization.

### DML Metadata
Each record holds an amount of metadata node, noted by the first character being an underscore (`_`), and further clarified with a `NOXFER` attribute. These elements will always appear first in a record.

| Name | Type | Always Appears | Description |
| ---- | ---- | -------------- | ----------- |
| _MsgOrder       | UBYT | No  | Used during deserialization to determine the message type. |
| _MsgName        | STR  | Yes | The name of the message. | 
| _MsgDescription | STR  | Yes | A quick summary on what this message is for. |
| _MsgHandler     | STR  | Yes | Used internally to determine what method handler should be called upon receiving this message. |
| _MsgAccessLvl   | UBYT | No  | Used internally to determine that a client has sufficient permission to call this message. |

```xml title="LoginMessages.xml" linenums="1" hl_lines="3 4 5 6"
<MSG_CREATECHARACTERRESPONSE>
    <RECORD>
      <_MsgOrder TYPE="UBYT" NOXFER="TRUE">5</_MsgOrder>
      <_MsgName TYPE="STR" NOXFER="TRUE">MSG_CREATECHARACTERRESPONSE</_MsgName>
      <_MsgDescription TYPE="STR" NOXFER="TRUE">Server sends this when character creation is completed.</_MsgDescription>
      <_MsgHandler TYPE="STR" NOXFER="TRUE">MSG_CreateCharacterResponse</_MsgHandler>
      <ErrorCode TYPE="INT"></ErrorCode>
    </RECORD>
</MSG_CREATECHARACTERRESPONSE>
```
These DML elements are _not_ serialized, and serve no other purpose than developer documentation.

If the `_MsgAccessLvl` does not appear, it's safe to assume that a client with _any_ authority is capable.

For whatever reason, Kingsisle does _not_ include the `_MsgOrder` metadata element for every protocol. If this is the case, the unique message ID for every record will be the order in which those records appear _ordinally_.

## DML Record Example
An example of a _DML record_:
```xml title="GameMessages.xml" linenums="1"
<MSG_ATTACH>
    <RECORD>
        <_MsgName TYPE="STR" NOXFER="TRUE">MSG_ATTACH</_MsgName>
        <_MsgDescription TYPE="STR" NOXFER="TRUE">Attach a socket to a game object.</_MsgDescription>
        <_MsgHandler TYPE="STR" NOXFER="TRUE">MSG_Attach</_MsgHandler>
        <_MsgAccessLvl TYPE="UBYT" NOXFER="TRUE">1</_MsgAccessLvl>
        <GameObjectID TYPE="GID"></GameObjectID>
        <LoginKey TYPE="STR"></LoginKey>
        <UserID TYPE="GID"></UserID>
        <CharID TYPE="GID"></CharID>
        <ZoneName TYPE="STR"></ZoneName>
        <Location TYPE="STR"></Location>
        <TargetPlayerID TYPE="GID"></TargetPlayerID>
        <ZoneID TYPE="GID"></ZoneID>
        <Slot TYPE="INT"></Slot>
        <SessionID TYPE="GID"></SessionID>
        <SessionSlot TYPE="INT"></SessionSlot>
        <PassKey TYPE="STR"></PassKey>
        <Reattach TYPE="UBYT"></Reattach>
        <Retry TYPE="UBYT"></Retry>
        <Locale TYPE="STR"></Locale>
    </RECORD>
</MSG_ATTACH>
```