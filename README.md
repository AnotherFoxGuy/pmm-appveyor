# Poco MD5 Example

Example of and MD5 calculation app using POCO C++ libraries installed with Conan C/C++ package manager.

## Compiling steps

1. Create a build directory:

    ```
    $ mkdir build && cd build
    ```

2. Configure the CMake project (Using MSVC 15 in this example):

    ```
    $ cmake .. -G "Visual Studio 15 2017 Win64"
    ```

3. Build it:

    ```
    $ cmake --build . --config Release
    ```

4. Run the application:

    ```
    $ .\bin\md5.exe
    c3fcd3d76192e4007dfb496cca67e13b
    ```
