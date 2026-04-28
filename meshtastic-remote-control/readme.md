# Meshtastic Remote Control — Home Assistant Blueprint

Trigger Home Assistant actions by sending text messages on a Meshtastic channel. Up to 8 commands per automation, each with its own trigger word, actions, and optional reply on the same channel.

## Requirements

- Home Assistant
- The official [Meshtastic integration](https://github.com/meshtastic/home-assistant)
- A Meshtastic gateway node connected to HA

## Installation

[![Open your Home Assistant instance and show the blueprint import dialog with this blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://raw.githubusercontent.com/d4mysus/ha_blueprints/refs/heads/main/meshtastic-remote-control/meshtastic_remote_control.yaml)
Or copy `meshtastic_remote_control.yaml` to `<config>/blueprints/automation/<your_name>/` and reload blueprints.

## Configuration

- **Gateway Node ID** — decimal node ID of the gateway connected to HA (find it in `data.data.gateway` of an incoming `meshtastic_api_text_message` event)
- **Channel Index** — slot 0–7 (0 is primary, custom channels start at 1)
- **Restrict to specific sender** — optional, set to 0 to accept any sender
- **Reply delay** — seconds before replying, 2–5 recommended

For each command slot: trigger word, actions, optional reply text. Empty trigger word disables the slot.

## Example

- Command 1 — Trigger: `on`, Action: turn on `light.living_room`, Reply: `Lamp is ON`
- Command 2 — Trigger: `off`, Action: turn off `light.living_room`, Reply: `Lamp is OFF`

## Troubleshooting

Check **Settings → Automations & Scenes → [your automation] → Traces** to see which condition failed and the actual values. Most common issue: using the sender's node ID instead of the gateway's.

## License

MIT
