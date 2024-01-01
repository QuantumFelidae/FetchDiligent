# FetchDiligent
A short CMake utility to fetch, build, and link Diligent Engine within your own projects.

## Remote Usage
The most simple usage just exposes the DiligentCore targets
```CMake
include(FetchContent)
FetchContent_Declare(
    Diligent
    GIT_REPOSITORY https://github.com/QuantumFelidae/FetchDiligent.git
    GIT_TAG master
)
FetchContent_MakeAvailable(Diligent)
```
Now, DiligentCore targets are available to link against. For example:
```CMake
target_link_libraries(main PRIVATE Diligent-GraphicsEngineVk-shared)
```
### Extra Diligent Modules
Obtaining the other Diligent modules, DiligentTools and DiligentFx is done by setting the appropriate variables before calling `MakeAvailable`. For example:

```CMake
include(FetchContent)
FetchContent_Declare(
    Diligent
    GIT_REPOSITORY https://github.com/QuantumFelidae/FetchDiligent.git
    GIT_TAG master
)
set(FETCH_DILIGENT_TOOLS TRUE)
set(FETCH_DILIGENT_FX TRUE)
FetchContent_MakeAvailable(Diligent)
```
Now, targets from these modules can be linked in your project. 
```CMake
target_link_libraries(main PRIVATE 
                        Diligent-Imgui
                        Diligent-AssetLoader 
                        Diligent-GraphicsEngineVk-shared)
```
### Versioning

To pin a specific git tag to pull from, one can set the variables `DILIGENT_CORE_GIT_TAG`, `DILIGENT_TOOLS_GIT_TAG`, or `DILIGENT_FX_GIT_TAG`

## Local Usage
If the CMakeLists.txt is renamed FetchDiligent.cmake, and placed in your module path, this simplifies to
```CMake
cmake_minimum_required (VERSION 3.26)

project ("Sample")
list(APPEND CMAKE_MODULE_PATH "<PATH>")
set(FETCH_DILIGENT_TOOLS TRUE)
include(FetchDiligent)

add_executable (main ${MAIN_SOURCES})


target_link_libraries(main PRIVATE 
                        Diligent-Imgui
                        Diligent-AssetLoader 
                        Diligent-GraphicsEngineVk-shared)
```
