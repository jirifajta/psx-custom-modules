# Psx custom modules

Many components need to be taken care of to have a working software program to run on PlayStation 1 (aka PSX or PS1). Some routines or parts of processes are, in my opinion tedious work.<br/>The aim is to make programming for the PSX more accessible by delegating such work to modules for such routines. A framework for such modules needs to have capabilities of getting faster processes done, being manageable, and keeping at least decent performance.

**Author:** MSc Jiří Fajta<br/>
**Code implementation date:** 2019-20XX<br/>
<br/>
> [!NOTE]
> This repository only contains my own source code written from scratch which is compatible with **Mipsel GCC** (like ![PSn00bSDK](https://github.com/Lameguy64/PSn00bSDK/)) compiler.<br/>The code is intentionally not written to tied to a specific SDK to keep it flexible.
<br/>

## ![PSX PsxVramManager and PsxClutManager](/src/PsxSys/)
Makes storing, using and managing _textures_ and _cluts_ (color lookup tabels) handling in VRAM easier. 
> [!TIP]
> Also usefull for streaming these kind of assets into VRAM by swapping textures during large scenes in a program.
### Status
- [X] Code implemented and tested
- [X] Readme description
- [ ] Release

## ![PSX Polygon subdivision](/src/PsxSys/)
Subdivide polygons in screenspace to limit pixels off screen. A prototype was already made for Java which can be found at ![PSX uniform polygon processing](https://github.com/jirifajta/computer-graphics-polygon-subdivision).
### Status
- [X] Proof of Concept
- [ ] Work in progress to convert into C code.
- [ ] Release

## ![PSX uniform polygon processing](https://github.com/jirifajta/psx-uniform-polygon-processing)
Simplyfies creating and updating primitives in a uniform manner while keeping high performance.<br/>
These are written in assembly.

## More modules...
There are more coded modules. Maybe some of them will be made available later.
- custom light handling
- timer
- custom access to files on a cdrom. Like access a file, searching using a query and returning a list of a requested file type or files containing substring.
- custom GTE routines.
- split screen PoC.
- 3D stereoscopic PoC. ![See here for more.](https://github.com/jirifajta/psx-3d-stereoscopic)
- default fog and Silent Hill Fog. ![See here for more.](https://github.com/jirifajta/psx-3d-stereoscopic)
- custom memory page file system.
- concept of a gameitem.
- Level Of Detail handler.
- .....