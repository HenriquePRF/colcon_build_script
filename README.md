# colcon_build_script

A simple bash script to streamline building ROS 2 workspaces using colcon that can be run from any directory.

## Installation

1. Clone this repository: 
```bash
git clone https://github.com/HenriquePRF/colcon_build_script.git
cd colcon_build_script
```

2. Copy the script to `~/.local/bin`:
```bash
mkdir -p ~/.local/bin
cp cb ~/. local/bin/
chmod +x ~/.local/bin/cb
```

3. Make sure `~/.local/bin` is in your PATH (most distributions include this by default):
```bash
# Add this to your ~/. bashrc if needed
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## Configuration

Change the workspace directory, edit the `ws_dir` variable in `~/.local/bin/cb`:
```bash
ws_dir="your_workspace_path"
```

## Usage

### Build entire workspace
```bash
cb
```

### Build specific packages
```bash
cb package1 package2 package3
```

## How It Works

1. Saves your current directory
2. Navigates to the configured ROS 2 workspace
3. Runs colcon build with CMAKE_EXPORT_COMPILE_COMMANDS enabled
4. Returns you to your starting directory

> **Note:** The script builds with `CMAKE_EXPORT_COMPILE_COMMANDS=ON` which generates a `compile_commands.json` file. This enables better IntelliSense and code completion in VSCode and other IDEs. 
