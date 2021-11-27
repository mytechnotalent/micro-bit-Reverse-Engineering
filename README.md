![image](https://github.com/mytechnotalent/micro-bit-Reverse-Engineering/blob/main/micro-bit%20Reverse%20Engineering.png?raw=true)

# micro:bit
# Reverse Engineering
A micro:bit entry-level Reverse Engineering tutorial code repo which was presented at the 2021 micro:bit LIVE event.

## Schematic
![image](https://github.com/mytechnotalent/micro-bit-Reverse-Engineering/blob/main/schematic.png?raw=true)

## Parts
[micro:bit](https://microbit.org/buy/?location=US&version=microbitV2)

## How To Install CODAL Build Tools
### Install WSL (Windows Users) Windows Command Prompt
```bash
wsl --install
```

### Git Clone microbit-v2-samples (Inside WSL)
```bash
cd
cd Documents
git clone https://github.com/lancaster-university/microbit-v2-samples
cd microbit-v2-samples
```

### Install ARM Build Tools (Inside WSL)
```bash
sudo apt install gcc
sudo apt install git
sudo apt install cmake
sudo apt install gcc-arm-none-eabi binutils-arm-none-eabi
```

### Build micro:bit CODAL Samples & Copy Binaries To Windows Desktop (Inside WSL)
```bash
python3 build.py
cp MICROBIT.hex /mnt/c/Users/YOUR_USER/Desktop
cp build/MICROBIT /mnt/c/Users/YOUR_USER/Desktop/
```


## License
[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)
