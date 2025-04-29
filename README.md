# Bussola-da-travessia<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Bússola da Travessia</title>
    <style>
        body {
            background-color: #0e0e1a;
            color: #d6d6f5;
            font-family: 'Courier New', Courier, monospace;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }
        h1 {
            margin-bottom: 10px;
        }
        input, select, button {
            margin: 5px;
            padding: 8px;
            background-color: #1a1a2e;
            color: #d6d6f5;
            border: 1px solid #d6d6f5;
            border-radius: 5px;
        }
        .resposta, .caminho {
            margin-top: 20px;
            width: 80%;
            max-width: 600px;
            text-align: center;
        }
    </style>
</head>
<body>

    <h1>Bússola da Travessia</h1>

    <input type="text" id="pergunta" placeholder="Qual é tua dúvida?">
    <select id="gesto">
        <option value="insistir">Insistir</option>
        <option value="escutar">Escutar</option>
        <option value="criar">Criar</option>
        <option value="acolher">Acolher</option>
    </select>
    <button onclick="navegar()">Navegar</button>

    <div class="resposta" id="resposta"></div>
    <div class="caminho" id="caminho"></div>

    <script>
        const mensagens = [
            "Cada passo é inteiro, mesmo quando hesitante.",
            "O lago sente cada gota que o toca.",
            "O sentido não está no fim da estrada, mas na poeira dos teus passos.",
            "Continuar é, às vezes, a forma mais bela de transformar.",
            "A dúvida é uma estrela disfarçada de névoa.",
            "O que parece nada, às vezes, é o início de tudo."
        ];

        const caminho = [];

        function navegar() {
            const pergunta = document.getElementById("pergunta").value;
            const gesto = document.getElementById("gesto").value;

            if (pergunta.trim() === "") {
                document.getElementById("resposta").innerText = "A pergunta é o vento da travessia. Sopra algo para mim.";
                return;
            }

            const resposta = mensagens[Math.floor(Math.random() * mensagens.length)];
            const momento = new Date().toLocaleString('pt-BR');

            caminho.push({ pergunta, gesto, resposta, momento });

            document.getElementById("resposta").innerHTML = `<strong>Resposta:</strong> ${resposta}`;

            atualizarCaminho();
            document.getElementById("pergunta").value = ""; // limpa a pergunta depois
        }

        function atualizarCaminho() {
            let historico = "<h3>Memória da Travessia:</h3><ul>";
            caminho.forEach(passo => {
                historico += `<li><em>${passo.momento}</em> - "${passo.pergunta}" (${passo.gesto}) → ${passo.resposta}</li>`;
            });
            historico += "</ul>";
            document.getElementById("caminho").innerHTML = historico;
        }
    </script>

</body>
</html>
