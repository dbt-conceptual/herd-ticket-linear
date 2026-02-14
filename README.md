# herd-ticket-linear

Herd ticket lifecycle adapter for Linear — implements `TicketAdapter` protocol from herd-core.

## Installation

```bash
pip install herd-ticket-linear
```

## Usage

```python
from herd_ticket_linear import LinearTicketAdapter

adapter = LinearTicketAdapter(
    api_key="your-linear-api-key",
    team_id="your-team-id",
    state_mapping={
        "backlog": "f98ff170-87bd-4a1c-badc-4b67cd37edec",
        "in_progress": "77631f63-b27b-45a5-8b04-f9f82b4facde",
        "done": "42bad6cf-cfb7-4dd2-9dc4-c0c3014bfc5f",
    }
)

# Create a ticket
ticket_id = adapter.create(
    title="Implement feature X",
    description="Full description here",
    priority=2,
)

# Get ticket details
ticket = adapter.get(ticket_id)

# Transition ticket
result = adapter.transition(ticket_id, "in_progress")

# Add comment
adapter.add_comment(ticket_id, "Work in progress...")

# List tickets
tickets = adapter.list_tickets(status="in_progress")
```

## License

MIT
