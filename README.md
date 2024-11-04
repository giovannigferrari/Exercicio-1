<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>1Cálculo de Números</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        input, button {
            padding: 10px;
            margin: 5px;
        }
        .result {
            margin-top: 20px;
        }
        .container{
            align-items: center;
            align-content: center;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
    <h1>Informe N números inteiros</h1>
    <input type="number" id="numInput" placeholder="Digite um número" />
    <button onclick="adicionarNumero()">Adicionar número</button>
    <button onclick="calcularResultados()">Calcular</button>
    <h2>Números inseridos:</h2>
    <p id="numerosInseridos"></p>
    <div class="result">
        <p>Soma de todos os números: <span id="soma"></span></p>
        <p>Média aritmética: <span id="media"></span></p>
        <p>Números pares: <span id="pares"></span></p>
        <p>Números ímpares: <span id="impares"></span></p>
    </div>
    </div>
    <script>
        let numeros = [];
        function adicionarNumero() {
            const input = document.getElementById('numInput');
            const valor = parseInt(input.value); 
            if (!isNaN(valor)) {
                numeros.push(valor);
                document.getElementById('numerosInseridos').textContent = numeros.join(', ');
                input.value = '';  
            } else {
                alert("Por favor, insira um número válido.");
            }
        }
        function calcularResultados() {
            if (numeros.length === 0) {
                alert("Por favor, insira pelo menos um número.");
                return;
            }
            const soma = numeros.reduce((acc, num) => acc + num, 0);
            document.getElementById('soma').textContent = soma;
            const media = soma / numeros.length;
            document.getElementById('media').textContent = media.toFixed(2);
            let pares = 0, impares = 0;
            numeros.forEach(num => {
                if (num % 2 === 0) {
                    pares++;
                } else {
                    impares++;
                }
            });
            document.getElementById('pares').textContent = pares;
            document.getElementById('impares').textContent = impares;
        }
    </script>
</body>
</html>
