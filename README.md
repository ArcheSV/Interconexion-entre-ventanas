# Interconexión de Ventanas

Este proyecto simple tiene **dos páginas HTML** (`window1.html` y `window2.html`) las cuales se comunican entre sí para sincronizar la posición de un círculo y una línea entre dos ventanas del navegador. Es un proyecto simple para aprender tanto HTML como el uso de APIs como el [**`BroadcastChannel`**](https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API).
---

## ¿Cómo funciona?

1. **Canvas y círculo**
   - Cada página crea un `<canvas>` que ocupa todo el viewport.
   - En el centro del canvas se dibuja un círculo blanco con borde negro (radio 30px).
2. **BroadcastChannel**
   - Ambas ventanas comparten el mismo canal llamado `"window_sync"` mediante la API [**`BroadcastChannel`**](https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API).
   - Cada ventana envía su posición (coordenadas X/Y del centro del círculo) cada ~16 ms. Para calcular los milisegundos necesarios según los fotogramas que queramos, se divide 1000 entre esa cantidad (p. ej: 1000 / 60 = 16.6ms).
3. **Sincronización**
   - Cuando una ventana recibe el mensaje del otro, actualiza la posición objetivo (`targetOtherWindowPos`).
   - En el siguiente frame se dibuja una línea negra que conecta el círculo propio con el círculo de la otra ventana.
4. **Redimensionado**
   - Al cambiar el tamaño de la ventana se ajusta el canvas y se sigue enviando la posición actual.

---

## Cómo usarlo

Es tan simple como abrir los archivos `window1.html` y `window2.html` en dos pestañas o ventanas distintas del navegador (Chrome, Edge, Firefox, etc.), no se necesita
ningun servidor.

---

## Como personalizar y cambiar los valores

- **Cambiar colores**: modifica los valores `fillStyle` y `strokeStyle` en el bloque de dibujo del canvas.
- **Ajustar radio**: cambia la constante `radius` en la función `draw()`.
- **Frecuencia de broadcast**: la constante `BROADCAST_INTERVAL` es la que controla cuán a menudo se envían las coordenadas.

## Licencia

Este ejemplo está bajo la licencia **MIT**. Siéntete libre de usarlo, modificarlo y compartirlo.
