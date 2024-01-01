cmake_minimum_required( VERSION 3.25)

include(FetchContent)
include(FindVulkan)

FetchContent_Declare(
    d_core
    GIT_REPOSITORY https://github.com/DiligentGraphics/DiligentCore.git
    GIT_TAG master
)

FetchContent_MakeAvailable(d_core)


if(${FETCH_DILIGENT_TOOLS})
    FetchContent_Declare(
        d_tools
        GIT_REPOSITORY https://github.com/DiligentGraphics/DiligentTools.git
        GIT_TAG master
    )
    FetchContent_MakeAvailable(d_tools)
    target_include_directories(Diligent-Imgui PRIVATE ${d_core_SOURCE_DIR}/_/_/_)
endif()

if(${FETCH_DILIGENT_FX})
    FetchContent_Declare(
        d_fx
        GIT_REPOSITORY https://github.com/DiligentGraphics/DiligentFX.git
        GIT_TAG master
    )
    FetchContent_MakeAvailable(d_fx)
endif()