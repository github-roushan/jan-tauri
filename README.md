# An experiment converting Jan from Electron to Tauri.

To build the project, run:

> npx tauri build

on your platform.

The output will be in `src-tauri/target/release`.

The size should be around 6–10MB.

This is a very experimental setup, meaning the app is purely UI. It only works with:

> llama3.2:3b-gguf-q4-km

Ensure that version is running on your Cortex CLI API server.
