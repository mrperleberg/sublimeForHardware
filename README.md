# Sublime Text 3 for Hardware Development

This repository contains all Packages for **Sublime Text 3**  that I have installed in my computer. Main packages in this repository is focused in hardware development in Verilog and VHDL.

## Installation on Windows:

If you already have some Packages installed, I recommend making a backup of `C:\Users\<yourUser>\AppData\Roaming\Sublime Text 3\Packages` folder.

- **Install** Package Control inside sublime text 3 (Preferences -> Install Package Control).
- **Clone/Download** this github repository to anywhere in your computer.
- **Copy** the `githubRepository/Packages` folder to `C:\Users\<yourUser>\AppData\Roaming\Sublime Text 3\Packages`
- **Restart** Sublime Text 3

### Symbolic link

Instead of copying the `githubRepository/Packages` folder, you can also create a symbolic link from `C:\Users\<yourUser>\AppData\Roaming\Sublime Text 3\Packages` to `githubRepository\Packages` folder, with the following commands:

    cd C:\Users\Murilo\AppData\Roaming\Sublime Text 3
    mklink /d Packages "path\to\githubRepository\Packages"

So you can push further updates.

## ModelSim Linter

Linter is a analysis tool that find errors in source codes. Linter can be configured inside Sublime Text 3 by using ModelSim tools. For that:

### 1: Insert ModelSim tools to system PATH:

[How to add folder to PATH on Windows](https://www.architectryan.com/2018/03/17/add-to-the-path-on-windows-10/)
**1.1** Press Windows, then search for `PATH` or `env`, and go to `Edit the system environment variables`. 
**1.2** Go to `Environment Variables`
**1.3** Then in `System Variables`, edit the `PATH`,
**1.4** In a new line, insert the modelsim tools folder: `C:\intelFPGA\20.1\modelsim_ase\win32aloem`

### 2: Create a temporary ModelSim project

In Modelsim, just create a new project anywhere. No files need to be added in the project. This project will be used by Linter when parsing the code.
I recommend in a folder as 

    C:\Users\<yourUser>\Documents\modelsimTemporaryForSublime\

After created, the temporary project can be closed inside the modelsim.

### 3: Configure Linter to use the temporary project

In Sublime Text 3, go to
Preferences -> Package Settings -> SublimeLinter -> Settings.
Set `working_dir` from **both** `vcom` and `vlog` to use the temporary project:

    "working_dir": "C:\Users\<yourUser>\Documents\modelsimTemporaryForSublime\"

#### Known Bugs:

**Linter randomly stops parsing source code.** 
Probable cause: Interference between ModelSim and Linter trying to parse the source code at the same time.
Solution: remove the `.lock` file from the temporary modelsim folder.

## Key binds

`CTRL + A` Auto indents the inputs and signal declarations from .vhd files
`F12` Call *Text Pastry* Package, which can generate a list of numbers
