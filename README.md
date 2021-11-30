![image](https://github.com/mytechnotalent/micro-bit-Reverse-Engineering/blob/main/micro-bit%20Reverse%20Engineering.png?raw=true)

# micro:bit
# Reverse Engineering
A micro:bit entry-level Reverse Engineering tutorial code repo which was presented at the 2021 micro:bit LIVE event.

## Schematic
![image](https://github.com/mytechnotalent/micro-bit-Reverse-Engineering/blob/main/schematic.png?raw=true)

## Parts
[micro:bit](https://microbit.org/buy/?location=US&version=microbitV2)

## How To Install CODAL Build Tools
### Install WSL (Windows Command Prompt)
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

## STEP 1: Flash `MICROBIT.hex` To micro:bit (Windows Command Prompt)
```bash
cd Desktop
cp MICROBIT.hex E:
```

## STEP 2: Download & Extract Ghidra To Windows Desktop
```
Visit https://github.com/NationalSecurityAgency/ghidra/releases
Download ghidra_XX.X-BETA_PUBLIC_XXXXXXXX.zip
Right-Click Zip File & Unzip To Desktop
```

## STEP 3: Download & Install Java SDK
```
Download Java SDK https://download.oracle.com/java/XX/latest/jdk-XX_windows-x64_bin.msi
```

## STEP 4: Run Ghidra
```
Double-Click ghidraRun.bat
Bypass Windows Prompt & Run
```

## STEP 5: Setup Ghidra Project (Windows Command Prompt)
```bash
cd Desktop
mkdir micro-bit
cp MICROBIT micro-bit
```

## STEP 6: Create & Run Ghidra Project (Ghidra Application)
```
Click File
Click New Project...
Click Next >>
Project Directory: C:\Users\YOUR_USER\Desktop\micro-bit
Project Name: micro-bit
Click Finish
Drag & Drop MICROBIT File Into Ghidra App Into Active Project: micro-bit Folder
Click OK
Click OK
Double-Click MICROBIT
```

## STEP 7: Reverse Engineer Ghidra micro-bit
```
Click Yes
Click Analyze
Filter: main
Double-Click main In Exports Folder Within Symbol Tree (Left-Hand Side)
In Decompile:main Tab, Double-Click "HELLO WORLD"
Click Window Menu - Bytes: MICROBIT
Visit https://www.asciitable.com (ASCII Table)
In Listing: MICROBIT Tab, Left-Click 48 (48 45 4c)
In Bytes: MICROBIT Window, Click Paper/Pencil Icon, 4 In 48 Will Blink
Type 48 41 43 4b 59 (Turns HELLO into HACKY)
In Decompile:main Tab, Observe Line `codal::AnimatedDisplay::scroll(&uBit.display.super_AnimatedDisplay,aMStack12,0x78);`
Double-Click On The Above Code Line, Click `codal`
In Decompile:main Tab, Right-Click `0001c6cc 78 22           movs       r2,#0x78`, Patch Instruction, Click OK
Visit https://lancaster-university.github.io/microbit-docs/ubit/display/#scroll (micro:bit runtime API)
Change 0x78 to 0xd8, Press Enter (Will Slow Down Animation)
Click File, Export Program...
Format: ELF
Output File: C:\Users\YOUR_USER\Desktop\MICROBIT-hack
Click OK
```

## STEP 8: Copy `MICROBIT-hack` To WSL (Inside WSL)
```bash
cp /mnt/c/Users/YOUR_USER/Desktop/MICROBIT-hack .
arm-none-eabi-objcopy -O ihex MICROBIT-hack MICROBIT-hack.hex
cp MICROBIT-hack.hex /mnt/c/Users/YOUR_USER/Desktop
```

## STEP 9: Flash `MICROBIT-hack.hex` To micro:bit (Windows Command Prompt)
```bash
cp MICROBIT-hack.hex E:
```

## STEP 10: Save Ghidra Project
```
Click File, Exit Ghidra, Save
```

## Additional micro:bit STEM Resources
[Python For Kids](https://github.com/mytechnotalent/Python-For-Kids)
[Study Buddy](https://github.com/mytechnotalent/MicroPython-micro-bit-Study-Buddy)
[Talking TextaBot](https://github.com/mytechnotalent/MicroPython-micro-bit-Talking-TextaBot)
[Talking Heads Or Tails](https://github.com/mytechnotalent/MicroPython-micro-bit-Talking-Heads-Or-Tails)

## License
[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)
