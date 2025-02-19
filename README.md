# Source SDK 2013 - CMake
This project ports the buildsystem from VPC to CMake.

The layout of the CMake projects should be similar to that of VPC. Hopefully it should feel familiar even if you have no experience with CMake. The base scripts are in _cmake_scripts. Each project has its own corresponding .cmake file similar to VPC. 

Example: src/tier1/tier1.vpc -> src/tier1/tier1.cmake

The batch and shell scripts to generate projects now call CMake instead and place project files in a created "build" directory. If you're comfortable with CMake, you don't have to rely on these at all and can use your favorite IDE's CMake integration.

If your folder structure for SDK2013 is different, you should only have to modify SRCDIR and GAMEDIR in the CMakeLists.txt file if you need to move things around.

## Compiler Support

## General
By default, this targets C++14 since modern VS defaults to C++14 anyway. 

### Windows
VS2019 and VS2022 are known to build, but this is untested with older versions.

### Linux
GCC 5 or greater should also work fine. This repo should build out of the box with the Steam Runtime Soldier container. Scout will require a bit of tinkering to update CMake and switch to GCC 5 or higher.

### macOS
This should also build on macOS. Just note that for Xcode, only versions 9.4.1 and earlier support the i386 architecture. If building from a different IDE, or command line, you might not have to worry about this depending on your setup. The project generation scripts should output Makefiles by default.

Building with macOS 10.13.6 (High Sierra) is recommended. Please check this project out if you're interested in a macOS container: https://github.com/sickcodes/Docker-OSX

## Credits

I'd like to thank JJL772, OzxyBox, and those behind the Source-PlusPlus repo which includes Joshua Ashton, SCell555, and Gocnak.

The modified particles.lib that allows modern VS to build came from Source-PlusPlus: https://github.com/Joshua-Ashton/Source-PlusPlus

JJL772 has a repo which helped me with the ABI difference issues on newer GCC versions: https://github.com/JJL772/source-sdk-2013

OzxyBox has a Source SDK repo which supports VS2022 which I referenced for help a few times. This CMake port is not NEARLY as extensive as the changes here: https://github.com/ozxybox/source-mp13-vs2022


# Original README
Source code for Source SDK 2013.

Contains the game code for Half-Life 2, HL2: DM and TF2.

**Now including Team Fortress 2! ✨**

## Build instructions

Clone the repository using the following command:

`git clone https://github.com/ValveSoftware/source-sdk-2013`

### Windows

Requirements:
- Source SDK 2013 Multiplayer installed via Steam
- Visual Studio 2022

Inside the cloned directory, navigate to `src`, run:
```bat
createallprojects.bat
```
This will generate the Visual Studio project `everything.sln` which will be used to build your mod.

Then, on the menu bar, go to `Build > Build Solution`, and wait for everything to build.

You can then select the `Client (Mod Name)` project you wish to run, right click and select `Set as Startup Project` and hit the big green `> Local Windows Debugger` button on the tool bar in order to launch your mod.

The default launch options should be already filled in for the `Release` configuration.

### Linux

Requirements:
- Source SDK 2013 Multiplayer installed via Steam
- podman

Inside the cloned directory, navigate to `src`, run:
```bash
./buildallprojects
```

This will build all the projects related to the SDK and your mods automatically against the Steam Runtime.

You can then, in the root of the cloned directory, you can navigate to `game` and run your mod by launching the build launcher for your mod project, eg:
```bash
./mod_tf
```

*Mods that are distributed on Steam MUST be built against the Steam Runtime, which the above steps will automatically do for you.*

## Distributing your Mod

There is guidance on distributing your mod both on and off Steam available at the following link:

https://partner.steamgames.com/doc/sdk/uploading/distributing_source_engine

## Additional Resources

- [Valve Developer Wiki](https://developer.valvesoftware.com/wiki/Source_SDK_2013)

## License

The SDK is licensed to users on a non-commercial basis under the [SOURCE 1 SDK LICENSE](LICENSE), which is contained in the [LICENSE](LICENSE) file in the root of the repository.

For more information, see [Distributing your Mod](#markdown-header-distributing-your-mod).
