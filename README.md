# Build_Tensorflow_Cpp
Build tensorflow for C++ API \
Normally if you build tensorflow C++ according to tensorflow homepage on Windows operating system, \
some errors will arise and the most common error is loss of definition of symbols. \
This repository helps you to build tensorflow C++ completely and without throwing any errors. \
Tensorflow version I used here is **2.6.0**
## Step 1: Install BAZEL
Download bazel for windows corresponding to the version of tf you want to build.\
Link: https://github.com/bazelbuild/bazel/releases \
In here i use bazel 3.7.2 for tensorflow version 2.6.0\
Select the bazel file with the .exe extension to download \
Set PATH for bazel. Example: C:\bazel\bazel_3.7.2.exe
## Step 2: Install MYSYS2
Download mysys2 and install. Link: https://www.msys2.org/ \
After install, set PATH: **C:\msys64\usr\bin** for mysys2.\
Use cmd.exe, run: **pacman -S git patch unzip**
## Step 3: Install Visual Studio and MSVC++
Download Visual Studio, link: https://visualstudio.microsoft.com/ and install with MSVC++
## Step 4: Install python
Download python and install, link: https://www.python.org/downloads/ \
**NOTE: Don't forget add Python to PATH**
## Step 5: Download tensorflow source and configure
Download tensorflow source, link: https://github.com/tensorflow/tensorflow \
Decompression tensorflow.\
Copy **def_file_filter.py.tpl** file in **Define Symbol Tensorflow DLL/ New Normalize**\
And paste **../tensorflow-master/tensorflow-master/tensorflow/tools/def_file_filter** (_Repalce def_file_filter.py.tpl file old_)\
Running the following at the root of your TensorFlow source tree: \
Click directory path and delete. Type **cmd** to open command line\
In command line type:** python configure.py** and answer some question\
**Please specify the location of python.[Default is...]:** Press Enter key to skip \
**Please input the desired Python library path to use. Default is [...]:** Press Enter key to skip\
**Do you wish to build TensorFlow with ROCm support? [y/N]: N**\
**Do you wish to build TensorFlow with CUDA support? [y/N]: N**\
If you build CUDA support please type: Y\
**Please specify optimization flasg to use during complilation ... [Default is /arch:AVX]:** Press Enter key to skip\
If your CPU supported AVX2 please type: **/arch:AVX2**\
**Would you like to override eigen strong inline for sone C++ compilatiopn to reduce the compilation tine? [Y/n]: Y**\
**Would uou line to interactively configure .WORKSPACE for Androi builds? [y/N]: N**\
After answer question type: \
**bazel build --config=opt tensorflow:tensorflow.lib**\
After bazel has finished building the lib please type:\
**bazel build --config=opt tensorflow:install_headers**\
IF YOU WANT BUILD DLL FILE\
**bazel build --config=opt tensorflow:tensorflow.dll**
## NOTE:
If you want build with CUDA support, please type: \
**bazel build --config=opt --config=cuda tensorflow:tensorflow.lib** \
**bazel build --config=opt --config=cuda tensorflow:install_headers** \
**bazel build --config=opt --config=cuda tensorflow:tensorflow.dll**

## I built tensorflow version 2.6.0 for AVX2 enabled CPU here: (File Tensorflow_AVX2.rar)
## https://drive.google.com/drive/folders/15mYovBLNAbFlk9y3uQr430tn2wmiohda?usp=sharing
