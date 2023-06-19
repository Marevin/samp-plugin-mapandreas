# Map Andreas Plugin  #

[![sampctl](https://img.shields.io/badge/sampctl-samp--plugin--mapandreas-2f2f2f.svg?style=for-the-badge)](https://github.com/philip1337/samp-plugin-mapandreas)

This plugin was initially made by Kalcor and extended bv Mauzen.  

It allows you to load different height maps and check the mininum height for any given (x,y) coordinates.  
You can use it, for example, to prevent a player from falling through the ground or in an anti-cheat to detect airbreaks easier.
<!--
## Features
- Load height map
- You can also implement it in your sampgdk plugins.  
-->

## Forum threads about this plugin:
- MapAndreas v1.2.1 Updated @ ~~[sa-mp.com](http://forum.sa-mp.com/showthread.php?t=275492)~~
- MapAndreas v1.2.1 Updated @ ~~[sa-mp.com](http://forum.sa-mp.com/showpost.php?p=3130004&postcount=153)~~
- MapAndreas v1.0 beta @ [~~sa-mp.com~~](http://forum.sa-mp.com/showthread.php?t=120013) [(blast.hk mirror)](https://sampforum.blast.hk/showthread.php?tid=120013)

## Functions
|native|params|return|
|-------|-------|:-----:|
|MapAndreas_Init|mode, const name[]|int (0 failed/1 success)|
|MapAndreas_Unload|n/a|int (0 failed/1 success)|
|MapAndreas_SaveCurrentHMap|const name[]|int (0 failed/1 success)|
|MapAndreas_FindZ_For2DCoord|Float:X, Float:Y, &Float:Z|int (0 failed/1 success)|
|MapAndreas_FindAverageZ|Float:X, Float:Y, &Float:Z|int (0 failed/1 success)|
|MapAndreas_SetZ_For2DCoord|Float:X, Float:Y, Float:Z|int (0 failed/1 success)|

- [Pawn include file: mapandreas.inc](include/mapandreas.inc)

## Installation

Simply install to your project:

```bash
sampctl package install philip1337/samp-plugin-mapandreas
```

Include in your code and begin using the library:

```pawn
#include <mapandreas>
```

### Example
Initialize MapAndreas and get a position.

    public OnGameModeInit()
    {
        MapAndreas_Init(MAP_ANDREAS_MODE_FULL, "scriptfiles/SAFull.hmap");
		
        new Float:pos;
		
        if (MapAndreas_FindAverageZ(20.001, 25.006, pos))
        {
            // Found position - Z coordinate saved in 'pos' variable
        }		
        return 0;
    }
    
    
## Build
#### Requirements
- [Modified version of gclient](https://github.com/timniederhausen/gclient)
- CMake >=3.1
- C++11
  - debian package: libc6-dev-i386

Synchronize dependencies from [DEPS](DEPS) File.

    gclient.py sync -v -f

You can also download it manually and place it into the external directory.

    mkdir build
    cd build
    cmake ..\samp-log-spdlog
    make

- [How to use cmake](https://github.com/bast/cmake-example)
