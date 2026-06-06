# BTHome Config Tools

A Web Bluetooth configuration tool for connecting to and configuring supported BTHome Bluetooth sensors directly from a browser.

> This tool is intended only for Athom devices.

## Supported Devices

- Presence sensor `PSBT03`
- Door/window sensor `SS01-DTH`
- Wireless button `WS01`

## Features

- Read, generate, and write the BTHome AES key
- Configure the presence sensor report interval, from `10` to `600` seconds
- Configure presence sensor radar parameters: `ONTH`, `HOLD`, `R1TH`, `R2TH`, and `R3TH`
- Send raw radar AT commands to the presence sensor
- Configure door sensor debounce time, from `10` to `5000` ms
- Configure the button advertising interval, from `5` to `3600` seconds
- Upgrade firmware over OTA
- Restore key, reboot device, and reset radar parameters

## Browser Requirements

This tool uses Web Bluetooth, so it must run in a browser that supports it:

- Recommended: Chrome / Edge on desktop
- Android: Chrome
- Not supported: iOS Safari

## Usage

Open <https://athom-tech.github.io/bthome-sensor/> and follow the on-page instructions to configure

## Configuration

### BTHome AES Key

The AES key is 16 bytes long, represented as 32 hexadecimal characters. It is used by platforms such as Home Assistant to authenticate encrypted BTHome devices.

You can enter a key manually or generate a random one. A generated key is not written to the device until you click the save button.

### Presence Sensor

The presence sensor supports:

- Report interval: `10-600` seconds, persisted after power loss
- Common radar parameters: `ONTH`, `HOLD`, `R1TH`, `R2TH`, and `R3TH`
- Raw AT command sending
- Radar factory reset

When reading or applying common radar parameters, the tool automatically handles radar configuration mode. Before sending a single raw AT command manually, click **Enter Config Mode** if the radar is not already in configuration mode.

### Door Sensor

The door sensor supports debounce time configuration from `10` to `5000` ms. The default value is `100` ms. After a state change, the device waits for this duration before reporting the stable state.

### Button

The button supports advertising interval configuration from `5` to `3600` seconds. The default value is `60` s. The device broadcasts sensor data once per this interval, and the setting persists after power loss. To configure a button, hold its button for `8` seconds to enter configuration mode (LED blinks at 1 Hz).

## OTA Upgrade

- Do not disconnect Bluetooth
- Do not close or refresh the page
- Do not switch device type
- The device will reboot automatically after the upgrade completes

## License

MIT License. See [LICENSE](LICENSE) for details.
