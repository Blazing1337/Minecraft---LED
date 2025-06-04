# 🧱 Minecraft Effect Control Dashboard (Node-RED + Docker)



A **web-based management dashboard** for Minecraft servers, built using **Node-RED**, with integration for **RCON**, **MQTT-controlled LEDs**, and a streamlined UI for assigning in-game effects to players.

## 🚀 Features

- ✅ Real-time player list from the active Minecraft server  
- 🎮 Effect assignment UI – choose effect, strength, and duration  
- 🌈 LED control via MQTT for immersive visual feedback (e.g., WS2812 LEDs)  
- 🔘 Trigger effects with a button  
- ⚙️ RCON integration for secure in-game command execution  
- 📊 Built-in Node-RED Dashboard interface  

## 📦 Requirements

- A Minecraft server with RCON enabled  
- Node-RED  
- An MQTT broker (e.g., Mosquitto)  
- Connected LED hardware (e.g., ESP32 + WS2812)  
- Docker & Docker Compose (optional but recommended)

## 🎯 Project Goal

Create an intuitive, visual interface for Minecraft server administrators — especially in **educational** or **STEM learning environments** — enabling simplified effect control, monitoring, and automation through modern web tools.

## ⚙️ Quick Start

### 🔧 Prerequisites

- [Docker](https://docs.docker.com/get-docker/) & [Docker Compose](https://docs.docker.com/compose/install/)  
- [Git](https://git-scm.com/)

## 🐳 Deployment via Docker

```bash
git clone https://github.com/schto173/minecraft-manager.git
cd minecraft-manager
cp .env.example .env
```

Edit `.env`:

```
MC_HOST=minecraft
MC_PORT=25565
RCON_PORT=25575
RCON_PASSWORD=your_secure_password
```

Start services:

```bash
docker compose up -d
```

Access the web interface:  
📍 http://localhost:3000

## 🖥️ Standalone (No Docker)

1. Install Node.js (v16+) and `npm`  
2. Install dependencies:

```bash
npm install
```

3. Configure `.env`  
4. Run:

```bash
npm start
```

## 🧩 Docker Compose Configuration

```yaml
version: '3'
services:
  minecraft:
    image: itzg/minecraft-server
    ports:
      - "25565:25565"
    environment:
      EULA: "TRUE"
      ENABLE_RCON: "true"
      RCON_PASSWORD: "${RCON_PASSWORD}"
    volumes:
      - ./minecraft-data:/data
    restart: unless-stopped

  webapp:
    build: .
    ports:
      - "3000:3000"
    environment:
      - MC_HOST=minecraft
      - MC_PORT=25565
      - RCON_PORT=25575
      - RCON_PASSWORD=${RCON_PASSWORD}
    depends_on:
      - minecraft
    restart: unless-stopped
```

## 🔄 Updating

```bash
git pull
docker compose down
docker compose up -d
```

## 🧰 Troubleshooting

### ❌ Connection Issues

- Ensure RCON password matches in all configs  
- Wait until the Minecraft server is fully initialized  
- Check logs:  

```bash
docker compose logs minecraft
```

### 🔁 Port Conflicts

- Adjust exposed ports in `docker-compose.yml`  
- Update `.env` accordingly  

## 🗂️ Project Structure

```
minecraft-manager/
├── website               # Frontend (dashboard)
├── docker-compose.yml   # Docker orchestration
└── .env.example         # Environment config template
```

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

## 📜 License

Licensed under the [MIT License](LICENSE).

## 🙌 Acknowledgments

- [minecraft-server-util](https://github.com/PassTheMayo/minecraft-server-util)  
- [rcon-client](https://github.com/janispritzkau/rcon-client)  
- [itzg/minecraft-server](https://github.com/itzg/docker-minecraft-server)
