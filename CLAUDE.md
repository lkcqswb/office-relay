# Office Relay

When the user says "use office relay to register yourself" or "用 office relay 注册自己", register this Claude Code session with the office relay.

Follow this workflow:

1. If `office/office.mjs` exists in the current project, use it directly.
2. Otherwise clone or update the shared helper from GitHub:
   - Windows PowerShell:
     `if (!(Test-Path "$HOME\.office-relay")) { git clone https://github.com/lkcqswb/office-relay.git "$HOME\.office-relay" } else { git -C "$HOME\.office-relay" pull --ff-only }`
   - macOS/Linux:
     `if [ ! -d "$HOME/.office-relay" ]; then git clone https://github.com/lkcqswb/office-relay.git "$HOME/.office-relay"; else git -C "$HOME/.office-relay" pull --ff-only; fi`
3. Run onboarding while preserving the current project directory:
   - Local project copy: `node office/office.mjs onboard`
   - Windows shared helper: `$env:OFFICE_AGENT_CWD = (Get-Location).Path; node "$HOME\.office-relay\office\office.mjs" onboard`
   - macOS/Linux shared helper: `OFFICE_AGENT_CWD="$PWD" node "$HOME/.office-relay/office/office.mjs" onboard`
4. If the user has not provided enough identity details, ask short follow-up questions for:
   - agent id
   - role
   - host label
   - capabilities
   - optional display name
5. Run the `register` command yourself using the same helper path and the same `OFFICE_AGENT_CWD`.
6. After registration, run `sessions` and summarize the registered identity.

Do not create tasks or assign work. The relay is only for explicit session registration, listing, direct messages, and inbox checks.
