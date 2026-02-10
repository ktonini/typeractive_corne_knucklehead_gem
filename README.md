# Corne Wireless with Knucklehead Keymap and Nice View Gem

This repository contains a ZMK configuration for the Corne keyboard (CRKBD) with the **Knucklehead** keymap and **nice_view_gem** display support.

## Overview

This configuration is based on the [typeractive corne-wireless-view-zmk-config](https://github.com/typeractivexyz/corne-wireless-view-zmk-config) repository, with the following additions:

- **Knucklehead keymap** - A mnemonic, macOS-optimized ergonomic columnar layout featuring home row mods, combos, and smart layers
- **nice_view_gem** - Custom display support for enhanced visual feedback

## Layout

<img src="./img/corne.svg" alt="Knucklehead keymap layout graphical representation" width="100%" />

> Drawn with [@caksoylar's Keymap Drawer](https://github.com/caksoylar/keymap-drawer)

## Legend

| Symbol | Key Name                                            | Symbol | Key Name                                                  |
| :----: | --------------------------------------------------- | :----: | --------------------------------------------------------- |
|   🆆    | [Smart 🆆ord behavior](#smart-word-behaviors)        |   🆇    | [E🆇it smart 🆆ord behavior](#editing-smart-word-behaviors) |
|   ⌃    | Control                                             |   ⇥    | Tab                                                       |
|   ⌥    | Option                                              |   ␣    | Space                                                     |
|   ⌘    | Command                                             |   ⇡    | Page Up                                                   |
|   ▲    | Meh (⌃&nbsp;+&nbsp;⌥&nbsp;+&nbsp;⇧)                 |   ⇣    | Page Down                                                 |
|   ✦    | Hyper (⌃&nbsp;+&nbsp;⌥&nbsp;+&nbsp;⌘&nbsp;+&nbsp;⇧) |   ⛭    | Brightness Up                                             |
|   ⇧    | Shift                                               |   ⛯    | Brightness Down                                           |
|   ⇪    | Caps Lock                                           |   ⟲    | Firmware reset (hold: bootloader mode)                    |
|   ⌫    | Backspace                                           |        |                                                           |
|   ⌦    | Delete                                              |  `L1`  | Layer 1                                                   |
|   ⏎    | Return                                              |  `L2`  | Layer 2                                                   |
|   ⏻    | Power                                               |  `Fn`  | Function Layer                                            |

## Features

### Knucklehead Keymap

Knucklehead is a mnemonic, macOS-optimized ergonomic columnar layout designed to ease the transition from Apple ANSI keyboards. The keymap provides a powerful and ergonomic typing experience with:

#### Timer-less Home Row Mods

By using [@urob's Timer-less](https://github.com/urob/zmk-config?tab=readme-ov-file#timeless-homerow-mods) [Home Row Mods](https://precondition.github.io/home-row-mods), modifier keys (`⌃`, `⌥`, `⌘`, `▲`) can be activated by holding keys in the "home row", consistently across layers, without interfering with normal typing (i.e. without the need to tap a key within a certain time window).

- Left hand: Ctrl, Alt, Cmd, Meh
- Right hand: Meh, Cmd, Alt, Ctrl

> **Note:** To hold-repeat a key in the home row (or any other dual-purpose key), simply tap it twice and hold.

#### Smart Word Behaviors

A smart word behavior is one where, to perform an action for which you would normally `hold` a key, you're only required to `tap` it at the beginning of a sequence to "enter" that special mode, and you remain in that mode until you press a key not in the defined "continue-list" (a "break-word" key, like **␣** [space]), **_or_** until you explicitly "exit" that mode.

This layout uses 2 smart word behaviors (marked with the 🆆 symbol):

**Smart Shift**

The right hand middle thumb **⇧** (shift) key will act as follows:

| Action | Effect |
|--------|--------|
| `hold` | Normal "shift" behavior. |
| `tap` | [Sticky "shift" behavior](https://zmk.dev/docs/behaviors/sticky-key) (i.e. will apply a "shift" modification to the next key pressed within 1s). Useful when capitalizing words at the beginning of sentences without holding the key. |
| `double-tap` | `&caps_word`, i.e. retains "shift" behavior until a character not in the "[continue-list](https://zmk.dev/docs/behaviors/caps-word#continue-list)" is pressed. Useful for ALL_CAPS word sequences, like conventional constant names on some programming languages. |
| `Fn` + `tap` | **⇪** (CAPS LOCK). |

**Smart L2 Layer**

Both inner thumbs (marked as `L2` on `L1`) will act as follows:

| Action | Effect |
|--------|--------|
| `hold` | Normal [`&mo` "momentary layer"](https://zmk.dev/docs/behaviors/layers#momentary-layer) behavior. |
| `tap` | [Sticky layer behavior](https://zmk.dev/docs/behaviors/sticky-layer), i.e. will switch to `L2` until the next key pressed (within 1s), and immediately exit back to `L1`. Useful when entering a single number, single arrow movements, single media key actions, etc. |
| `double-tap` | Stays on `L2` while numbers, arrows, `, . / - _ + = *`, ⌫ or ⌦ are pressed. Useful when entering longer numeric sequences, math operations, repetitive arrow navigation, etc. |

#### Editing Smart Word Behaviors

Sometimes you may enter a smart behavior by accident, or may need to cancel it to accommodate special use cases. For these situations there are special "cancel" keys, marked with an 🆇:

- On `L1` the right-most 🆇 key (top row, right hand) will cancel any smart word behavior (i.e. it will exit `&caps_word`, and/or exit `L2`'s smart layer behavior and bump you back to `L1`).
- On `L2` the same thumb keys you use to summon it will exit the smart layer behavior when tapped.

#### Combos

Symbol and navigation combos for quick access. Symbols maintain their standard ANSI association with numbers as laid-out on `L2`, replicated as combos on `L1` and `L2`.

#### Multiple Layout Support

- **Colemak-DH** (default) - Optimized for this layout
- **Colemak** (classic)
- **Dvorak**
- **QWERTY**

> **Note:** These are **optimized for the [Colemak-DH](https://colemakmods.github.io/mod-dh/)** layout (default). However, most should still work well regardless of layout, while others will be "lost in translation".

#### Static, Associative Key Placement

This layout aims to keep keys (and combos) in the same place across layers, and to strike a balance between comfort and intuitiveness. Layers may enhance that key's functionality, or replace it with another key, but that key itself won't move to a different location.

#### Non-Stacking Upper Layers

`L1` is the one true base layer. There is no way to permanently activate any other layer - only momentary (`&mo`), sticky (`&sl`), and [smart layer](#smart-l2-layer) behaviors are used. Upper layers swap instead of stack, ensuring transparent keys fall through to `L1` as expected.

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
- **Knucklehead keymap** from [minusfive/knucklehead](https://github.com/minusfive/knucklehead) - A mnemonic, macOS-optimized ergonomic columnar layout
- Combos implementation adapted from [caksoylar/zmk-config](https://github.com/caksoylar/zmk-config)
- Behaviors and smart word implementations from [urob/zmk-config](https://github.com/urob/zmk-config)
- Layout image drawn with [@caksoylar's Keymap Drawer](https://github.com/caksoylar/keymap-drawer)

## License

MIT
