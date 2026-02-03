# Corne Wireless with Knucklehead Keymap and Nice View Gem

This repository contains a ZMK configuration for the Corne keyboard (CRKBD) with the **Knucklehead** keymap and **nice_view_gem** display support.

## Overview

This configuration is based on the [typeractive corne-wireless-view-zmk-config](https://github.com/typeractivexyz/corne-wireless-view-zmk-config) repository, with the following additions:

- **Knucklehead keymap** - A sophisticated keymap featuring home row mods, combos, and smart layers
- **nice_view_gem** - Custom display support for enhanced visual feedback

## Features

### Knucklehead Keymap

The Knucklehead keymap provides a powerful and ergonomic typing experience with:

- **Home Row Mods (HRM)** - Modifiers on the home row for efficient typing
  - Left hand: Ctrl, Alt, Cmd, Meh
  - Right hand: Meh, Cmd, Alt, Ctrl
- **Smart Layers** - Intelligent layer activation with num-word support
- **Combos** - Symbol and navigation combos for quick access
- **Multiple Layout Support**:
  - Colemak-DH (default)
  - Colemak
  - Dvorak
  - QWERTY
- **Custom Behaviors**:
  - Smart shift (tap for sticky shift, double-tap for caps-word)
  - Smart num-word with arrows and shift support
  - Balanced tapping terms for optimal responsiveness

### Display Features

- **nice_view_gem** - Custom status screen with animations
- Display blanking on idle for battery conservation
- Custom status screen support

### Battery Optimization

The configuration includes several battery-saving features:

- Deep sleep enabled (30-minute timeout)
- Display blanking on idle
- Animation disabled for reduced power consumption
- Configurable via `config/corne.conf`

## Building

This repository uses GitHub Actions for automated firmware builds. Simply push changes to trigger a build, or manually trigger the workflow from the Actions tab.

The build configuration supports:
- Left and right halves with nice_view_gem display
- ZMK Studio support for real-time keymap updates

## Configuration

### Switching Layouts

To switch between keyboard layouts, edit `knucklehead/base.dtsi` and uncomment your desired layout:

```c
// Alpha layer: uncomment desired, comment the others
#include "L1_colemak-dh.dtsi"
// #include "L1_colemak.dtsi"
// #include "L1_dvorak.dtsi"
// #include "L1_qwerty.dtsi"
```

### Customizing Behaviors

Key timing constants can be adjusted in `knucklehead/base.dtsi`:

- `TAPPING_TERM_MS` - Base tapping term (default: 280ms)
- `QUICK_TAP_MS` - Quick tap threshold (default: 175ms)
- `COMBO_TERM_DEFAULT` - Combo timeout (default: 30ms)

## Dependencies

This configuration uses the following ZMK modules:

- [zmk-auto-layer](https://github.com/urob/zmk-auto-layer) - For num-word and smart layer support
- [zmk-tri-state](https://github.com/urob/zmk-tri-state) - For tri-state behaviors
- [nice-view-gem](https://github.com/M165437/nice-view-gem) - For display support

## Credits

- Based on [typeractive corne-wireless-view-zmk-config](https://github.com/typeractivexyz/corne-wireless-view-zmk-config)
- Knucklehead keymap inspired by various ZMK community configurations
- Combos implementation adapted from [caksoylar/zmk-config](https://github.com/caksoylar/zmk-config)
- Behaviors inspired by [urob/zmk-config](https://github.com/urob/zmk-config)

## License

MIT
