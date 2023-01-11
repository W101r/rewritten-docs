| Name | C++ Type | Binary |
| ---- | -------- | ------ |
BYT |	int8_t |	Signed 1-byte integer. |
UBYT |	uint8_t |	Unsigned 1-byte integer. |
SHRT |	int16_t |	Signed 2-byte integer in little-endian byte order. |
USHRT |	uint16_t |	Unsigned 2-byte integer in little-endian byte order. |
INT |	int32_t |	Signed 4-byte integer in little-endian byte order. |
UINT |	uint32_t |	Unsigned 4-byte integer in little-endian byte order. |
STR |	uint8_t[] or char[] |	A length-prefixed string of bytes, with the length being a USHRT. |
WSTR |	uint16_t[] or char16_t[] |	A length-prefixed string of little-endian UTF-16 characters without the Byte Order Mark, with the length being a USHRT. |
FLT |	float |	IEEE-754 32-bit floating point integer in little-endian byte order. |
DBL |	double |	IEEE-754 64-bit floating point integer in little-endian byte order. |
GID |	uint64_t |	Unsigned 8-byte integer in little-endian byte order. |

!!! name ""
    This table is from Joshsora's Libki.