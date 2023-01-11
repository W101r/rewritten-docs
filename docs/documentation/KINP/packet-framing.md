# Packet Framing
This page serves as a general overview of Kingsisle's packet framing used in Wizard101.

_Assume that every byte sequence will be in little-endian order unless otherwise stated._
## Magic Header
Each magic packet starts with a 2-byte sequence in little-endian byte order: `0xF00D`.
This is referred to as the _start signal_.

Following the start signal is another 2-byte sequence in little-endian byte order. This signifies the length of the following message.
If the length of the following body is larger than the limits of a `uint16_t`, or `0x7FFF`, the magic header will change:

#### Small Header
| Name | Type | Description |
| --- | ----------- | ------------|
| Start Signal | uint16_t | Always `0xF00D`. Indicates the start of a message. |
| length | uint16_t | The length of the following body. |

#### Large Header
| Name | Type | Description |
| --- | ----------- | ------------|
| Start Signal | uint16_t | Always `0xF00D`. Indicates the start of a message. |
| length | uint16_t | Constant `0x8000` |
| bigLength | uint32_t | The actual length of the following body. |

## Body
Starting the body off is the body header. This header forks the payload into two separate types of messages: [control](../KINP/control-mesages.md) and [data](../DML/dml.md).

| Name | Type | Description |
| --- | ----------- | ------------|
| isControl | bool | Indicates whether this packet is a control message or DML message. |
| opCode | uint8 | Determines the operation code for a control message. | 
| padding | uint16 | Padding between the body header and payload. |
| payload | uint8[] | The following payload. |

## Payload
!!! note ""
    At this point, it's recommended that you become familiar with the [Data Management Layer](../DML/dml.md) first.
If the body header indicates this payload will be a control message, then the corresponding binary buffer will begin here.

On the contrary, a data message will continue with a secondary header indicating the [DML protocol](../DML/dml-protocols.md) and [DML record](../DML/dml-records.md).

| Name | Type | Description |
| --- | ----------- | ------------|
| svcid | uint8 | The service ID of the payload; this equates to the DML protocol ID. |
| msgid | uint8 | The message ID of the payload, relative to the protocol. |
| length | uint16 | Indicates the length of the payload, including this header. |
| payload | uint8[] | The following data payload. |