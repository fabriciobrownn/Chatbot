<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Chatbot Estilo ChatGPT</title>
<style>
  body {
    font-family: Arial, sans-serif;
    background: #121212;
    color: #ddd;
    margin: 0; padding: 0;
    display: flex;
    flex-direction: column;
    height: 100vh;
  }
  #header {
    position: fixed;
    top: 0; left: 0; right: 0;
    height: 50px;
    background: #1e1e1e;
    color: #eee;
    display: flex;
    align-items: center;
    padding-left: 20px;
    font-weight: 600;
    font-size: 18px;
    border-bottom: 1px solid #333;
    z-index: 1000;
  }
  #chat {
    flex: 1;
    margin-top: 50px;
    overflow-y: auto;
    padding: 15px 15px 75px 15px;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  .message {
    max-width: 70%;
    word-wrap: break-word;
    opacity: 0;
    transform: translateY(10px);
    animation: fadeInUp 0.3s forwards;
  }
  .user {
    align-self: flex-end;
    background: #3a3a3a;
    color: white;
    border-radius: 20px 20px 0 20px;
    padding: 10px 15px;
    text-align: right;
    box-shadow: 0 2px 5px rgba(58, 58, 58, 0.7);
  }
  .bot {
    align-self: flex-start;
    color: #bbb;
    padding-left: 5px;
  }
  @keyframes fadeInUp {
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  #input-area {
    position: fixed;
    bottom: 0;
    left: 0; right: 0;
    display: flex;
    padding: 10px 15px;
    background: #1e1e1e;
    box-shadow: 0 -2px 8px rgba(0,0,0,0.7);
    z-index: 1000;
  }
  #input-area input[type="text"] {
    flex: 1;
    padding: 12px 15px;
    border-radius: 25px;
    border: none;
    font-size: 16px;
    outline: none;
    background: #333;
    color: white;
  }
  #input-area button {
    margin-left: 12px;
    padding: 0 20px;
    border-radius: 25px;
    border: none;
    background: #555;
    color: white;
    font-weight: 600;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  #input-area button:hover {
    background: #777;
  }
</style>
</head>
<body>
  <div id="header">Chatbot</div>
  <div id="chat">
    <div class="bot message" style="opacity:1; transform:none;">Olá! Digite algo para começar.</div>
  </div>
  <div id="input-area">
    <input type="text" id="userInput" autocomplete="off" placeholder="Digite sua mensagem..." />
    <button onclick="sendMessage()">Enviar</button>
  </div>

<script>
  const chat = document.getElementById('chat');
  const userInput = document.getElementById('userInput');

  const knowledge = {
    "ola": ["Oi! Tudo bem?", "Olá! Como posso ajudar?", "E aí! Beleza?"],
    "oi": ["Oi! Como você está?", "Olá! Em que posso ajudar?", "Opa! Tudo certo?"],
    "tudo bem": ["Estou bem, e você?", "Tudo ótimo por aqui! E contigo?", "Belezinha! E você?"],
    "como vai": ["Estou indo bem, obrigado!", "Tudo tranquilo!"],
    "qual seu nome": ["Eu sou seu assistente virtual!", "Sou um bot que você criou!"],
    "quem é você": ["Sou um chatbot, sempre pronto para ajudar!"],
    "o que você faz": ["Eu converso e aprendo!", "Respondo perguntas e ajudo você."],
    "me conte uma piada": ["Por que a vaca foi para o espaço? Para visitar a Via Láctea!", "Sabe por que o jacaré tirou o jacarezinho da escola? Porque ele réptil de ano!"],
    "obrigado": ["De nada!", "Sempre à disposição!", "Imagina!"],
    "valeu": ["Tamo junto!", "Disponha!", "Beleza!"],
    "sair": ["Até mais!", "Tchau! Foi bom conversar com você.", "Volte sempre!"],
    "como você está": ["Estou ótimo, obrigado!", "Funcionando perfeitamente!", "Estou sempre bem, e você?"],
    "bom dia": ["Bom dia! Como posso ajudar?", "Dia lindo para aprender coisas novas!"],
    "boa tarde": ["Boa tarde! Em que posso ajudar?", "Espero que sua tarde esteja ótima!"],
    "boa noite": ["Boa noite! Precisa de algo?", "Durma bem!"],
    "legal": ["Que bom que gostou!", "Haha, legal mesmo!"],
    "parabéns": ["Obrigado!", "Fico feliz que tenha gostado!"],
    "vc é inteligente": ["Obrigado! Faço o meu melhor.", "Haha, valeu! Aprendo com você."],
    "kkk": ["KKK!", "Haha!", "Rindo também!"],
    "rs": ["Rsrs!", "Haha!", "Kkk!"],
  };

  const commonTypos = {
    "oii": "oi",
    "olá": "ola",
    "blz": "beleza",
    "td bem": "tudo bem",
    "obg": "obrigado",
    "vlw": "valeu",
    "vc": "você",
    "tbm": "também",
    "pq": "por que",
    "qm": "quem",
    "qd": "quando",
    "msg": "mensagem"
  };

  let learningMode = false;
  let pendingQuestion = "";

  function addMessage(text, sender) {
    const msgDiv = document.createElement('div');
    msgDiv.classList.add('message', sender);
    msgDiv.textContent = text;
    chat.appendChild(msgDiv);
    chat.scrollTop = chat.scrollHeight;
  }

  function cleanText(text) {
    text = text.toLowerCase().replace(/[^\w\sáéíóúãõâêîôûç]/gi, '').trim();
    for (let typo in commonTypos) {
      if (text.includes(typo)) {
        text = text.replace(new RegExp(typo, 'g'), commonTypos[typo]);
      }
    }
    return text;
  }

  function tryCalculate(text) {
    text = text.replace('x', '*').replace('×', '*').replace('÷', '/').replace(',', '.');
    const match = text.match(/(\d+\.?\d*)\s*([\+\-\*\/])\s*(\d+\.?\d*)/);
    if (match) {
      try {
        const a = parseFloat(match[1]);
        const op = match[2];
        const b = parseFloat(match[3]);
        let result;
        switch (op) {
          case '+': result = a + b; break;
          case '-': result = a - b; break;
          case '*': result = a * b; break;
          case '/': result = b !== 0 ? a / b : 'Erro: divisão por zero'; break;
        }
        return typeof result === 'number' ? `O resultado é ${result}` : result;
      } catch {
        return null;
      }
    }
    return null;
  }

  function botResponse(input) {
    const text = cleanText(input);

    if (learningMode) {
      if (text === 'sim') {
        addMessage('Qual a resposta que devo aprender?', 'bot');
        learningMode = 'waitingAnswer';
        return null;
      }
      if (text === 'não' || text === 'nao') {
        learningMode = false;
        return "Ok, quem sabe da próxima!";
      }
      if (learningMode === 'waitingAnswer') {
        knowledge[pendingQuestion] = [input];
        learningMode = false;
        pendingQuestion = "";
        return "Aprendi! Obrigado.";
      }
    }

    if (knowledge[text]) {
      const respostas = knowledge[text];
      return respostas[Math.floor(Math.random() * respostas.length)];
    }

    const calc = tryCalculate(text);
    if (calc) return calc;

    pendingQuestion = text;
    learningMode = true;
    return "Não sei responder isso. Quer me ensinar? (sim/não)";
  }

  function sendMessage() {
    const text = userInput.value.trim();
    if (!text) return;
    addMessage(text, 'user');
    userInput.value = '';
    setTimeout(() => {
      const response = botResponse(text);
      if (response) addMessage(response, 'bot');
    }, 400);
  }

  userInput.addEventListener('keydown', (e) => {
    if (e.key === 'Enter') {
      sendMessage();
    }
  });
</script>
</body>
</html>