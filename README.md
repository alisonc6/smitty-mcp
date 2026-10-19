# SmittyHQ

Family calendars, tasks, reminders, and pickup coordination for your AI assistant.

## Registry entry

- Name: `io.github.alisonc6/smitty`
- Title: SmittyHQ
- Version: `1.0.0`
- Website: https://smittyhq.com/assistants
- Transport: `streamable-http`
- Endpoint: https://smitty-mcp-spike-production.up.railway.app/mcp

[`server.json`](server.json) contains the published registry metadata. Its name, title, description, version, website URL, and remote endpoint match the registry entry exactly.

## What it does

SmittyHQ keeps the household record for a connected assistant. Available tools read shared events and pickup responsibilities, request pickup or drop-off coordination, send supported coordination messages, and create events, subject to granted permissions and enabled features. A pending request is not confirmed coverage; the other adult must answer Smitty directly.

## How to connect

Access is currently a restricted pilot, not open self-service. A registry listing does not automatically enable access for a new household or assistant client. Contact [hello@smittyhq.com](mailto:hello@smittyhq.com) to arrange access and client configuration.

For an approved household and client:

1. Add a remote MCP server in your assistant using Streamable HTTP and the endpoint above.
2. Complete the SmittyHQ OAuth sign-in and consent flow. The connection is for one adult in one household.
3. Review the requested read and write permissions before connecting. Available actions depend on the permissions you grant and the features enabled for your household.
4. Start with a shared-calendar question, such as “What shared events do we have tomorrow?”

Use the `/mcp` endpoint, not the website URL. Requests require OAuth authentication; an unauthenticated request returns HTTP 401. Never put account credentials or access tokens in `server.json`, an issue, or this repository.

## Privacy and permissions

SmittyHQ checks the connected adult and household on each request. The assistant can read shared plans that adult is allowed to see; another adult's private events stay private. Write actions can change records or send coordination messages when authorized. Messaging also requires the recipient's consent and the applicable product checks.

Information returned by a tool is shared with the assistant service you connect. Review that service's privacy practices as well as SmittyHQ's policies. Disconnecting the assistant stops future authorized access; it does not erase information already returned to that service.

- Privacy policy: https://smittyhq.com/privacy
- Security and privacy overview: https://smittyhq.com/security
- Connection documentation: https://smittyhq.com/assistants
- Support: https://smittyhq.com/contact or [hello@smittyhq.com](mailto:hello@smittyhq.com)
- Privacy questions: [privacy@smittyhq.com](mailto:privacy@smittyhq.com)

## Keeping this listing current

When publishing a new registry version, update `server.json` and the registry details above together. This repository contains public connection documentation and metadata only; the SmittyHQ application source is maintained separately.
