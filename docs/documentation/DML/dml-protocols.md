!!! Sharing
    Due to legality reasons, we ask that none of our developers upload these records to any repository. Keep them local only.
    
A __DML Protocol__ is a subsection of Kingisle's Networking Protocol. It serves to elaborate requests to in-game context, such as `HousingMessages`, or `LoginMessages`.

## Protocol Syntax
Kingisle stores these protocols locally, inside the `root.wad`. Each protocol can be represented as an XML file.

The very first node included in every protocol is an XML metadata node, which states the XML version used for each file.

The following and last base node will be named after the file. This is where the protocol records lie. The child nodes will contain the written template for any message relating to the protocol. These are called the protocol _records_. However, the very first record is an exception. It is instead replaced with a metadata node, labeled `_ProtocolInfo`.

### Protocol Info
The protocol information is sorted as the first child node, under a metadata node, labeled always as `_ProtocolInfo`.

The ProtocolInfo node will always contain 4 elements:

| Name   | Description   |
| ------ | ------------- |
| ServiceID           | The unique ID of this protocol.             |
| ProtocolType        | A one-word descriptor for the protocol.     |
| ProtocolVersion     | The version of the protocol.                |
| ProtocolDescription | A short summary of details of the protocol. |

_An example of the ProtocolInfo node_:
```xml
<_ProtocolInfo>
    <RECORD>
      <ServiceID TYPE="UBYT">5</ServiceID>
      <ProtocolType TYPE="STR">GAME</ProtocolType>
      <ProtocolVersion TYPE="INT">1</ProtocolVersion>
      <ProtocolDescription TYPE="STR">Game Messages</ProtocolDescription>
    </RECORD>
</_ProtocolInfo>
```

### Protocol Records
!!! note ""
    You can find further elaboration on protocol records under [this](dml-records.md) section.

Every node after the protocol information will be the written template for every message the client is capable of sending, and all of the replies expected from the related server.

Each record will contain some amount of metadata, including the `_MsgOrder` for the given record. For whatever reason, Kingsisle does _not_ include this metadata element for every protocol. If this is the case, the unique message ID for every record will be the order in which those elements appear _ordinally_.

## Finding the Protocols
In Wizard101's case, the DML protocols are stored in the `root.wad` found under the `GameData` directory. Using an external tool, we can unpack the `.wad` files.

!!! Unpacking
    Unpacking the `root.wad` will take many moments! Give it some time.

Once finally unpacked, we are introduced to a multitude of uncompressed data. We can further elaborate the search by searching for `*Messages.xml`.