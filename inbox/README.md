# Inbox

Mobile and async capture drop zone. Captured observations land here as markdown files; desktop sessions sweep periodically and route through Skill #00 to the appropriate store.

## File naming

`YYYY-MM-DD-HHMM-slug.md` — date with optional time and brief slug.

## Sweep procedure

1. List `inbox/` contents
2. For each file: read, run through Skill #00 (capture-and-route)
3. Append routed entry to `knowledge-base/synthesis-store.jsonl`
4. Move processed file to `inbox/archive/YYYY-MM/` or delete after confirmation
5. Commit with `[inbox-sweep]` prefix in message

Recommended cadence: weekly, or whenever the inbox has more than 5 unprocessed files.
