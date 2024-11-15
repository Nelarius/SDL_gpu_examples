include(FetchContent)

# Declare
FetchContent_Declare(SDL
    GIT_REPOSITORY "https://github.com/libsdl-org/SDL"
    GIT_TAG "78cc5c173404488d80751af226d1eaf67033bcc4"
    GIT_SHALLOW ON) # preview-3.1.6

FetchContent_Declare(SDL_gpu_shadercross
    GIT_REPOSITORY "https://github.com/libsdl-org/SDL_gpu_shadercross"
    GIT_TAG "8c45abff9a8195da6779e63b0a7dc6f90013cf01")

FetchContent_Declare(SPIRV_Cross
    GIT_REPOSITORY "https://github.com/KhronosGroup/SPIRV-Cross"
    GIT_TAG "0e2880ab990e79ce6cc8c79c219feda42d98b1e8") # MoltenVk-1.1.5

# Fetch
message(STATUS "Fetching SDL...")
set(SDL_STATIC ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(SDL)

message(STATUS "Fetching SDL_gpu_shadercross...")
FetchContent_MakeAvailable(SDL_gpu_shadercross)

message(STATUS "Fetching SPIRV-Cross...")
FetchContent_MakeAvailable(SPIRV_Cross)

# Configure
add_library(SDL_gpu_shadercross INTERFACE)
target_include_directories(SDL_gpu_shadercross INTERFACE ${sdl_gpu_shadercross_SOURCE_DIR})
