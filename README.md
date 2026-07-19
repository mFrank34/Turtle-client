# TurtleNet Lua Client

This is the official Lua client for **TurtleNet**, designed to run on ComputerCraft (CC: Tweaked) devices. It enables remote control, telemetry, and automation for Turtles and Computers via secure WebSockets (WSS).

---

## Features

*   **Secure Connectivity:** Communicates over WSS (WebSocket Secure) to ensure remote commands are encrypted.
*   **Auto-Reconnection:** Automatically attempts to re-establish connections if the server is offline or the WebSocket drops.
*   **Telemetry:** Real-time reporting of fuel levels, inventory state, and GPS coordinates.
*   **Remote Execution:** Supports a wide range of peripheral and turtle commands:
    *   **Movement:** Forward, back, up, down, turn left/right.
    *   **Mining:** Digging (front/up/down) and inspection.
    *   **Interaction:** Placing, dropping, and sucking items.
    *   **Inventory Management:** Slot selection and full inventory scans.
    *   **Utility:** Peripheral scanning and GPS location.

---

## Setup & Installation

1.  **Configure Environment:** Ensure your Minecraft server or CC: Tweaked instance has HTTP/HTTPS access enabled in the configuration file (`cc-tweaked.cfg`).
2.  **Deployment:** Create a new file on your turtle or computer (e.g., `turtlenet.lua`) and paste the client code into it.
3.  **Auto-start:** To have the client run automatically when the computer boots, rename the file to `startup` or place it in the `/startup/` directory.

---

## Configuration

Modify the `CONFIG` table at the top of the script to match your environment:

```lua
local CONFIG = {
    host = "turtle.frankslab.uk", -- Your domain or IP
    protocol_http = "https://",   -- Ensure this matches your server
    protocol_ws = "wss://",       -- Ensure this matches your server
    -- node_id is automatically determined by Label or ID
}
```

## Command Reference

The client listens for JSON-formatted messages over the WebSocket. Below are the supported command types:

| Category | Commands |
|----------|----------|
| **Movement** | `move_forward`, `move_back`, `move_up`, `move_down`, `turn_left`, `turn_right` |
| **Mining** | `dig`, `dig_up`, `dig_down` |
| **Interaction** | `suck`, `suck_up`, `suck_down`, `drop`, `drop_up`, `drop_down`, `place`, `place_up`, `place_down` |
| **Inspection** | `inspect`, `inspect_up`, `inspect_down` |
| **Inventory** | `select_slot`, `refuel`, `scan_inventory` |
| **Utilities** | `scan_peripherals`, `get_location` |