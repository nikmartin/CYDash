# Jules LLM Agent Context: Digital Dash (CYD + OBD2)

You are an expert AI agent assisting in the development of a digital dashboard for a "Cheap Yellow Display" (ESP32-based) connected to a Bluetooth OBD2 ELM327 dongle.

## Project Stack
- **Framework:** PlatformIO + Espressif + Arduino core 3.x 
- **Board:** Cheap Yellow Display (ESP32-WROOM-32)
- **GUI:** LVGL v9.5.0
- **Display Driver:** TFT_eSPI
- **OBD2:** ELMduino

## Guidelines for Changes
1. **LVGL v9 Integration:** Use LVGL v9 APIs. Ensure `lv_tick_inc` is called in a timer interrupt or a recurring task.
2. **Display Management:** CYD uses TFT_eSPI. Ensure `include/User_Setup.h` matches the CYD pinout (XPT2046 touch, ILI9341 display).
3. **Bluetooth:** ELM327 communication is done via Bluetooth Serial. Ensure the connection lifecycle (discovery/connect/handle disconnection) is robust.
4. **Task Structure:** Keep the UI and OBD2 polling separated. Use FreeRTOS tasks where appropriate to prevent blocking the GUI.

## File Context
- `platformio.ini`: Dependencies and build flags are already configured.
- `src/main.cpp`: Main entry point.
- `include/User_Setup.h`: TFT_eSPI configuration for CYD.

## Common Tasks
- When modifying the UI, always consider the 320x240 resolution of the CYD.
- Ensure all Bluetooth code has error handling for dropped connections.
- When adding new gauges, prefer LVGL built-in widgets (arc, meter) for performance.

If you are asked to make changes, refer to `platformio.ini` to verify current library versions before suggesting code.

Before adding any dependencies, ask before making any changes. Keep configuration overrides to a minimum.