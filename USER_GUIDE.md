# TurboClaw User Guide

Your complete guide to using TurboClaw effectively - from basic commands to advanced automation.

## Table of Contents

1. [Getting Started](#getting-started)
2. [Basic Commands](#basic-commands)
3. [Personality & Behavior](#personality--behavior)
4. [Communication Channels](#communication-channels)
5. [File Management](#file-management)
6. [Integrations](#integrations)
7. [Automation](#automation)
8. [Use Cases](#use-cases)
9. [Security & Privacy](#security--privacy)
10. [Troubleshooting](#troubleshooting)

## Getting Started

### Your First Interaction

Once TurboClaw is installed and configured, you can interact with your agent through:

- **macOS App** - Native dashboard with chat interface
- **Terminal** - Direct CLI commands
- **WhatsApp/Discord/Slack** - Connected messaging platforms
- **Phone** - Voice calls (if configured)

### Basic Interaction

```bash
# Chat with your agent
turboclaw chat "What can you help me with?"

# Ask for help
turboclaw chat "How do I set up email integration?"

# Get system status
turboclaw status
```

## Basic Commands

### Chat Commands

```bash
# Start interactive chat session
turboclaw chat

# Send single message
turboclaw chat "your message here"

# Chat with specific model
turboclaw chat --model claude-sonnet "analyze this data"
```

### System Commands

```bash
# Check agent status
turboclaw status

# View running processes
turboclaw ps

# Restart agent services
turboclaw restart

# Stop all services
turboclaw stop

# View logs
turboclaw logs
turboclaw logs --follow  # real-time
```

### Configuration Commands

```bash
# View current config
turboclaw config

# Edit configuration
turboclaw config edit

# Reset to defaults
turboclaw config reset
```

## Personality & Behavior

### Using the Personality Wizard

Access through the macOS app or command line:

```bash
turboclaw personality wizard
```

### Key Personality Settings

**Communication Style:**
- **Professional** - Formal, structured responses
- **Casual** - Conversational, friendly tone
- **Technical** - Detailed, precise explanations
- **Creative** - Imaginative, expressive responses

**Expertise Areas:**
- Software development
- Business analysis
- Creative writing
- Research assistance
- Project management
- Data analysis

**Behavioral Boundaries:**
- What tasks to accept/decline
- Information sharing policies
- External service permissions
- Automation limits

### Custom Personality Files

Advanced users can directly edit personality files:

```bash
# View current personality
turboclaw personality show

# Export for editing
turboclaw personality export > my-personality.yaml

# Import custom personality
turboclaw personality import my-personality.yaml
```

## Communication Channels

### WhatsApp Business

Perfect for personal assistance and mobile interaction:

```bash
# Setup WhatsApp
turboclaw channel add whatsapp
# Scan QR code with WhatsApp Business app

# Test connection
turboclaw channel test whatsapp
```

**WhatsApp Features:**
- Text messages and voice notes
- Image analysis
- Document processing
- Location sharing
- Contact management

### Discord Integration

Ideal for community and team environments:

```bash
# Add Discord bot
turboclaw channel add discord --token YOUR_BOT_TOKEN

# Configure server permissions
turboclaw channel config discord --guilds server_id_1,server_id_2
```

**Discord Features:**
- Multi-server support
- Role-based permissions
- Slash commands
- File sharing
- Voice channel participation

### Slack Integration

Enterprise-focused team collaboration:

```bash
# Connect to Slack workspace
turboclaw channel add slack --token YOUR_SLACK_TOKEN

# Configure channels
turboclaw channel config slack --channels general,dev-team
```

### Phone Calls (ElevenLabs + Twilio)

Voice interaction capabilities:

```bash
# Setup voice agent
turboclaw voice setup
# Provide ElevenLabs and Twilio credentials

# Test voice capability
turboclaw voice test
```

## File Management

### Document Processing

```bash
# Analyze document
turboclaw file analyze document.pdf

# Extract text
turboclaw file extract document.pdf > extracted.txt

# Convert format
turboclaw file convert document.docx --to pdf
```

### Workspace Organization

```bash
# View workspace files
turboclaw files list

# Search files by content
turboclaw files search "keyword"

# Archive old files
turboclaw files archive --older-than 30d
```

### Cloud Storage

Connect to cloud services:

```bash
# Google Drive
turboclaw cloud add gdrive
turboclaw cloud sync gdrive ~/Documents

# OneDrive
turboclaw cloud add onedrive
turboclaw cloud sync onedrive ~/Work
```

## Integrations

### Email (Gmail/Outlook)

```bash
# Setup email integration
turboclaw integration add gmail
# Follow OAuth flow

# Check emails
turboclaw email check

# Send email through agent
turboclaw email send --to user@example.com --subject "Meeting" --body "Let's meet tomorrow"
```

### Calendar Management

```bash
# Connect calendar
turboclaw integration add google-calendar

# View today's events
turboclaw calendar today

# Schedule meeting
turboclaw calendar add "Team meeting" --date "2024-03-15" --time "14:00"
```

### Project Management

```bash
# Connect to GitHub
turboclaw integration add github --token YOUR_TOKEN

# Track issues
turboclaw github issues --repo myproject

# Connect to Notion
turboclaw integration add notion --token YOUR_TOKEN
```

### Development Tools

```bash
# Code analysis
turboclaw code review src/

# Run tests
turboclaw code test

# Deploy application
turboclaw code deploy --environment production
```

## Automation

### Scheduled Tasks

```bash
# Daily email summary
turboclaw schedule add "email summary" --daily --time "09:00"

# Weekly reports
turboclaw schedule add "weekly report" --weekly --day monday --time "10:00"

# Custom cron jobs
turboclaw schedule add "backup files" --cron "0 2 * * *"
```

### Workflow Automation

Create complex automation workflows:

```yaml
# workflows/daily-routine.yaml
name: "Daily Routine"
trigger:
  schedule: "0 8 * * *"  # 8 AM daily
steps:
  - check_emails
  - review_calendar
  - generate_summary
  - send_to_slack
```

```bash
# Load workflow
turboclaw workflow add daily-routine.yaml

# List workflows
turboclaw workflow list

# Run workflow manually
turboclaw workflow run "Daily Routine"
```

### Smart Notifications

Set up intelligent alerts:

```bash
# Important email detection
turboclaw notify setup email --priority high --keywords "urgent,deadline"

# Calendar reminders
turboclaw notify setup calendar --before 15min

# System monitoring
turboclaw notify setup system --cpu 80% --memory 90%
```

## Use Cases

### 1. Personal Assistant

**Daily routine management:**
- Morning briefing with weather, calendar, emails
- Smart reminders for tasks and deadlines
- Evening summary of the day's activities

```bash
# Setup morning routine
turboclaw routine add morning "weather, calendar today, email summary"
```

### 2. Business Operations

**Customer support:**
- Automated responses to common queries
- Ticket categorization and routing
- Follow-up scheduling

**Sales assistance:**
- Lead qualification
- Meeting scheduling
- Proposal generation

### 3. Content Creation

**Writing assistance:**
- Blog post drafting
- Social media content
- Email copywriting
- Documentation generation

```bash
# Generate blog post
turboclaw content create blog --topic "AI in Healthcare" --length 1500
```

### 4. Research & Analysis

**Data processing:**
- Document analysis
- Market research compilation
- Competitive analysis
- Report generation

```bash
# Analyze research documents
turboclaw research analyze papers/ --output summary.md
```

### 5. Development Support

**Code assistance:**
- Code review and suggestions
- Bug tracking and resolution
- Documentation updates
- Deployment automation

```bash
# Code review
turboclaw code review --pr 123 --repo myproject
```

### 6. Learning & Education

**Knowledge management:**
- Course material organization
- Quiz generation
- Progress tracking
- Resource recommendations

## Security & Privacy

### Data Protection

TurboClaw implements multiple security layers:

- **Local Processing** - Sensitive data stays on your device
- **Encrypted Communication** - All channels use TLS/SSL
- **Access Controls** - Role-based permissions
- **Audit Logging** - Complete activity tracking

### Privacy Settings

```bash
# View privacy settings
turboclaw privacy status

# Configure data retention
turboclaw privacy retention --days 90

# Export personal data
turboclaw privacy export

# Delete personal data
turboclaw privacy delete --confirm
```

### Access Control

```bash
# Manage user permissions
turboclaw users add colleague@company.com --role read-only

# API key management
turboclaw keys list
turboclaw keys rotate --service anthropic

# Security audit
turboclaw security audit
```

## Troubleshooting

### Performance Issues

**Agent responding slowly:**
```bash
# Check system resources
turboclaw monitor resources

# Optimize memory usage
turboclaw optimize memory

# Clear caches
turboclaw cache clear
```

**High API costs:**
```bash
# View usage statistics
turboclaw usage stats --month

# Set spending limits
turboclaw usage limit --monthly 100

# Switch to cheaper models
turboclaw models set-default claude-haiku
```

### Connection Problems

**Channels disconnecting:**
```bash
# Refresh channel tokens
turboclaw channels refresh

# Reset channel configuration
turboclaw channels reset discord

# Test connectivity
turboclaw channels test all
```

**Model access issues:**
```bash
# Verify API keys
turboclaw models verify

# Test model endpoints
turboclaw models test anthropic

# Switch fallback models
turboclaw models fallback claude-haiku
```

### Data Issues

**Workspace corruption:**
```bash
# Backup current workspace
turboclaw backup create

# Restore from backup
turboclaw backup restore --date 2024-03-01

# Reset workspace
turboclaw workspace reset
```

## Advanced Features

### Custom Skills

Create specialized capabilities:

```bash
# Install community skill
turboclaw skills install weather-forecast

# Create custom skill
turboclaw skills create my-skill --template basic

# Publish skill
turboclaw skills publish my-skill
```

### Multi-Agent Collaboration

Set up agent teams:

```bash
# Create agent cluster
turboclaw cluster create team-alpha

# Add specialized agents
turboclaw cluster add team-alpha research-agent
turboclaw cluster add team-alpha writing-agent

# Coordinate tasks
turboclaw cluster task "research competitor analysis" --assign research-agent
```

### API Development

Build on TurboClaw:

```bash
# Start API server
turboclaw api start --port 3000

# Generate API documentation
turboclaw api docs

# Test endpoints
turboclaw api test
```

## Getting Help

### Documentation

- **Official Docs**: [turboclaw.eu/docs](https://turboclaw.eu/docs)
- **API Reference**: [turboclaw.eu/api](https://turboclaw.eu/api)
- **Video Tutorials**: [youtube.com/turboclaw](https://youtube.com/turboclaw)

### Community Support

- **Discord Server**: [discord.gg/turboclaw](https://discord.gg/turboclaw)
- **GitHub Discussions**: [github.com/TurboClawHQ/turboclaw/discussions](https://github.com/TurboClawHQ/turboclaw/discussions)
- **Reddit**: [r/TurboClaw](https://reddit.com/r/TurboClaw)

### Professional Support

- **Email**: support@xfaang.com
- **Priority Support**: Available for business customers
- **Custom Development**: enterprise@xfaang.com

---

*This guide covers the fundamentals of TurboClaw. For advanced topics and latest features, check our [online documentation](https://turboclaw.eu/docs).*