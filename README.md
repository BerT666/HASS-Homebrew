# HASS-Homebrew

Home Assistant blueprints for fermentation chamber temperature control — heating, cooling, and a sensor fail-safe, built for homebrew/mead/wine setups but usable with any temperature sensor and switch entities.

## Blueprints

| Blueprint | What it does | Import |
|---|---|---|
| **Heater Control** | Turns a heating actuator on/off around a target temperature, with hysteresis and a backup check. | [![Open your Home Assistant instance and show the blueprint import dialog.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2FBerT666%2FHASS-Homebrew%2Fmain%2Ffermentation_heater_control.yaml) |
| **Cooler Control** | Turns a cooling actuator (e.g. a compressor) on/off around a target temperature, with hysteresis plus minimum runtime/pause to protect the compressor. | [![Open your Home Assistant instance and show the blueprint import dialog.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2FBerT666%2FHASS-Homebrew%2Fmain%2Ffermentation_cooler_control.yaml) |
| **Sensor Watchdog** | Turns off actuators and notifies you if the temperature sensor goes stale (unavailable/unknown), and notifies again once it recovers. | [![Open your Home Assistant instance and show the blueprint import dialog.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2FBerT666%2FHASS-Homebrew%2Fmain%2Ffermentation_sensor_watchdog.yaml) |

Each blueprint is independent — use only the ones you need. The "My Home Assistant" buttons above open the import dialog on your own instance with the blueprint URL pre-filled (requires the [`my` integration](https://www.home-assistant.io/integrations/my/), enabled by default).

Manual import: **Settings → Automations & Scenes → Blueprints → Import Blueprint**, then paste the blueprint's GitHub URL (see the `.yaml` files in this repo).

## Requirements

- Home Assistant 2024.10 or newer.
- A temperature sensor entity (`device_class: temperature`).
- An `input_boolean` helper marking whether fermentation is active.
- An `input_number` helper holding your target temperature.
- Switch entities for whichever actuators you're controlling.

Nothing is hardcoded — every entity is picked through a selector when you create the automation from the blueprint.

## Background

Originally built to control a converted IKEA KALLNAT fridge as a mead fermentation chamber, using a RAPT Pill Bluetooth hydrometer for temperature, a heat belt for backup heat, and the fridge's own compressor (via a smart plug) for cooling. Generalized here so the same logic works with any hydrometer/sensor and any switch-controlled heater/cooler.

## Future:
will add fermentation monitoring and alerting based on SG, °B / °P will maybe follow.

## License

[MIT](LICENSE)
