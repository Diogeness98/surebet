<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <title>Calculadora de Surebet (3 Odds)</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 400px;
      margin: 40px auto;
      padding: 20px;
      background: #f4f4f4;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
      color: #333;
    }
    label {
      display: block;
      margin: 12px 0 4px;
      font-weight: bold;
      color: #555;
    }
    input {
      width: 100%;
      padding: 8px;
      font-size: 16px;
      border-radius: 4px;
      border: 1px solid #ccc;
      box-sizing: border-box;
    }
    button {
      margin-top: 20px;
      width: 100%;
      padding: 12px;
      font-size: 18px;
      background-color: #28a745;
      color: white;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #218838;
    }
    .resultado {
      margin-top: 25px;
      font-size: 18px;
      font-weight: bold;
      color: #222;
      white-space: pre-line;
    }
  </style>
</head>
<body>
  <h2>Calculadora de Surebet (3 Odds)</h2>

  <label for="odd1">Odd 1:</label>
  <input type="number" id="odd1" step="0.01" min="1" placeholder="Ex: 2.5" />

  <label for="odd2">Odd 2:</label>
  <input type="number" id="odd2" step="0.01" min="1" placeholder="Ex: 3.1" />

  <label for="odd3">Odd 3:</label>
  <input type="number" id="odd3" step="0.01" min="1" placeholder="Ex: 4.0" />

  <label for="total">Total a Apostar (R$):</label>
  <input type="number" id="total" step="0.01" min="0.01" placeholder="Ex: 100" />

  <button onclick="calcularSurebet()">Calcular</button>

  <div class="resultado" id="resultado"></div>

  <script>
    function calcularSurebet() {
      const odd1 = parseFloat(document.getElementById('odd1').value);
      const odd2 = parseFloat(document.getElementById('odd2').value);
      const odd3 = parseFloat(document.getElementById('odd3').value);
      const total = parseFloat(document.getElementById('total').value);

      if (!odd1 || !odd2 || !odd3 || !total) {
        alert('Por favor, preencha todos os campos corretamente.');
        return;
      }

      const soma = (1 / odd1) + (1 / odd2) + (1 / odd3);
      const resultadoDiv = document.getElementById('resultado');

      if (soma >= 1) {
        resultadoDiv.textContent = 'Não é uma Surebet.';
      } else {
        const valor1 = total / (odd1 * soma);
        const valor2 = total / (odd2 * soma);
        const valor3 = total / (odd3 * soma);
        const lucro = (odd1 * valor1) - total;

        resultadoDiv.textContent =
          `É uma Surebet!\n\n` +
          `Aposte:\n` +
          `R$ ${valor1.toFixed(2)} na Odd 1\n` +
          `R$ ${valor2.toFixed(2)} na Odd 2\n` +
          `R$ ${valor3.toFixed(2)} na Odd 3\n\n` +
          `Lucro Garantido: R$ ${lucro.toFixed(2)}`;
      }
    }
  </script>
</body>
</html>
