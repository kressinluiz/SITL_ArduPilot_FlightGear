# SITL_ArduPilot_FlightGear

## Como executar o SITL disponível no repositório do ArduPilot

Loremm

### Setting up the Build Environment (Linux/Ubuntu)

- sudo apt-get update
- sudo apt-get install git
- sudo apt-get install gitk git-gui

### Clone ArduPilot Repository

- git clone https://github.com/ArduPilot/ardupilot.git
- cd ardupilot
- git submodule update --init --recursive

### Install some required packages

Caminho no repositório que contêm o script para instalar o script
- Tools/environment_install/install-prereqs-ubuntu.sh -y
Recarregar o 'caminho' 
- . ~/.profile

Agora deve ser possível de construir com waf de acordo com as instruções em BUILD.md na raiz do repositório.
