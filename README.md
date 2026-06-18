# Alpha / One ROM Datalog Link Validator
Download: https://limewire.com/d/alDRX#6Lf8xsMOfw

A small Windows utility for verifying that a datalog UART adapter can transmit and receive correctly before troubleshooting Alpha or One ROM datalogging.

The tool performs a simple UART loopback test at **38400 baud**. It sends one byte, `0x10`, and expects to receive the same byte back.

## What It Tests

This app confirms that the PC-side serial adapter and wiring can complete a basic TX-to-RX loopback.

It is useful for checking:

- Correct COM port selection
- USB serial adapter transmit function
- USB serial adapter receive function
- TX/RX wiring continuity
- Basic datalog cable readiness

## Requirements

- Windows PC
- USB serial / UART adapter
- OneROM datalog wiring setup
- No software dependencies required for the standalone EXE

## How To Use

1. Connect the UART adapter to the PC.
2. Physically connect the adapter **TX** pin directly to its **RX** pin.
3. Open `AlphaOneRomDatalogLinkValidator.exe`.
4. Select the correct COM port.
5. Click **Connect**.
6. Click **Run Loopback Test**.

## Expected Result

A passing test shows:

- **Sent:** `10`
- **Expected Received:** `10`
- **Received:** `10`

If the received byte matches the sent byte, the app reports that the UART loopback wiring is working.

## Failed Test

If no byte is received, check:

- TX is connected directly to RX
- The correct COM port is selected
- The USB serial adapter driver is installed
- No other program is using the COM port
- The adapter is powered and recognized by Windows

If a different byte is received, check wiring, adapter configuration, and whether another device is connected to the UART lines.

## Important Note

For this loopback test, TX must be connected directly to RX on the adapter.

If the adapter is connected normally to an ECU, ROM board, or datalog device, the test may fail unless that device echoes the byte back. This tool is intended to validate the serial adapter and wiring path first.

## Serial Settings

The tool uses:

- Baud rate: `38400`
- Data bits: `8`
- Parity: `None`
- Stop bits: `1`
- Test payload: `0x10`
