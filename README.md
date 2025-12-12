# RoboDC - Sistema Completo de Controle e Interação com Robô

![Ionic](https://img.shields.io/badge/Ionic-6.1.9-blue)
![Angular](https://img.shields.io/badge/Angular-15.0.0-red)
![FastAPI](https://img.shields.io/badge/FastAPI-Latest-green)
![ROS2](https://img.shields.io/badge/ROS2-Humble-blue)

Sistema completo para controle e interação com o robô DC na UFSCar, composto por aplicativo mobile, API backend e integração ROS.

## 📋 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Arquitetura do Sistema](#-arquitetura-do-sistema)
- [Componentes](#-componentes)
- [Funcionalidades](#-funcionalidades)
- [Requisitos](#-requisitos)
- [Instalação e Configuração](#-instalação-e-configuração)
- [Uso](#-uso)
- [Estrutura do Repositório](#-estrutura-do-repositório)
- [Documentação Adicional](#-documentação-adicional)
- [Contribuindo](#-contribuindo)
- [Licença](#-licença)

## 🤖 Sobre o Projeto

O **RoboDC** é um sistema completo desenvolvido para a Universidade Federal de São Carlos (UFSCar) que permite a interação com um robô de serviço através de um aplicativo mobile. O projeto integra tecnologias modernas de desenvolvimento web/mobile com sistemas robóticos ROS (Robot Operating System).

### Principais Características

- 📱 **Aplicativo Mobile**: Interface Ionic/Angular para controle intuitivo
- 🚀 **API FastAPI**: Backend moderno com suporte a ROS1 e ROS2
- 🤖 **Integração ROS**: Sistema completo de navegação e controle
- 🎭 **Expressões Faciais**: Controle de LEDs via Bluetooth
- 🗣️ **Text-to-Speech**: Síntese de voz integrada
- 📍 **Navegação Autônoma**: Sistema de localização e navegação
- ♟️ **Recursos Interativos**: Jogos, eventos, informações do RU

## 🏗 Arquitetura do Sistema

```
┌─────────────────┐
│   RoboDC App    │  (Ionic/Angular)
│  (Mobile/Web)   │
└────────┬────────┘
         │ HTTP/REST
         ▼
┌─────────────────┐
│   RoboDC API    │  (FastAPI)
│   (Backend)     │
└────────┬────────┘
         │ ROS Topics/Services
         ▼
┌─────────────────┐
│   RoboDC ROS2   │  (ROS2 Humble)
│  (Robot Control)│
└─────────────────┘
         │
         ▼
    🤖 Robô Físico
```

## 🧩 Componentes

### 1. RoboDC App (`robodc-app/`)

Aplicativo mobile desenvolvido em Ionic/Angular que serve como interface principal de usuário.

**Tecnologias:**
- Ionic Framework 6.1.9
- Angular 15.0.0
- Capacitor 4.7.0
- TypeScript

**Funcionalidades:**
- Controle remoto do robô
- Consulta ao cardápio do RU
- Sistema de navegação
- Gerenciamento de eventos
- Jogo de xadrez
- Controle de expressões faciais
- Suporte multilíngue (PT-BR, EN-US)

### 2. RoboDC API (`robodc-api/`)

API REST desenvolvida em FastAPI que gerencia a comunicação entre o app e o sistema ROS.

**Tecnologias:**
- FastAPI
- Python 3.x
- ROS1/ROS2 (configurável)
- Bluetooth (PyBluez)

**Funcionalidades:**
- Endpoints de navegação
- Controle de LEDs/expressões
- Suporte a ROS1 (move_base) e ROS2 (nav2)
- Documentação automática (Swagger/ReDoc)
- CORS configurável

### 3. RoboDC ROS2 (`robodc-ros2/`)

Pacotes ROS2 para controle de hardware e navegação do robô.

**Componentes:**
- `modubot_joystick`: Controle via joystick
- `modubot_model_description`: Modelo do robô
- `modubot_odometry`: Sistema de odometria
- `modubot_teleop`: Teleoperação
- `urdf_description`: Descrição URDF
- `teleop_twist_keyboard`: Controle via teclado

## ✨ Funcionalidades

### Interface Mobile
- ✅ Controle remoto do robô (joystick virtual)
- ✅ Navegação para locais pré-definidos
- ✅ Consulta de cardápio do RU em tempo real
- ✅ Localização e mapas
- ✅ Calendário de eventos
- ✅ Jogo de xadrez
- ✅ Expressões faciais personalizáveis
- ✅ Text-to-Speech
- ✅ Suporte multilíngue

### API Backend
- ✅ Navegação autônoma (move_base/nav2)
- ✅ Status de navegação em tempo real
- ✅ Cancelamento de navegação
- ✅ Controle de LEDs via Bluetooth
- ✅ Suporte a ROS1 e ROS2
- ✅ Documentação interativa

### Sistema ROS
- ✅ Controle de motores
- ✅ Odometria
- ✅ Navegação autônoma
- ✅ Teleoperação
- ✅ Modelo 3D do robô

## 📦 Requisitos

### Para o Aplicativo (robodc-app)
- Node.js 14+
- npm ou yarn
- Ionic CLI
- (Opcional) Android Studio para build Android

### Para a API (robodc-api)
- Python 3.8+
- ROS1 (Noetic) ou ROS2 (Humble)
- Bluetooth adapter (para controle de LEDs)

### Para ROS2 (robodc-ros2)
- Ubuntu 20.04+ ou 22.04
- ROS2 Humble
- colcon build tools

## 🚀 Instalação e Configuração

### 1. Clone o Repositório

```bash
git clone <repository-url>
cd robodc
```

### 2. Configure o Aplicativo

```bash
cd robodc-app
npm install
```

**Configuração de ambiente:**
- Edite `src/environments/environment.ts` para desenvolvimento
- Edite `src/environments/environment.prod.ts` para produção

### 3. Configure a API

```bash
cd robodc-api
pip install -r requirements.txt

# Para ROS1:
pip install -r requirements-ros1.txt

# Para ROS2:
pip install -r requirements-ros2.txt
```

**Configuração de variáveis de ambiente:**

Crie um arquivo `.env`:

```bash
ROS_VERSION=ros2              # ou ros1
ROS_NODE_NAME=robodc_api_node
DEBUG=False
BLUETOOTH_ADDRESS=8C:AA:B5:93:69:EE
BLUETOOTH_PORT=1
```

### 4. Configure o ROS2

```bash
cd robodc-ros2/modubot_ws
colcon build
source install/setup.bash
```

## 🎮 Uso

### Executar o Aplicativo

**Modo desenvolvimento (web):**
```bash
cd robodc-app
ionic serve
```

**Build para Android:**
```bash
ionic capacitor build android
```

### Executar a API

**Com ROS2:**
```bash
cd robodc-api
export ROS_VERSION=ros2
uvicorn main:app --host 0.0.0.0 --port 8000
```

**Com ROS1:**
```bash
cd robodc-api
export ROS_VERSION=ros1
uvicorn main:app --host 0.0.0.0 --port 8000
```

**Acessar documentação:**
- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

### Executar ROS2

**Terminal 1 - Navegação:**
```bash
cd robodc-ros2/modubot_ws
source install/setup.bash
ros2 launch <seu_launch_file>
```

**Terminal 2 - Teleop (opcional):**
```bash
cd robodc-ros2/modubot_ws
source install/setup.bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

## 📁 Estrutura do Repositório

```
robodc/
├── robodc-api/              # Backend API (FastAPI)
│   ├── routers/             # Endpoints REST
│   ├── services/            # Lógica de negócio e ROS
│   ├── schemas/             # Modelos de dados
│   ├── main.py              # Aplicação principal
│   └── requirements*.txt    # Dependências Python
│
├── robodc-app/              # Aplicativo Mobile (Ionic/Angular)
│   ├── src/
│   │   ├── app/
│   │   │   ├── pages/       # Páginas do app
│   │   │   ├── services/    # Serviços Angular
│   │   │   └── models/      # Modelos TypeScript
│   │   ├── assets/          # Recursos estáticos
│   │   └── environments/    # Configurações de ambiente
│   └── android/             # Projeto Android (Capacitor)
│
└── robodc-ros2/             # Pacotes ROS2
    └── modubot_ws/          # Workspace ROS2
        └── src/             # Pacotes ROS
            ├── modubot_joystick/
            ├── modubot_odometry/
            ├── modubot_teleop/
            └── ...
```

## 📚 Documentação Adicional

Cada componente possui documentação detalhada:

- [RoboDC App README](robodc-app/README.md) - Documentação completa do aplicativo
- [RoboDC API README](robodc-api/README.md) - Documentação completa da API
- [API Swagger](http://localhost:8000/docs) - Documentação interativa da API (quando em execução)

## 🔧 Desenvolvimento

### Executar Testes

**App:**
```bash
cd robodc-app
npm test
```

**API:**
```bash
cd robodc-api
pytest
```

### Build de Produção

**App (Web):**
```bash
cd robodc-app
ionic build --prod
```

**App (Android):**
```bash
cd robodc-app
ionic capacitor build android --prod
```

## 🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request
