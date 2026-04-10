# Help & Grow Expert Network — Multi-Agent Skill Package

A universal, adaptable, and scalable skill package that teaches your AI agent to interact with the **Help&Grow Expert Network** — a platform connecting users with verified domain experts for 1-on-1 consultations.

This package is designed following best practices for multi-agent interoperability. It is **fully compatible** with modern agentic frameworks, including:

- **Alibaba Cloud HiClaw / DashScope**
- **Google Cloud Scion / Vertex AI Agents**
- **OpenClaw & QClaw**
- **Hermes Agent Framework**
- **BytePlus (Coze / Similar Multi-Agent Frameworks)**
- **MCP (Model Context Protocol) Clients**

## What This Skill Does

By integrating this skill, your agent gains the ability to:
- **Search experts** by domain, keyword, or session type
- **Match experts** to complex user needs using natural language
- **View expert profiles** with bio, services, ratings, and pricing
- **Check availability** and find open time slots
- **Direct users to book** a consultation session directly

## Integration Guides

This repository provides multiple formats to ensure maximum compatibility across any framework.

### 1. OpenAPI Specification (Recommended for HiClaw, Scion, BytePlus, Hermes)
Most modern enterprise agent frameworks support importing tools directly via an OpenAPI specification. 

- **File**: [`openapi.yaml`](./openapi.yaml)
- **Usage**: 
  1. Go to your Agent Builder (e.g., Alibaba DashScope Plugins, BytePlus Coze Tools, or Google Vertex AI Extensions).
  2. Select "Import Tool from OpenAPI".
  3. Upload the `openapi.yaml` file from this repository.
  4. The framework will automatically generate the `getDomains`, `searchExperts`, `matchExperts`, `getExpertProfile`, and `getExpertAvailability` tools.

### 2. Model Context Protocol (MCP)
If you are using an MCP-compatible agent (like Claude Desktop or an MCP-enabled custom framework):
- The Help & Grow backend natively exposes an MCP server at `https://expert-network.vercel.app/api/mcp`.
- Connect your agent directly to the endpoint to dynamically load all available tools and schema updates.

### 3. OpenClaw / QClaw (Markdown Skill)
For lightweight markdown-based agents, use the standard `SKILL.md` file.

```bash
# Clone into your OpenClaw skills directory
git clone https://github.com/jlzxwt8/expert-network-skill.git ~/.openclaw/skills/expert-network
```
Or import via npm for WorkBuddy/CodeBuddy:
```bash
npx skills add jlzxwt8/expert-network-skill
```

## API Endpoints Overview

All endpoints are public (no authentication required) and return standardized JSON.

| Endpoint | Method | Description |
|---|---|---|
| `/api/v1/domains` | GET | List all available expertise domains |
| `/api/v1/experts` | GET | Search experts with filters (`q`, `domain`, `limit`) |
| `/api/v1/match` | GET | Natural language expert matching (AI-powered) |
| `/api/experts/{id}` | GET | Get full expert profile |
| `/api/experts/{id}/slots` | GET | Check real-time availability slots |

**Base URL**: `https://expert-network.vercel.app`

## Best Practices for Agent Prompts

When configuring your agent's system prompt to use these tools, include these instructions for the best user experience:

1. **Understand the Need**: Ask clarifying questions if the user's request is vague before searching.
2. **Prefer `/match` over `/experts`**: If the user describes a complex problem (e.g., "I need help scaling my B2B SaaS"), use the `matchExperts` tool instead of keyword search.
3. **Present Clearly**: When showing results, always include the expert's name, their primary domains, a 1-sentence bio summary, their rating, and their pricing.
4. **Always Provide Booking Links**: Append the expert's profile URL (`https://expert-network.vercel.app/experts/{id}`) so the user can easily book the session.

## License

MIT
