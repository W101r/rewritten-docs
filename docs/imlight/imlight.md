# Imlight
Imlight is a private server emulation project by the Wizard101Rewritten community.

You can view the overview of server architecture [here](https://drive.google.com/file/d/17utqstWzrlxPp8cVjTZX4e_Hhy8ThKSn/view?usp=sharing).

---
## Quick Start

!!! Todo
    This should be expanded into subsections soon.

**Imlight** requires pre-generation of two internal systems in order to function properly.

1. KiNP Records
2. Property Classes

You can review in detail what these systems entail for [KiNP Records](../documentation/DML/dml-records.md) and [Property Classes](../documentation/ObjectProperty/PropertyClass.md).

The input needed for these systems can be found internally in Wizard101. Use the Wizard101 revision you'd like Imlight to run on.

### KiNP Records
!!! Todo
    Expand on this by creating a WAD article and explaining the file format.

This is the more difficult of the two sections. These files can be found in the `root.wad` of the game directory. However, these `.wad` files are packed and compressed and require external tooling to unravel. You can use [LINK HERE] to do exactly this.

Once unpacked, search for `*Messages.xml`. All files found are required by Imlight.

Copy these files into the `Imlight.Generator [input/records/]` directory.

### Property Classes
You can easily dump the property classes as `.xml` representation by handing launch arguments to Wizard101's executable.

In your `Wizard101/bin/` directory:
```
WizardGraphicalClient.exe -x PropertyClassDump.xml
```
You'll find the output in the same directory. Copy this file to the `Imlight.Generator [input/]` directory.