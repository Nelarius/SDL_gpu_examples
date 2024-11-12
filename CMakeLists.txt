cmake_minimum_required(VERSION 3.10)
project(SDL_gpu_examples)
add_subdirectory(external)

add_executable(SDL_gpu_examples
    Examples/main.c
    Examples/Common.h
    stb_image.h
    Examples/Common.c
    Examples/ClearScreen.c
    Examples/ClearScreenMultiWindow.c
    Examples/BasicTriangle.c
    Examples/BasicVertexBuffer.c
    Examples/CullMode.c
    Examples/BasicStencil.c
    Examples/InstancedIndexed.c
    Examples/TexturedQuad.c
    Examples/ComputeSampler.c
    Examples/TexturedAnimatedQuad.c
    Examples/Clear3DSlice.c
    Examples/BasicCompute.c
    Examples/ComputeUniforms.c
    Examples/ToneMapping.c
    Examples/CustomSampling.c
    Examples/DrawIndirect.c
    Examples/ComputeSpriteBatch.c
    Examples/CopyAndReadback.c
    Examples/CopyConsistency.c
    Examples/Texture2DArray.c
    Examples/TriangleMSAA.c
    Examples/Cubemap.c
    Examples/WindowResize.c
    Examples/Blit2DArray.c
    Examples/BlitCube.c
    Examples/BlitMirror.c
    Examples/GenerateMipmaps.c
    Examples/ASTC.c
)

target_include_directories(SDL_gpu_examples PRIVATE shadercross)

target_link_libraries(SDL_gpu_examples
    SDL3::SDL3-static
    SDL3::Headers
    SDL_gpu_shadercross
    spirv-cross-c
)

target_compile_definitions(SDL_gpu_examples PRIVATE SDL_GPU_SHADERCROSS_STATIC)

add_custom_command(TARGET SDL_gpu_examples POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory ${CMAKE_SOURCE_DIR}/Content $<TARGET_FILE_DIR:SDL_gpu_examples>/Content
)
