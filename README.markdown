Binary-only Java WebSockets
===============

This is a fork of the Java-WebSocket library (version 1.6.1) created specifically for the [MicroPython Tools plugin](https://github.com/lukaskremla/micropython-tools-jetbrains) for JetBrains IDEs.

## Why this fork exists

The MicroPython WebREPL protocol sends binary data that isn't valid UTF-8 when communicating over raw paste mode. The original library attempted to decode all WebSocket messages as UTF-8 strings, causing errors when receiving binary data from WebREPL.

This fork:
- Removes UTF-8 validation in the TextFrame class
- Ensures the string-based onMessage method is never used
- Processes all incoming data as raw binary first
- Modifies the default WebSocketClient reset() function to be publicly accessible
- Adds a workaround for error handling to the reset() and run()

License
-------

Everything found in this repo is licensed under an MIT license. See
the `LICENSE` file for specifics.
