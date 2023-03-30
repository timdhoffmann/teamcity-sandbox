# Minimal Teamcity Sandbox Setup

- Runs Server on Ubuntu (WSL).
- Agents intended to be run separately on Windows.

## Prerequisites

- JDK 1.8 installed on the machine running the agent.

```bash
choco install corretto8jdk
```

## Usage

- Start server from repository root on Linux.

```
docker compose up -d
```

- Open `localhost:8112` in your browser.
- Go through initial setup if running for the first time.
- Navigate to _Administration > Install Build Agents > Full zip file distribution_ and download.
- Extract to local directory (Windows).
- Navigate to extracted directory.
- Rename buildAgent.dist.properties to buildAgent.properties.
- Edit the file and change the server adress to the adress above.
- Start the agent.

```pwsh
.\bin\agent.bat start
```

## Troubleshooting

### Teamcity is stuck updating versioned settings

Observed: After loading project settings from VCS, Teamcity gets stuck, for example "Resolving Maven dependencies..."

Solution: Disable VPN, shut down the container with `docker compose down` and start it again.
