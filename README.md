# An experimentation of convertin Jan from Electron to Tauri

To build the project just do:

> npx tauri build

on your platform.

The output should be in `scr-tauri/target/release`.

The size should be around 6 - 10MB.

I am doing it in a very experimental manner, meaning this app is purely UI only. It only work using:

> llama3.2:3b-gguf-q4-km

So make sure to have that version running on your cortex CLI API server.
