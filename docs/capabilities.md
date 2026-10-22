# Capabilities and permissions

Use `get_connection_capabilities` to check what the current connection is allowed
to do. Use the live tool descriptions and schemas for exact arguments and supported
actions; this document is a guide rather than a complete protocol schema.

| Tool | Purpose |
| --- | --- |
| `get_connection_capabilities` | Check connection permissions and whether writes are enabled. |
| `find_pickup_events` | Look up upcoming shared events relevant to pickup planning. |
| `get_events_for_day` | Look up events for a selected day within the connected adult's visibility. |
| `get_responsibility` | Read recorded responsibility and coordination status. |
| `request_pickup` | Request initial pickup coverage, when authorized and supported. |
| `request_drop_off` | Request initial drop-off coverage, when authorized and supported. |
| `commit_coverage` | Record the connected adult's own pickup or drop-off coverage. |
| `send_coordination_message` | Send an approved, supported coordination message. |
| `create_shared_event` | Create an approved shared household event. |
| `rsvp_shared_event` | Record a supported RSVP for the connected adult. |

Tools require appropriate grants. Common permissions include `events:read`,
`responsibility:read`, `pickup:request`, `drop_off:request`, `message:send` and
`event:create`. The consent flow and live capabilities determine the permissions
offered and granted. Existing connections may need fresh consent for new permissions.

## Action handling

- Check the current event and responsibility before proposing a coordination action.
- Obtain approval for the exact event or message being created or sent.
- The other adult's acceptance must come from that adult through Smitty.
- Read back the recorded result; do not infer acceptance or delivery from a queued request.
- Reuse action identifiers when retrying. If an event was created but its text failed,
  report those outcomes separately instead of creating another event.

Public access to the connector endpoint does not grant access to household data.
OAuth authentication, connection permissions and service rules apply to tool calls.
