# Window Interconnection

This simple project consists of **two HTML pages** (window1.html and window2.html) that communicate with each other to synchronize the position of a circle and a line between two browser windows. It is a simple project to practice both HTML and the use of APIs such as [**`BroadcastChannel`**](https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API).
---

## How does it work?

1. **Canvas and circle**
   - Each page creates a `<canvas>` that occupies the entire viewport.
   - A white circle with a black border (30px radius) is drawn in the center of the canvas.
2. **BroadcastChannel**
   - Both windows share the same channel named `"window_sync"` using the [**`BroadcastChannel`**](https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API) API.
   - Each window sends its position (X/Y coordinates of the circle's center) every ~16 ms. To calculate the necessary milliseconds based on the desired frame rate, divide 1000 by that amount (e.g., 1000 / 60 = 16.6ms).
3. **Synchronization**
   - When one window receives a message from the other, it updates the target position (`targetOtherWindowPos`).
   - In the next frame, a black line is drawn connecting its own circle with the circle in the other window.
4. **Resizing**
   - When the window size changes, the canvas adjusts, and the current position continues to be sent.

---

## How to use it

It's as simple as opening the window1.html and window2.html files in two different browser tabs or windows (Chrome, Edge, Firefox, etc.); no server is needed.

---

## How to customize and change values

- **Change colors**: modify the `fillStyle` and `strokeStyle` values in the canvas drawing block.
- **Adjust radius**: change the `radius` constant in the draw() function.
- **Broadcast frequency**: the `BROADCAST_INTERVAL` constant controls how often coordinates are sent.

## License

This example is under the **MIT** license.
