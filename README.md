<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nosso Amor</title>
    <style>
        body { text-align: center; font-family: Arial, sans-serif; margin-top: 50px; }
        h1 { color: #ff4081; }
        #contador, #proximo-aniversario { font-size: 24px; font-weight: bold; }
    </style>
</head>
<body>
    <h1>Nosso Amor:</h1>
    <p id="contador"></p>

    <h1>Falta para nosso próximo aniversário:</h1>
    <p id="proximo-aniversario"></p>

    <script>
        function calcularTempo() {
            const dataInicio = new Date("2014-02-21T22:00:00"); // Data inicial

            const agora = new Date();
            let diferenca = agora - dataInicio;

            // Cálculo do tempo juntos
            const anos = Math.floor(diferenca / (1000 * 60 * 60 * 24 * 365.25));
            diferenca -= anos * (1000 * 60 * 60 * 24 * 365.25);

            const meses = Math.floor(diferenca / (1000 * 60 * 60 * 24 * 30.44));
            diferenca -= meses * (1000 * 60 * 60 * 24 * 30.44);

            const dias = Math.floor(diferenca / (1000 * 60 * 60 * 24));
            diferenca -= dias * (1000 * 60 * 60 * 24);

            const horas = Math.floor(diferenca / (1000 * 60 * 60));
            diferenca -= horas * (1000 * 60 * 60);

            const minutos = Math.floor(diferenca / (1000 * 60));

            // Exibir tempo juntos
            document.getElementById("contador").innerText = 
                `${anos} anos, ${meses} meses, ${dias} dias, ${horas} horas e ${minutos} minutos`;

            // Calcular tempo até o próximo aniversário
            let proximoAniversario = new Date(agora.getFullYear(), 1, 21, 22, 0, 0); // Próximo 21 de fevereiro às 22h
            if (agora > proximoAniversario) {
                proximoAniversario.setFullYear(agora.getFullYear() + 1);
            }

            const diferencaAniversario = proximoAniversario - agora;

            const diasRestantes = Math.floor(diferencaAniversario / (1000 * 60 * 60 * 24));
            const horasRestantes = Math.floor((diferencaAniversario % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutosRestantes = Math.floor((diferencaAniversario % (1000 * 60 * 60)) / (1000 * 60));

            // Exibir tempo restante até o próximo aniversário
            document.getElementById("proximo-aniversario").innerText = 
                `${diasRestantes} dias, ${horasRestantes} horas e ${minutosRestantes} minutos`;
        }

        // Atualiza o contador a cada minuto
        calcularTempo();
        setInterval(calcularTempo, 60000);
    </script>
</body>
</html>
