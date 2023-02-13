# Minimal Teamcity Sandbox Setup

- Runs Server on Ubuntu (WSL).
- Agents intended to be run separately on Windows.

## Usage

```
docker compose up -d
```

## Troubleshooting

### Teamcity is stuck updating versioned settings

Observed: After loading project settings from VCS, Teamcity gets stuck, for example "Resolving Maven dependencies..."

Solution: Disable VPN, shut down the container with `docker compose down` and start it again.