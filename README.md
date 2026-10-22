# Smitty MCP

Connect an assistant to SmittyHQ, the household record for family logistics.

**Hosted MCP endpoint:** https://mcp.smittyhq.com/mcp

This repository contains public connector documentation and configuration examples.
It does not contain the hosted server implementation or a self-hostable package.
No local server installation is required to use the hosted connector.

## Connect

1. Create or sign in to your account at [SmittyHQ](https://smittyhq.com).
2. In Muse, add `https://mcp.smittyhq.com/mcp` as a remote MCP server.
3. Complete the Smitty sign-in and permission flow for your adult account and household.
4. Ask your assistant to check connection capabilities before requesting an action.

Other clients need compatible remote MCP transport and OAuth support. Registration
is subject to Smitty's approved callback configuration; this documentation does not
promise compatibility with every MCP client. Do not use a permanent bearer token as
a substitute for the OAuth sign-in flow.

For a client-neutral connection description, see
[examples/connection.json](examples/connection.json). Its field names are descriptive;
use your client's own configuration format.

## What a connection can do

- Read shared events visible to the connected adult.
- Read recorded pickup responsibility and its current status.
- With granted permissions, service support and action approval, request pickup or
  drop-off, record the connected adult's own coverage, send supported coordination
  texts, and create shared events.

Available tools and permissions depend on the active service and connection.
[Capabilities and permissions](docs/capabilities.md) explains these boundaries.

## Privacy and consent

A connection belongs to one adult in one household. Another adult's private events
remain private. Families connect calendars and school sources in Smitty; the
assistant reads authorized information from Smitty.

The recipient confirms a requested pickup by replying to Smitty. A request is not
confirmed coverage. A queued text is not proof of delivery. Existing recipient
consent, household plan limits and service rules still apply.

Information shared with an assistant is also subject to that assistant provider's
policies. See Smitty's [security page](https://smittyhq.com/security),
[privacy policy](https://smittyhq.com/privacy), and
[terms](https://smittyhq.com/terms).

## Troubleshooting

- If connection setup fails, check the server URL and retry after the service is
  available. A published repository does not establish live service availability.
- If an action is unavailable, ask the assistant to check connection capabilities.
  Additional permissions require fresh consent; refreshing a token cannot add them.
- For account or connection help, contact [hello@smittyhq.com](mailto:hello@smittyhq.com).
  Do not post passwords, tokens, household details or private screenshots in public issues.

## Registry metadata

The connector identifier is `io.github.alisonc6/smitty`. [server.json](server.json)
prepares version `1.0.1` with the current public hostname. Updating this repository
does not publish a new version to an external registry; registry submission is a
separate step.

## Links

- [SmittyHQ](https://smittyhq.com)
- [Assistant setup](https://smittyhq.com/assistants)
- [Family source integrations](https://smittyhq.com/integrations)

## License

The documentation and examples in this repository are covered by the [MIT license](LICENSE).
That license applies only to material published here. Use of the hosted SmittyHQ
service remains subject to its own terms. SmittyHQ names and branding are not
licensed for use as an endorsement.
