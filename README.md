# Digital Image Processing — Term Project 1 (Squid Game Composite)

An MFC program that composites `squid_head + squid_body − squid_points` using CxImage per-pixel operations.

## Folder layout
```
cximage/            CxImage library (retargeted to v142; build outputs are not committed)
Team12_Squid/
  team12_squid/     Our MFC project (created by VS: team12_squid.sln, .vcxproj, sources)
  DOC/              Report and result images
  sample_images/    Sample images from the assignment
```

## 1. Build the CxImage library (once after cloning)
1. Visual Studio Installer → Individual components → make sure **C++ MFC / ATL for v142 build tools (x86 & x64)** are installed
2. Open `cximage/CxImgLib.sln` → set configuration to **Unicode Debug / Win32** → Build Solution
3. Done when `cximage_wd.lib` and the other libs appear in `cximage/x86/lib/`

## 2. Settings for the new MFC project
- Project name: **`team12_squid`** (spec: the `.sln` must be named `teamNumber_teamName.sln`)
- Location: **`Team12_Squid/`**, check **Place solution and project in the same directory**
  → creates `Team12_Squid/team12_squid/team12_squid.sln` (the right depth for the `..\..\cximage` relative path)
- Platform: **x86 (Win32)** — the CxImage libraries are built as 32-bit only
- Project properties (All Configurations, Win32):
  - General → Platform Toolset: **v142**, Character Set: **Unicode**, Use of MFC: **Shared DLL**
  - C/C++ → General → Additional Include Directories: `$(SolutionDir)..\..\cximage\CxImage`
  - Linker → General → Additional Library Directories: `$(SolutionDir)..\..\cximage\x86\lib`
  - Linker → Input → Additional Dependencies (Debug):
    `png_wd.lib;jpeg_wd.lib;zlib_wd.lib;tiff_wd.lib;jbig_wd.lib;jasper_wd.lib;mng_wd.lib;libdcr_wd.lib;cximage_wd.lib`
- Add `#include "ximage.h"` to `pch.h` (or `stdafx.h`)

## Submission
- File name: `Team12_Squid.zip` (spec: `TeamNumber_TeamName.zip`)
- Zip `cximage/` and `Team12_Squid/` together so the grader can build without any modification
