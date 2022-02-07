# SITL_ArduPilot_FlightGear
![image](https://user-images.githubusercontent.com/20712533/152864198-187b419e-3527-48c5-8b77-4e59655b5f78.png)

## Como executar o SITL disponível no repositório do ArduPilot

As instruções podem ser encontradas [aqui](https://ardupilot.org/dev/docs/SITL-setup-landingpage.html).

Elas não funcionaram diretamente. 
Foi necessário alterar o script sim_vehicle.py contido no repositório ardupilot/Tools/autotest devido a um erro ao carregar os parâmetros contidos em Tools/autotest/default_params.
A seguir contêm as alterações realizadas em sim_vehicle.py:
![image](https://user-images.githubusercontent.com/20712533/152863357-177ad93a-d360-42e8-87fc-10bbd90f0bc4.png)

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

Para construir o projeto do ardupilot para um tipo específico de frame e para utilizar no SITL, execute os seguintes comandos diretamente da raiz do repositório ArduPilot:
- ./waf configure --board sitl
- ./waf copter

A partir disso é possível inicializar o veículo simulado e enviar comandos para ele pelo MAVProxy ou outra GCS de sua escolha.
Para inicializar:
- ../Tools/autotest/sim_vehicle.py --console --map

Maiores informações sobre o controle do veículo estão disponíveis [aqui](https://ardupilot.org/dev/docs/sitl-examples.html). Aprender a utilizar o MAVProxy é uma mão na roda.

## Como utilizar o simulador de vôo Flight Gear

- Instale o flight gear com o seguinte comando: sudo apt-get install flightgear
- Execute o script fg_quad_view.sh ou fg_quad_plane.sh dependendo da aeronave em Tools/autotest.
- Execute o sim_vehicle.py passando uma localização como argumento como "-L KSFO" (Aeroporto Internacional de São Francisco)

Verifique que está tudo funcionando digitando os seguintes comandos no console do MAVProxy:
- mode guided
- arm throttle
- takeoff 40
Os resultados estão na imagem a seguir:
![image](https://user-images.githubusercontent.com/20712533/152866688-cb6151d5-a920-4a0e-bc87-73179cee1f6a.png)

## TODO

- Como carregar diferentes mapas no Flight Gear?
- Como conectar um controle físico (joystick) ao Flight Gear SITL Ardupilot?
- Como alterar a aparência do drone simulado no Flight Gear?
- Como adicionar câmera com gimbal ao drone simulado?
- Como adicionar sensores direcionados para baixo para pouso?
- Como simulador Flight Companion Computer? Utilizar um físico?

