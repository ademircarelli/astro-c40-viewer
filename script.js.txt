window.addEventListener("gamepadconnected", (e) => {
  console.log("Controle conectado:", e.gamepad);
  loop();
});

window.addEventListener("gamepaddisconnected", (e) => {
  console.log("Controle desconectado:", e.gamepad);
});

function loop() {
  const gamepads = navigator.getGamepads();
  const gp = gamepads[0];

  if (gp) {
    const buttons = document.querySelectorAll(".button");

    buttons.forEach((btn) => {
      const buttonIndex = parseInt(btn.dataset.button);
      if (gp.buttons[buttonIndex] && gp.buttons[buttonIndex].pressed) {
        btn.style.display = "block";
      } else {
        btn.style.display = "none";
      }
    });
  }

  requestAnimationFrame(loop);
}
