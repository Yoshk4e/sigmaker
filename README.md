# IDA Pro/Any Sigmaker for 9.X (LINUX/GNU)
Signature Maker Plugin for IDA Pro/Any >= 9.X

- can probably be ported to macOS too but its not something i would bother doing when i don't even have a one
- Note: The SDK folder just contains a placeholder and NOT the real ida SDK you get it yourself after after purchasing ida 
## Building requirements
- CMake 3.16+
- A brain
- Change the SDK paths in plugin.h to match yours ( I'm too lazy to make it work on any pc :3 )
## How to Build??
- open a terminal in your project root and paste this command ( you can ignore the warnings or suppress it)
```sh
mkdir -p build && cd build   && cmake -DCMAKE_CXX_STANDARD=23 -S .. -B .   && cmake --build .
```
## Requirements
- IDA Pro/Any Plugin SDK 9.X, Only tested for 9.X, unsure if older versions work

## Installation
Drop into plugins folder of your IDA installation.

`path\to\ida\plugins`

## Usage
In disassembly view, select a line you want to generate a signature for, and press 
**CTRL+ALT+S**
![](https://i.imgur.com/Cpz50AR.png)

The generated signature will be printed to the output console, as well as copied to the clipboard:
![](https://i.imgur.com/4yYEbb3.png)

___

| Signature type | Example preview |
| --- | ----------- |
| IDA Signature | E8 ? ? ? ? 45 33 F6 66 44 89 34 33 |
| x64Dbg Signature | E8 ?? ?? ?? ?? 45 33 F6 66 44 89 34 33 |
| C Byte Array Signature + String mask | \xE8\x00\x00\x00\x00\x45\x33\xF6\x66\x44\x89\x34\x33 x????xxxxxxxx |
| C Raw Bytes Signature + Bitmask | 0xE8, 0x00, 0x00, 0x00, 0x00, 0x45, 0x33, 0xF6, 0x66, 0x44, 0x89, 0x34, 0x33  0b1111111100001 |

___
### Finding XREFs
Generating code Signatures by data or code xrefs and finding the shortest ones is also supported:
![](https://i.imgur.com/GqLH2dF.png)

___
### Signature searching
Searching for Signatures works for supported formats:

![](https://i.imgur.com/rLR1qmt.png)

Just enter any string containing your Signature, it will automatically try to figure out what kind of Signature format is being used:

![](https://i.imgur.com/gMQpYTP.png)

Currently, all output formats you can generate are supported.

Match(es) of your signature will be printed to console:

![](https://i.imgur.com/JZjgz4a.png)
