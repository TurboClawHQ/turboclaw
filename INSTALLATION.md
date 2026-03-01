# TurboClaw Installation Guide

Complete step-by-step instructions for installing and configuring your TurboClaw digital agent.

## System Requirements

- **macOS**: 10.15+ (Catalina or newer)
- **Node.js**: 18.0+ 
- **RAM**: 4GB minimum, 8GB recommended
- **Storage**: 2GB free space
- **Network**: Stable internet connection

## Quick Installation

### Method 1: One-Command Setup (Recommended)

```bash
npm install -g turboclaw
turboclaw init
```

This will:
1. Install TurboClaw globally
2. Create your agent workspace
3. Download the native macOS app
4. Launch the personality wizard

### Method 2: Manual Setup

If you prefer more control over the process:

```bash
# 1. Install TurboClaw CLI
npm install -g turboclaw

# 2. Create workspace directory
mkdir ~/my-agent && cd ~/my-agent

# 3. Initialize configuration
turboclaw init --manual

# 4. Download macOS app (optional)
turboclaw app install
```

## First-Time Configuration

### 1. Personality Wizard

After installation, the personality wizard will guide you through 8 steps:

1. **Agent Name** - What should your agent be called?
2. **Personality Type** - Professional, Creative, Friendly, or Custom
3. **Communication Style** - Formal, Casual, Technical, or Balanced
4. **Languages** - Primary and secondary languages
5. **Expertise Areas** - What should your agent specialize in?
6. **Boundaries** - What can/cannot your agent do?
7. **Voice & Tone** - How should your agent sound?
8. **Review & Deploy** - Confirm and activate

### 2. Channel Setup

Connect your agent to communication platforms:

#### WhatsApp Business
```bash
turboclaw channel add whatsapp
# Follow QR code instructions
```

#### Discord
```bash
turboclaw channel add discord --token your_bot_token
```

#### Slack
```bash
turboclaw channel add slack --token your_slack_token
```

#### Telegram
```bash
turboclaw channel add telegram --token your_bot_token
```

### 3. LLM Configuration

TurboClaw includes a pre-configured LLM proxy, but you can customize:

```bash
# Use default managed models (recommended)
turboclaw models setup --managed

# Or configure your own API keys
turboclaw models add anthropic --key your_anthropic_key
turboclaw models add openai --key your_openai_key
```

## macOS App

The native TurboClaw app provides:

- **Dashboard** - System status, conversation history
- **Agent Controls** - Start/stop, configuration
- **Channel Manager** - Connect/disconnect platforms
- **Logs Viewer** - Real-time debugging
- **Performance Monitor** - Usage stats and costs

### App Installation
```bash
# Install automatically during init
turboclaw init

# Or install separately
turboclaw app install

# Launch app
open /Applications/TurboClaw.app
```

## Verification

Test your installation:

```bash
# Check system status
turboclaw status

# Test agent response
turboclaw chat "Hello, are you working?"

# Verify channels
turboclaw channels list

# Check models
turboclaw models status
```

## Troubleshooting

### Common Issues

**Installation fails with permission errors:**
```bash
sudo npm install -g turboclaw --unsafe-perm=true
```

**Node.js version too old:**
```bash
# Install latest Node.js from nodejs.org
# Or use nvm:
nvm install node && nvm use node
```

**macOS app won't open:**
```bash
# Allow unsigned apps (if needed)
sudo spctl --master-disable
# Then try opening the app again
```

**Channels not connecting:**
```bash
# Reset channel configuration
turboclaw channels reset
turboclaw init --channels-only
```

**Agent not responding:**
```bash
# Check service status
turboclaw status

# Restart services
turboclaw restart

# Check logs
turboclaw logs --follow
```

## Updates

Keep TurboClaw updated:

```bash
# Update CLI
npm update -g turboclaw

# Update macOS app
turboclaw app update

# Update agent configuration
turboclaw update
```

## Uninstallation

To completely remove TurboClaw:

```bash
# Stop all services
turboclaw stop

# Uninstall CLI
npm uninstall -g turboclaw

# Remove app
rm -rf /Applications/TurboClaw.app

# Remove workspace (optional - contains your data!)
rm -rf ~/my-agent
```

## Next Steps

- Read the [User Guide](USER_GUIDE.md) for detailed usage instructions
- Check the [FAQ](FAQ.md) for common questions
- Join our Discord for community support

## Support

- **Documentation**: [turboclaw.eu/docs](https://turboclaw.eu/docs)
- **Discord**: [discord.gg/turboclaw](https://discord.gg/turboclaw) 
- **Email**: support@xfaang.com
- **GitHub Issues**: [TurboClawHQ/turboclaw](https://github.com/TurboClawHQ/turboclaw/issues)