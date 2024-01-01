cmake_minimum_required( VERSION 3.25)

include(FetchContent)
include(FindVulkan)

file(MAKE_DIRECTORY "${FETCH_CONTENT_BASE_DIR}/DiligentCore")

set(DILIGENTCORE_SRC_DIR "${FETCHCONTENT_BASE_DIR}/DiligentCore/")
set(DILIGENTCORE_BIN_DIR "${FETCHCONTENT_BASE_DIR}/DiligentCore-build")

FetchContent_Declare(DiligentCore 
    SOURCE_DIR  ${DILIGENTCORE_SRC_DIR}
    BINARY_DIR ${DILIGENTCORE_BIN_DIR}
    GIT_REPOSITORY https://github.com/DiligentGraphics/DiligentCore.git
    GIT_TAG master
)
FetchContent_MakeAvailable(DiligentCore)

if(${FETCH_DILIGENT_TOOLS})
    FetchContent_Declare(
        DiligentTools
        GIT_REPOSITORY https://github.com/DiligentGraphics/DiligentTools.git
        GIT_TAG master
    )
    FetchContent_MakeAvailable(DiligentTools)
endif()

if(${FETCH_DILIGENT_FX})
    FetchContent_Declare(
        d_fx
        GIT_REPOSITORY https://github.com/DiligentGraphics/DiligentFX.git
        GIT_TAG master
    )
    FetchContent_MakeAvailable(d_fx)
endif()