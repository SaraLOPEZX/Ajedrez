 function updateTimers() {
      if (currentPlayer === 'white') {
        whiteTime++;
      } else {
        blackTime++;
      }

      // Formateamos el tiempo en minutos y segundos
      document.getElementById('white-time').textContent = formatTime(whiteTime);
      document.getElementById('black-time').textContent = formatTime(blackTime);
    }

    // Formatea el tiempo en minutos y segundos
    function formatTime(time) {
      const minutes = Math.floor(time / 60);
      const seconds = time % 60;
      return `${pad(minutes)}:${pad(seconds)}`;
    }

    // Añade un 0 al número si es menor a 10
    function pad(num) {
      return num < 10 ? '0' + num : num;
    }

    // Inicia el temporizador del jugador actual
    function startTimer() {
      if (currentPlayer === 'white') {
        document.getElementById('white-time').parentNode.classList.add('white-turn');
        document.getElementById('black-time').parentNode.classList.remove('black-turn');
        if (whiteTimer) clearInterval(whiteTimer);
        whiteTimer = setInterval(updateTimers, 1000);
      } else {
        document.getElementById('black-time').parentNode.classList.add('black-turn');
        document.getElementById('white-time').parentNode.classList.remove('white-turn');
        if (blackTimer) clearInterval(blackTimer);
        blackTimer = setInterval(updateTimers, 1000);
      }
    }

    // Detiene el temporizador del jugador actual
    function stopTimer() {
      if (currentPlayer === 'white') {
        clearInterval(whiteTimer);
      } else {
        clearInterval(blackTimer);
      }
    }

    // Llamamos a la función para crear el tablero cuando la página cargue
    window.onload = function() {
      createChessBoard();
      startTimer();  // Iniciar el temporizador al cargar el juego
    };
  </script>

</body>
</html>
