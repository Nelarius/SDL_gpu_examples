Collection of examples to demonstrate the usage of the SDL_GPU API.

To clone and build:
```
git clone https://github.com/libsdl-org/SDL
cd SDL
mkdir build
cd build
cmake ..

cd ../..
git clone --recursive https://github.com/TheSpydog/SDL_gpu_examples
cd SDL_gpu_examples
mkdir build
cd build
cmake .. -DSDL3_DIR="full/path/to/SDL/build"
```
then run `make` or your favorite IDE.

You will also need the SPIRV-Cross dynamic library in your executable directory. You can grab the latest prebuilt library from [this page](https://github.com/KhronosGroup/SPIRV-Cross/actions). Scroll down to Artifacts, then download the package for your target operating system. Then copy the following file into your build directory, based on your target OS:

* **Windows**: `bin/spirv-cross-c-shared.dll`
* **MacOS**: `lib/spirv-cross-c-shared.0.dylib`
* **Linux**: `lib/spirv-cross-c-shared.so.0`


