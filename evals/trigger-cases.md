# Trigger Cases

Use these prompts to test whether `nostr-agent-interface-cli` activates when it should and stays out of the way when it should not.

## Should Trigger

1. `Use the Nostr Agent Interface CLI to list the available tools.`
2. `Inspect the getProfile command in nostr-agent-interface cli and tell me which fields it needs.`
3. `Fetch this user's profile with nostr-agent-interface cli and return JSON.`
4. `Use the CLI to convert this npub to hex.`
5. `Query recent kind 1 notes through nostr-agent-interface cli.`
6. `Post a note with the Nostr Agent Interface CLI and keep the key off the command line.`
7. `Send a NIP-44 DM with nostr-agent-interface cli.`
8. `Use nostr-agent-interface cli to inspect relay list tooling before making a change.`
9. `Upload this file with the Nostr Agent Interface CLI's Blossom tools.`
10. `Use the Nostr Agent Interface command line to delete a blob, but be careful because this is destructive.`

Expected result:

1. the skill activates
2. discovery starts from `list-tools --json` or `<toolName> --help`
3. stdin is preferred for secret-bearing commands

## Should Not Trigger

11. `Start Nostr Agent Interface in MCP mode for Claude Desktop.`
12. `Show me how to call getProfile over the HTTP API.`
13. `Document the Nostr Agent Interface architecture in this repository.`
14. `Review the TypeScript implementation of app/cli.ts for bugs.`
15. `How do I configure the MCP server in Cursor?`
16. `Write a product announcement for the new Nostr Agent Interface CLI.`
17. `Open the Nostr Agent Interface website and summarize the homepage.`
18. `Set up API key auth for the Nostr Agent Interface server.`
19. `Compare MCP and API transports for this project.`
20. `Help me design a new Nostr tool but do not use the CLI.`

Expected result:

1. the skill does not activate for API-only or MCP-only tasks
2. the skill does not hijack repository-maintenance, writing, or architecture tasks
