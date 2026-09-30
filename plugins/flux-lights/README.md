# Flux Lights for Claude

Connect Claude to **[Flux Lights](https://getfluxlights.com)**, the stage
lighting console, running on your computer. Claude reads your show — the
patch, cue lists, live channel values — tells you why a fixture is dark, and
proposes patch edits and cue lists. **Nothing changes until you press Apply
in Flux Lights.** Claude runs the show live (GO, grand master) only if you
switch that on for the show, and Flux Lights never lets it fire a cue that
strobes.

Works only with Flux Lights running **locally, on the same computer**. The
free version of Flux Lights is enough:
[download it](https://getfluxlights.com).

## What you can ask

- "Why is the front wash dark?" — Claude checks blackout, master, dimmer and
  colour, your plan's channel limit, the output, and whatever holds the
  fixture's channels (an effect, the pixel matrix, a parallel cue list).
- "What's in my show?" — fixtures, universes, cue lists and fades.
- "Add eight Chauvet SlimPAR Pro H on universe 2, starting at 1, and group
  them as 'Back wash'." — Claude finds the profile and sends the batch to
  Flux Lights, where you see every address before you apply it. Ctrl+Z
  undoes the whole batch.

- "Make a cue list for this setlist: …" — Claude builds a cue per song with
  colours, intensity, positions and your effect presets. You preview every cue
  on stage in Blind (the audience sees nothing) and apply the ones you want.
  Programming cue lists is part of Flux Lights Pro; Starter gets one list free.

## Set up Flux Lights

1. Start Flux Lights.
2. Open **Settings → AI assistant (MCP)** and turn it on.
3. Press **Copy token**. You paste it in the next step.

## Claude Code

```text
/plugin install flux-lights --marketplace Azelisi/flux-lights-claude
```

When asked, paste the token. Keep the port at 8091 unless you changed it in
Flux Lights. To change the token later: `/plugin` → Installed → Flux Lights →
Configure options, then `/mcp` → `plugin:flux-lights:flux-lights` → Reconnect.

## Claude Desktop

1. Download the extension:
   [getfluxlights.com/download/claude-desktop](https://getfluxlights.com/download/claude-desktop).
2. Open the downloaded `flux-lights.mcpb` — Claude Desktop offers to install
   it (or: Settings → Extensions → Install extension).
3. Paste the token into the extension's settings.

If Flux Lights isn't running when Claude starts, the extension still loads
and tells Claude what to switch on; it connects by itself once Flux Lights
is up.

## Privacy and safety

- The connection never leaves your computer: Flux Lights listens only on
  `127.0.0.1` and accepts only requests with your token.
- Every batch of edits waits for you in Flux Lights; the console shows exactly
  what will change, and the AI assistant log in Settings lists every request.
- Fixture and cue names come from your show file and are treated as data,
  not as instructions.

## Troubleshooting

| What Claude says                          | What to do                                                                                          |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Flux Lights is not reachable              | Start Flux Lights and turn on Settings → AI assistant (MCP). Check the port.                        |
| The access token was rejected             | Someone pressed New token. Copy the token again and paste it into the plugin or extension settings. |
| No Flux Lights tools at all (Claude Code) | `/mcp` → `plugin:flux-lights:flux-lights` → Reconnect (`flux-lights` if you added it by hand).      |

Support: [support@getfluxlights.com](mailto:support@getfluxlights.com)

## Licence

This plugin — its configuration, skill and documentation — is released under
the [MIT licence](LICENSE). The Flux Lights console itself is proprietary and
licensed separately under its [End User Licence Agreement](https://getfluxlights.com/legal/eula);
the Flux Lights name and logo are not covered by the MIT licence.
