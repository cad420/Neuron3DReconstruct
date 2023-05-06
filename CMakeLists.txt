cmake_minimum_required(VERSION 3.16)

project(Neuron3DReconstruct LANGUAGES CXX C CUDA)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

add_subdirectory(VolumeViser)



add_executable(Neuron3DReconstruct main.cpp)

target_link_libraries(Neuron3DReconstruct PRIVATE VolumeViserLib)

target_compile_definitions(VolumeViserLib PUBLIC USE_SDF USE_LINEAR_BUFFER_FOR_TEXTURE)

target_compile_features(Neuron3DReconstruct PRIVATE cxx_std_20)

set_target_properties(
        Neuron3DReconstruct
        PROPERTIES
        CUDA_SEPARABLE_COMPILATION ON
        CUDA_ARCHITECTURES 80
)