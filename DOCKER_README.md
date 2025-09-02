# Docker Setup for LiveKit Meet (Next.js App Only)

This simplified Docker setup runs only the Next.js LiveKit Meet application. You'll need to provide your own LiveKit server.

## Quick Start

1. **Copy environment file:**
   ```bash
   cp .env.docker .env
   ```

2. **Update environment variables:**
   Edit `.env` file and provide your LiveKit server details:
   ```bash
   LIVEKIT_API_KEY=your-actual-api-key
   LIVEKIT_API_SECRET=your-actual-secret
   LIVEKIT_URL=wss://your-livekit-server.com
   ```

3. **Start the application:**
   ```bash
   docker compose up -d
   ```

4. **Access the application:**
   Open http://localhost:3000

## What You Need

### LiveKit Server
You'll need access to a LiveKit server. You can:

1. **Use LiveKit Cloud:**
   - Sign up at https://cloud.livekit.io/
   - Get your API key, secret, and WebSocket URL
   - Update the `.env` file with these values

2. **Self-hosted LiveKit:**
   - Run your own LiveKit server
   - Get the connection details from your server setup

3. **Local Development:**
   - Use the full Docker Compose setup with LiveKit server included
   - See the complete setup in git history if needed

### Environment Variables

Required variables in `.env`:
```bash
LIVEKIT_API_KEY=your-api-key
LIVEKIT_API_SECRET=your-api-secret
LIVEKIT_URL=wss://your-livekit-server.com  # or ws:// for non-SSL
```

## Development

### Building
```bash
docker compose build
```

### Viewing logs
```bash
docker compose logs -f meet-app
```

### Stopping
```bash
docker compose down
```

## Troubleshooting

### Connection Issues
If the app can't connect to LiveKit:
1. Check your `LIVEKIT_URL` format (wss:// for SSL, ws:// for non-SSL)
2. Verify your API key and secret are correct
3. Ensure your LiveKit server is accessible from the Docker container

### Build Issues
If Docker build fails:
1. Make sure Git LFS files are pulled: `git lfs pull`
2. Clear Docker cache: `docker compose build --no-cache`

## Production Notes

- Use HTTPS (wss://) URLs for production LiveKit servers
- Keep your API keys secure and don't commit them to git
- Consider using Docker secrets or other secure methods for sensitive data
- Make sure your LiveKit server can handle the expected load
