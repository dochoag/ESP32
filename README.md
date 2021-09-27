# ESP32 
Esp32 with ESP-IDF SDK on VScode

## Install

### prereq
```
sudo apt-get install git wget flex bison gperf python3 python3-pip python3-setuptools cmake ninja-build ccache libffi-dev libssl-dev dfu-util libusb-1.0-0
```

###Get ESP-IDF

https://github.com/espressif/esp-idf

```
mkdir -p ~/esp
cd ~/esp
git clone --recursive https://github.com/espressif/esp-idf.git
```
###Set up tools
```
cd ~/esp/esp-idf
./install.sh esp32
```
###Set up the environment variables

 ```
 getdit ~/.bashrc
 ```
 
add ...
```
alias get_idf='. $HOME/esp/esp-idf/export.sh'
```

## Example Hello world

###Start a proyect
```
cd ~/esp
cp -r $IDF_PATH/examples/get-started/hello_world .
cp -r ~/esp/esp-idf/examples/get-started/hello_world .
```
```
 cd hello_world/
 $ make menuconfig
 
 ```
 
 save and exit
 
 ### open Vscode
 
open vscode in directory 

```
cd hello_world/
code .
```

inside of .vscode folder create c_cpp_properties.json file with next content:


 ```
 {
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "${workspaceFolder}/**",
                "${workspaceFolder}/build",
                "${env:IDF_PATH}/components/**"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/gcc",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "intelliSenseMode": "clang-x64"
        }
    ],
    "version": 4
}
```

### Compile

```
make
```

### Flash
connect ESP32 to micro usb to computer

```
make flash
```

### Serial Monitor 
```
make monitor
```











