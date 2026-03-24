# OpenDeck Darktable Plugin

This plugin enables controlling Darktable (exposure, contrast, navigation) using physical knobs and buttons on OpenDeck-compatible hardware (like the Soomfon SE).

## Features
- **Knob Support**: Maps `EncoderTwist` events to Darktable Lua commands.
- **Sandbox Escape**: Built for Flatpak environments. Uses `flatpak-spawn --host` to send DBus signals to the host's Darktable instance.
- **Cross-Plugin Namespace**: Synchronized with the `ak` namespace for seamless integration with the patched hardware plugin.

## How it works
The plugin listens for `EncoderTwist` events from OpenDeck and translates them into:
```bash
flatpak-spawn --host dbus-send --session --dest=org.darktable.service --type=method_call /org/darktable/service org.darktable.service.RemoteLua string:"darktable.gui.action('...', 0, ...)"
```

## Setup
1. Deploy the plugin folder to `~/.var/app/me.amankhanna.opendeck/config/opendeck/plugins/st.lynx.plugins.darktable.sdPlugin/`.
2. In OpenDeck UI, assign the "Darktable Control" actions to your device's dials.
3. Ensure Darktable is running on the host.
