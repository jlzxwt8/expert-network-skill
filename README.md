# Expert Network Skill

An [OpenClaw](https://docs.openclaw.ai/)-compatible skill for the **Help&Grow Expert Network** — a platform connecting users with verified domain experts for 1-on-1 consultations.

Works with **QClaw**, **WorkBuddy**, **OpenClaw**, and any AgentSkills-compatible AI agent.

## What It Does

This skill teaches your AI agent to:

- **Search experts** by domain, keyword, or session type
- **Match experts** to your needs using natural language descriptions
- **View expert profiles** with bio, services, ratings, and pricing
- **Check availability** and find open time slots
- **Direct you to book** a consultation session

### Available Domains

Marketing & BD · Headhunter · Law · Funding

## Install

### QClaw / OpenClaw

Import from GitHub in QClaw, or copy manually:

```bash
# Clone into your skills directory
git clone https://github.com/jlzxwt8/expert-network-skill.git ~/.openclaw/skills/expert-network
```

Then start a new session.

### WorkBuddy / CodeBuddy

```bash
npx skills add jlzxwt8/expert-network-skill
```

### Manual

Copy the `SKILL.md` file into your agent's skills directory.

## Usage

Once installed, just ask your agent naturally:

- "Find me a marketing expert"
- "I need help with fundraising for my Series A"
- "Show me experts available for online consultations"
- "Check if David has any open slots"

The agent will call the Expert Network API and present results with booking links.

## API Endpoints

The skill uses these public endpoints (no auth required):

| Endpoint | Description |
|---|---|
| `GET /api/v1/domains` | List all expertise domains |
| `GET /api/v1/experts?q=...&domain=...` | Search experts |
| `GET /api/v1/match?q=...` | Natural language expert matching |
| `GET /api/experts/{id}` | Get expert profile |
| `GET /api/experts/{id}/slots` | Check availability |

Base URL: `https://expert-network.vercel.app`

## Links

- **Platform**: https://expert-network.vercel.app
- **Source**: https://github.com/jlzxwt8/expert-network

## License

MIT
