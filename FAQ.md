# TurboClaw FAQ

Frequently Asked Questions about TurboClaw - your personal digital intelligence agent.

## General Questions

### What is TurboClaw?

TurboClaw is a pre-configured digital agent powered by OpenClaw that provides personal and business assistance through multiple communication channels. It's designed to be a "zero-friction" installation experience - you can have a working AI agent in minutes instead of hours.

### How is TurboClaw different from ChatGPT or Claude?

While ChatGPT and Claude are AI models you chat with in a browser, TurboClaw is a complete agent system that:

- **Integrates with your life** - WhatsApp, email, calendar, files, phone calls
- **Runs locally** - On your Mac, with your data staying private
- **Has memory** - Remembers conversations and learns your preferences
- **Takes actions** - Can send emails, schedule meetings, manage files
- **Works offline** - Core functionality doesn't require constant internet
- **Has personality** - Customizable behavior and communication style

### Is TurboClaw free?

TurboClaw uses a freemium model:

- **CLI and basic features** - Free forever
- **macOS app** - Free with optional Pro features
- **LLM usage** - Pay-as-you-use through our managed proxy
- **Premium integrations** - Advanced business features require subscription

The managed LLM proxy typically costs 30-50% less than direct API access while providing better reliability and model selection.

### What languages does TurboClaw support?

TurboClaw has native support for:
- **English** (primary)
- **Polish** (full localization)
- **Spanish** (beta)
- **German** (beta)
- **French** (beta)

The agent can communicate in 50+ languages through the underlying LLM models, but the interface and setup are currently English/Polish only.

## Installation & Setup

### What are the system requirements?

- **macOS** 10.15+ (Catalina or newer)
- **Node.js** 18.0+ 
- **RAM** 4GB minimum, 8GB recommended
- **Storage** 2GB free space
- **Internet** Stable broadband connection

Windows and Linux support is planned for late 2024.

### Installation failed - what should I do?

Common solutions:

```bash
# Permission issues
sudo npm install -g turboclaw --unsafe-perm=true

# Node.js too old
nvm install node && nvm use node

# Network issues
npm config set registry https://registry.npmjs.org/
npm cache clean --force
```

If problems persist, check our [troubleshooting guide](USER_GUIDE.md#troubleshooting) or ask on Discord.

### Can I install TurboClaw without the macOS app?

Yes! The macOS app is optional:

```bash
# CLI-only installation
npm install -g turboclaw
turboclaw init --no-app

# Install app later if needed
turboclaw app install
```

The CLI provides full functionality - the app is just a prettier interface.

### How do I update TurboClaw?

```bash
# Update CLI
npm update -g turboclaw

# Update macOS app (if installed)
turboclaw app update

# Update configuration/skills
turboclaw update
```

Updates are released monthly with new features and security patches.

## Configuration

### How do I customize my agent's personality?

Use the personality wizard:

```bash
turboclaw personality wizard
```

Or edit directly (advanced):

```bash
turboclaw personality export > my-agent.yaml
# Edit the file
turboclaw personality import my-agent.yaml
```

You can adjust communication style, expertise areas, boundaries, and behavioral traits.

### Can I use my own OpenAI/Anthropic API keys?

Yes! While TurboClaw includes a managed LLM proxy, you can configure your own keys:

```bash
# Add your own API keys
turboclaw models add openai --key sk-your-key
turboclaw models add anthropic --key sk-ant-your-key

# Or use the managed proxy (recommended)
turboclaw models setup --managed
```

Using your own keys gives you more control but requires managing quotas, rate limits, and model availability yourself.

### Which LLM models should I use?

For different use cases:

- **Daily chat** - Claude Haiku (fast, cheap)
- **Complex analysis** - Claude Sonnet (balanced)
- **Creative writing** - Claude Opus (best quality)
- **Code assistance** - GPT-4 (strong programming)
- **Quick questions** - GPT-4o Mini (very fast)

The managed proxy automatically handles model selection and fallbacks.

### How do I connect WhatsApp?

WhatsApp integration uses WhatsApp Business API:

1. **Business account required** - Personal WhatsApp won't work
2. **Setup process**:
   ```bash
   turboclaw channel add whatsapp
   # Follow QR code instructions in terminal
   ```
3. **Verification** - WhatsApp may require business verification
4. **Limitations** - Some features require approved business account

For personal use, consider Discord or Telegram instead.

## Communication Channels

### What messaging platforms are supported?

**Fully supported:**
- WhatsApp Business
- Discord
- Slack
- Telegram
- iMessage (macOS only)

**Beta/experimental:**
- Microsoft Teams
- Signal (limited)
- SMS (via Twilio)

### Can my agent make phone calls?

Yes! With ElevenLabs + Twilio integration:

```bash
turboclaw voice setup
# Provide ElevenLabs and Twilio credentials

# Your agent gets a phone number for inbound/outbound calls
```

Features:
- Natural voice conversations
- Real-time responses
- Voicemail processing
- Call transcription and summaries

### How do I set up Discord integration?

1. **Create Discord bot** at [discord.com/developers](https://discord.com/developers)
2. **Get bot token**
3. **Add to TurboClaw**:
   ```bash
   turboclaw channel add discord --token YOUR_BOT_TOKEN
   ```
4. **Invite to servers** using the OAuth2 URL generator
5. **Configure permissions** - TurboClaw needs read/write message permissions

### Can multiple people use the same agent?

Yes, through several approaches:

- **Shared channels** - Everyone in a Discord server/Slack workspace
- **Multiple accounts** - Different WhatsApp numbers, same agent
- **Family mode** - One agent, multiple authorized users
- **Business teams** - Role-based access with different permission levels

Configure in the macOS app or via:
```bash
turboclaw users add user@example.com --role member
```

## Privacy & Security

### Where is my data stored?

TurboClaw follows a "local-first" approach:

- **Agent workspace** - Stored locally on your Mac
- **Conversation history** - Local SQLite database
- **Files and documents** - Local filesystem
- **Temporary processing** - Cloud LLMs (encrypted in transit)
- **Backups** - Optional encrypted cloud backups

Your personal data never leaves your device permanently unless you explicitly configure cloud integrations.

### Is TurboClaw GDPR compliant?

Yes! TurboClaw is built by a European company (Xfaang, Poland) with GDPR compliance as a core requirement:

- **Data minimization** - Only processes necessary data
- **Right to access** - Export all your data anytime
- **Right to erasure** - Complete data deletion on request
- **Consent management** - Clear opt-in/opt-out controls
- **Data portability** - Standard export formats
- **Breach notification** - Automated security monitoring

### Can TurboClaw access my files without permission?

No. TurboClaw uses explicit permission models:

- **Sandbox by default** - Limited to its own workspace
- **Explicit grants** - You approve each integration (email, calendar, etc.)
- **Scope controls** - Granular permissions (read-only, specific folders)
- **Audit logging** - Complete record of all file access
- **Revocable access** - Disable permissions anytime

The macOS app shows real-time permission status.

### What happens if I uninstall TurboClaw?

```bash
# Clean uninstall (keeps your data)
turboclaw uninstall

# Complete removal (deletes all data)
turboclaw uninstall --purge
```

Without `--purge`, your agent workspace is preserved so you can reinstall later without losing conversations or configurations.

## Features & Capabilities

### What can TurboClaw actually do?

**Communication:**
- Send/receive messages across platforms
- Voice calls with natural conversation
- Email management and drafting
- Meeting scheduling and reminders

**Productivity:**
- Document analysis and summarization
- Task and project management
- Calendar and schedule optimization
- File organization and search

**Development:**
- Code review and suggestions
- Bug tracking and resolution
- Deployment automation
- Documentation generation

**Research & Analysis:**
- Web search and information gathering
- Data analysis and visualization
- Report writing and formatting
- Competitive intelligence

**Creative Work:**
- Content writing and editing
- Social media management
- Design feedback and suggestions
- Creative brainstorming

### Can TurboClaw learn and remember things about me?

Yes! TurboClaw has several memory systems:

- **Short-term** - Current conversation context
- **Session memory** - Remembers within each chat session
- **Personal memory** - Learns your preferences, habits, and background
- **Knowledge base** - Accumulates information you want to remember
- **Skills memory** - Improves at tasks through repetition

Memory is stored locally and can be reviewed/edited through the app.

### Does TurboClaw work offline?

Partially:

- **Core functions** - File management, scheduling, local tasks
- **Cached responses** - Common questions answered locally
- **Offline models** - Optional local LLM integration (beta)
- **Sync on reconnect** - Queues actions when offline

Full AI capabilities require internet for LLM access, but TurboClaw gracefully degrades when offline.

### Can I create custom commands or skills?

Yes! TurboClaw has an extensible skill system:

```bash
# Install community skills
turboclaw skills install weather-api
turboclaw skills install code-reviewer

# Create custom skill
turboclaw skills create my-skill --template basic

# Publish for others
turboclaw skills publish my-skill
```

Skills are Node.js modules with access to TurboClaw's full API.

## Business & Enterprise

### Is TurboClaw suitable for business use?

Absolutely! TurboClaw is designed for both personal and business use:

**Small businesses:**
- Customer service automation
- Social media management
- Basic CRM functions
- Appointment scheduling

**Enterprise features:**
- Team collaboration
- Advanced integrations (Salesforce, HubSpot, etc.)
- Role-based access control
- Compliance reporting
- SSO integration

### What about compliance and data governance?

Enterprise TurboClaw includes:

- **SOC 2 compliance** - Third-party security audit
- **HIPAA compliance** - Healthcare data protection (paid tier)
- **Audit trails** - Complete activity logging
- **Data retention policies** - Automated cleanup
- **Access controls** - Granular permissions
- **Encryption** - At rest and in transit

Contact enterprise@xfaang.com for compliance documentation.

### Can I integrate TurboClaw with our existing systems?

Yes! Common enterprise integrations:

- **CRM** - Salesforce, HubSpot, Pipedrive
- **Communication** - Slack, Teams, Zoom
- **Documentation** - Notion, Confluence, SharePoint
- **Development** - GitHub, GitLab, Jira
- **Analytics** - Tableau, PowerBI, Looker

Custom integrations available through our Professional Services team.

### What's the pricing for business use?

**Starter** ($49/month):
- 5 team members
- Basic integrations
- Standard support

**Professional** ($149/month):
- 25 team members
- Advanced integrations
- Priority support
- Custom skills

**Enterprise** (custom pricing):
- Unlimited users
- On-premise deployment
- Dedicated support
- Custom development

## Technical Questions

### What technology stack does TurboClaw use?

- **Core** - Node.js, TypeScript
- **Database** - SQLite (local), PostgreSQL (cloud features)
- **UI** - Electron (macOS app), React
- **AI Models** - Anthropic Claude, OpenAI GPT, Google Gemini
- **Communication** - WebRTC, WebSocket, REST APIs
- **Security** - TLS 1.3, AES-256 encryption, RSA 4096

### Can I run TurboClaw on a server?

Yes! TurboClaw supports headless server deployment:

```bash
# Server installation
npm install -g turboclaw
turboclaw init --headless --port 3000

# Docker deployment
docker run -d -p 3000:3000 turboclaw/server
```

Perfect for running your agent on a VPS, Raspberry Pi, or cloud server.

### How does the managed LLM proxy work?

TurboClaw's managed proxy provides:

- **Model abstraction** - Single API for multiple providers
- **Automatic failover** - Switches providers if one is down
- **Cost optimization** - Routes to cheapest suitable model
- **Rate limit management** - Handles quotas automatically
- **Caching** - Reduces duplicate requests
- **Analytics** - Usage tracking and optimization

You pay only for successful requests, with no setup fees or minimum commitments.

### Can I contribute to TurboClaw development?

Yes! TurboClaw is built on open-source OpenClaw:

- **OpenClaw** - MIT licensed core engine
- **TurboClaw** - Proprietary UX layer, but contributions welcome
- **Skills** - Community-driven skill marketplace
- **Documentation** - Always needs improvement

Check [CONTRIBUTING.md](CONTRIBUTING.md) for development setup and guidelines.

## Troubleshooting

### My agent isn't responding

**Check system status:**
```bash
turboclaw status
turboclaw logs --follow
```

**Common fixes:**
```bash
# Restart services
turboclaw restart

# Clear caches
turboclaw cache clear

# Reset configuration
turboclaw config reset
```

### Channels keep disconnecting

**Refresh tokens:**
```bash
turboclaw channels refresh
turboclaw channels test all
```

**Check permissions:**
- WhatsApp: Business account verified?
- Discord: Bot has correct permissions?
- Slack: Workspace admin approved?

### High API costs

**Monitor usage:**
```bash
turboclaw usage stats --detailed
turboclaw usage top-models
```

**Optimize costs:**
```bash
# Set spending limits
turboclaw usage limit --daily 10 --monthly 100

# Switch to cheaper models
turboclaw models set-default claude-haiku

# Enable caching
turboclaw config set cache.enabled true
```

### Performance issues

**System monitoring:**
```bash
turboclaw monitor --cpu --memory --network
```

**Optimization:**
```bash
# Clear old data
turboclaw cleanup --older-than 30d

# Optimize database
turboclaw database optimize

# Reduce memory usage
turboclaw config set memory.limit 2GB
```

## Getting More Help

### Where can I get support?

**Free Support:**
- [Discord Community](https://discord.gg/turboclaw) - Fastest response
- [GitHub Issues](https://github.com/TurboClawHQ/turboclaw/issues) - Bug reports
- [Documentation](https://turboclaw.eu/docs) - Comprehensive guides

**Paid Support:**
- **Email** - support@xfaang.com (48h response)
- **Priority** - priority-support@xfaang.com (4h response, paid customers)
- **Custom Development** - enterprise@xfaang.com

### How can I provide feedback?

We love feedback! Share through:

- **Discord** - #feedback channel
- **GitHub** - Feature requests and issues
- **Email** - feedback@xfaang.com
- **Twitter/X** - [@TurboClaw](https://twitter.com/turboclaw)

### What's on the roadmap?

**Q2 2024:**
- Windows and Linux support
- Advanced automation workflows
- Mobile app (iOS/Android)

**Q3 2024:**
- Multi-agent collaboration
- Advanced integrations (CRM, ERP)
- Voice-first interactions

**Q4 2024:**
- Edge deployment options
- Industry-specific agents
- Advanced analytics

Check [turboclaw.eu/roadmap](https://turboclaw.eu/roadmap) for the latest updates.

---

*Don't see your question here? Ask in our [Discord community](https://discord.gg/turboclaw) or email support@xfaang.com.*