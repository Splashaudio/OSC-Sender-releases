# OSC Sender

OSC Sender is an app for sending Open Sound Control (OSC) messages over UDP, to test or trigger lighting desks, sound and video software, and any other OSC device. Save the messages you use as preset pads and fire each one with a click or a keyboard shortcut.

**Download the latest version from [Releases](../../releases/latest).**

## Mac

- Needs macOS 13 (Ventura) or later on Apple silicon (M1 or newer).
- Download `OSC-Sender-mac-<version>.zip` (for example `OSC-Sender-mac-1.5.zip`), unzip it, and move **OSC_Sender.app** to Applications.
- The first time you open it, macOS may say it's from an unidentified developer. Right-click (or Control-click) the app, choose **Open**, then **Open** again. Or go to System Settings ▸ Privacy & Security and click **Open Anyway**.

## Windows

A Windows version of OSC Sender 1.5 is coming. When it's ready, it will be in [Releases](../../releases) as `OSC-Sender-windows-<version>.zip`.

## Using OSC Sender

The message editor is on the left and your preset pads are on the right.

1. Enter the destination: an IPv4 address or a hostname such as `localhost`, and the UDP port the receiver listens on. IPv4 broadcast addresses such as `255.255.255.255` work too.
2. Enter an OSC address starting with `/`, and any arguments, separated by commas.
3. Click **SEND**, or press Return. Turn on **Send repeatedly** to keep sending at an interval until you click **STOP** or press Esc.

The light in the top right flashes green on each send, stays green while repeating, and turns red if a send fails. **Last sent** at the bottom shows what went where.

### Arguments

With the type set to **Auto (mixed)**, each value's type is detected, so one message can mix types:

| You type | Sent as |
|---|---|
| `1` | Integer (32-bit) |
| `0.5` or `1e5` | Float |
| `true` / `false` | Boolean |
| `kick` | String |
| `"a, b"` or `'2'` | String. Quotes keep commas and stop numbers being converted. |
| `i:5`, `f:1`, `s:true`, `b:false` | Integer, Float, String, Boolean. The prefix forces the type. |

For example, `1, 0.5, "Lead vocal", true` sends an integer, a float, a string and a boolean. You can also choose a single type (String, Integer, Float or Boolean) for every value.

### Preset pads

- **Save as New…** saves the current message as a pad. The suggested name is the address and its arguments, such as `/fader/1 0.5`, so one address can have several presets.
- **Click a pad** to send it once. **Cmd+1 to Cmd+9** (Ctrl+1 to Ctrl+9 on Windows) send pads 1 to 9.
- **Cmd-click a pad** (Ctrl-click on Windows) to load it into the editor, change it, and click **Update**.
- **Right-click a pad** to send, edit, rename or delete it.
- **Rearrange** lets you drag pads into a new order.
- **Hide Presets** (Shift+Cmd+P) hides the pads and makes the window narrower. Cmd+1 to Cmd+9 still work.

Your settings and presets are saved automatically on your computer.

## Troubleshooting

- **Nothing arrives:** check the address and port match the receiver, that the receiver is listening for OSC over UDP, and that a firewall isn't blocking UDP. For software on the same computer, use `127.0.0.1`.
- **"Invalid settings":** the OSC address must start with `/`, quotes must be closed, and integers must be between -2147483648 and 2147483647 (use a float for bigger numbers).
