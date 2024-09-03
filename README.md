<!DOCTYPE html> 
<html> 
<head> 
  <title>Простой Чат-бот</title>
<img class="ICON" src = "https://i.gifer.com/origin/47/4705530785b66c5fcbdc84fba4315dc4_w200.gif"/>
  <style> 
  .ICON{
   position: absolute; 
      top: -6%; 
      left: 47%; 
      width:5%; 
      margin: 50px auto; 
      border: 10px solid rgba(255,255,255, 0,8); 
      border-radius: 200px; 
  }
 
    .text { 
	 display: flex; 
      justify-content: center; 
      align-items: center; 
      
      margin: 0; 
      font-family: sans-serif; 
      font-size: 4em; 
      color: #800080; /* Начальный фиолетовый цвет */ 
      animation: color-shift 3s linear infinite; 
    } 
 
    @keyframes color-shift { 
      0% { 
        color: #800080; /* Фиолетовый */ 
      } 
      50% { 
        color: #0000ff; /* Голубой */ 
      } 
      100% { 
        color: #800080; /* Фиолетовый */ 
      } 
    } 
  </style> 
</head> 
<body> 
 
  
  
  
  <style> 
    body { 
	background-image:url('https://i.pinimg.com/originals/7d/3b/e5/7d3be560eb3d4383a44810911d6c7384.gif');
      
    } 
 
    .chat-container { 
	background: linear-gradient(135deg,rgba(225,225,225 0,1),rgba(225,225,0));
	backdrop-filter:blur(20px);
	-webkit-backdrop-filter:blur(10px);
	
      display: flex; 
      flex-direction: column; 
      width: 50%; 
      margin: 50px auto; 
      border: 10px solid rgba(255,255,255, 0,8); 
	  box-shadow: 0 8px 32px 0 rgba(0,0,0,0.37);
      padding: 10px; 
      border-radius: 10px; 
    } 
 
    .chat-message { 
      padding: 10px; 
      margin-bottom: 10px; 
      border-radius: 5px; 
    } 
 
    .user-message { 
     background-color: #7b68ee; 
      color: #ffffff; 
      position: relative; 
    } 
 
    .bot-message {
	  background-color:#2F4F4F; 
      color: #ffffff; 
     
    } 
 
    .typing-indicator { 
      position: absolute; 
      top: 50%; 
      left: 50%; 
      transform: translate(-50%, -50%); 
      display: inline-block; 
      width: 10px; 
      height: 10px; 
      border-radius: 50%; 
      background-color: #fff; 
      animation: typing 1s linear infinite; 
    } 
 
    @keyframes typing { 
      0% { 
        opacity: 1; 
        transform: translate(-50%, -50%) scale(1); 
      } 
      50% { 
        opacity: 0.5; 
        transform: translate(-50%, -50%) scale(1.2); 
      } 
      100% { 
        opacity: 1; 
        transform: translate(-50%, -50%) scale(1); 
      } 
    } 
 
    input[type="text"] {
	
       position: fixed; /* Фиксируем контейнер на экране */ 
      bottom: 20px; /* Отступ от нижнего края */ 
      left: 43%; /* Центрирование по горизонтали */ 
      transform: translateX(-50%); /* Дополнительное центрирование */ 
      background-color: #fff; 
      padding: 10px; 
      border-radius: 5px; 
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); /* Добавляем тень */ 
      width: 30%; /* Ширина контейнера */ 
      max-width: 500px; /* Максимальная ширина */ 
    } 
 
    button { 
	img-src = "https://cdn-icons-png.flaticon.com/512/2111/2111644.png";
	 position: fixed; /* Фиксируем контейнер на экране */ 
      bottom: 20px; /* Отступ от нижнего края */ 
      left: 65%; /* Центрирование по горизонтали */ 
      transform: translateX(-50%); /* Дополнительное центрирование */ 
      background-color: #fff; 
      padding: 10px; 
      border-radius: 5px; 
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); /* Добавляем тень */ 
      width: 10%; /* Ширина контейнера */ 
      max-width: 500px; /* Максимальная ширина */ 
      padding: 10px 20px; 
      margin-top: 10px; 
      border: none; 
      background-color: #7b68ee; 
      color: white; 
      border-radius: 5px; 
      cursor: pointer; 
    } 
  </style> 
</head> 
<body> 
  
 
  <script> 
    const chatMessages = document.getElementById('chat-messages'); 
    const userInput = document.getElementById('user-input'); 
 
    function sendMessage() { 
      const message = userInput.value; 
      if (message.trim() !== '') { 
        // Display user message 
        displayMessage(message, 'user-message'); 
        userInput.value = ''; 
 
        // Simulate bot typing 
        const botMessage = "Bot: " + generateBotResponse(message); 
        typeMessage(botMessage, 'bot-message'); 
      } 
    } 
 
    function displayMessage(message, className) { 
      const messageElement = document.createElement('div'); 
      messageElement.classList.add('chat-message', className); 
      messageElement.textContent = message; 
      chatMessages.appendChild(messageElement); 
    } 
 
    function generateBotResponse(message) { 
      // Replace with your actual bot logic 
      return "This is a response to your message: " + message; 
    } 
 
    function typeMessage(message, className) { 
      const messageElement = document.createElement('div'); 
      messageElement.classList.add('chat-message', className); 
      messageElement.textContent = ''; //  &lt;-- Добавлено, чтобы текст начинался пустым 
 
      // Add typing indicator 
      const typingIndicator = document.createElement('span'); 
      typingIndicator.classList.add('typing-indicator'); 
      messageElement.appendChild(typingIndicator); 
 
      chatMessages.appendChild(messageElement); 
 
      let i = 0; 
      const interval = setInterval(() => { 
        if (i < message.length) { 
          messageElement.textContent += message.charAt(i); 
          i++; 
        } else { 
          clearInterval(interval); 
          // Remove typing indicator 
          typingIndicator.remove(); 
        } 
      }, 50);  
    } 
  </script> 
</head> 

  <div class="chat-container"> 
   
   
  </div> 
 
  <input type="text" id="message-input" placeholder="Введите сообщение..."> 
  <button onclick="sendMessage()">Отправить</button> 
 
  <script> 
    const chatContainer = document.querySelector('.chat-container'); 
    const messageInput = document.getElementById('message-input'); 
 
    function sendMessage() { 
      const message = messageInput.value.trim(); 
      if (message !== '') { 
        // Добавляем сообщение пользователя 
        const userMessage = document.createElement('div'); 
        userMessage.classList.add('chat-message', 'user-message'); 
        userMessage.textContent = message; 
        chatContainer.appendChild(userMessage); 
 
        // Отвечаем ботом 
        const botResponse = getBotResponse(message); 
        const botMessage = document.createElement('div'); 
        botMessage.classList.add('chat-message', 'bot-message'); 
        botMessage.textContent = botResponse; 
        chatContainer.appendChild(botMessage); 
 
        messageInput.value = ''; // Очищаем поле ввода 
      } 
    } 
 
    // Массив для хранения пар вопрос-ответ ДЛЯ КАЖДОГО СЛОВА ОТДЕЛНЫЙ ВИД С  ОШИБКАМИ
	//ПРИВЕТ 
   const questionsAndAnswers = [ 
  { 
    question: "привет", 
    answers: [ 
      "Привет! 👋 Как дела?", 
      "Привет! 👋 Чем могу помочь?", 
      "Приветствую! 👋" 
    ] 
  }, 
  //ХОРОШО А У ТЕТЯ
  { 
    question: "хорошо а у тебя", 
    answers: [ 
      "Замечательно! Чем могу помочь?", 
      "Отлично! 😄 Что тебя интересует?" 
    ] 
  }, 
  { 
    question: "приветствую", 
    answers: ["Привет! 👋 Как дела?", "Рад тебя видеть! 👋"] 
  }, 
  //КАК ДЕЛА
  { 
    question: "как дела?", 
    answers: [ 
      "У меня все отлично, спасибо за вопрос! 😊", 
      "У меня все хорошо, а как у тебя? 👍" 
    ] 
                         }, 

  { 
    question: "как дела", 
    answers: [ 
      "У меня все отлично, спасибо за вопрос! 😊", 
      "У меня все хорошо, а как у тебя? 👍" 
    ] 
  }, 
   { 
    question: "как дила ?", 
    answers: [ 
      "У меня все отлично, спасибо за вопрос! 😊", 
      "У меня все хорошо, а как у тебя? 👍" 
    ] 
  }, 
    { 
    question: "как дила?", 
    answers: [ 
      "У меня все отлично, спасибо за вопрос! 😊", 
      "У меня все хорошо, а как у тебя? 👍" 
    ] 
  }, 
      { 
    question: "как дила", 
    answers: [ 
      "У меня все отлично, спасибо за вопрос! 😊", 
      "У меня все хорошо, а как у тебя? 👍" 
    ] 
  }, 
  //ЧТО ТЫ УМЕЕШЬ
  
  {
   question: "что ты можешь", 
    answers: [ 
      "Я могу  помочь вам  с поиском интересной информации в социальных сетях, будь то  группы по вашим увлечениям,  блоги  о  технологиях или  аккаунты  с интересными  фотографиями.", 
	  "Я могу найти для вас группы по вашим интересам, блоги о технологиях или просто интересные аккаунты в соцсетях.",
	    "Я - ваш личный помощник в мире социальных сетей. Я могу подыскать вам  крутые  сайты, которые вас зацепят. ",
      "Я умею  анализировать  социальные сети  и  находить  сайты,  которые  могут  вам  быть  полезны  или  интересны." 
    ] 
  }, 
  
  {
   question: "что ты можешь?", 
    answers: [ 
      "Я могу  помочь вам  с поиском интересной информации в социальных сетях, будь то  группы по вашим увлечениям,  блоги  о  технологиях или  аккаунты  с интересными  фотографиями.", 
	  "Я могу найти для вас группы по вашим интересам, блоги о технологиях или просто интересные аккаунты в соцсетях.",
	    "Я - ваш личный помощник в мире социальных сетей. Я могу подыскать вам  крутые  сайты, которые вас зацепят. ",
      "Я умею  анализировать  социальные сети  и  находить  сайты,  которые  могут  вам  быть  полезны  или  интересны." 
    ] 
  }, 
  
  
 { 
    question: "что ты умеешь", 
    answers: [ 
      "Я могу  помочь вам  с поиском интересной информации в социальных сетях, будь то  группы по вашим увлечениям,  блоги  о  технологиях или  аккаунты  с интересными  фотографиями.", 
	  "Я могу найти для вас группы по вашим интересам, блоги о технологиях или просто интересные аккаунты в соцсетях.",
	    "Я - ваш личный помощник в мире социальных сетей. Я могу подыскать вам  крутые  сайты, которые вас зацепят. ",
      "Я умею  анализировать  социальные сети  и  находить  сайты,  которые  могут  вам  быть  полезны  или  интересны." 
    ] 
  }, 
  
 //врпрч про чаты 
 
  
  { 
    question: "спасибо", 
    answers: [ 
      "Не за что! 👋", 
      "Рад был помочь! 😊" 
    ] 
  }, 
  { 
    question: "пока", 
    answers: [ 
      "До свидания! 👋", 
      "Всего хорошего! 😊" 
    ] 
  }, 
  { 
    question: "до свидания", 
    answers: [ 
      "До свидания! 👋", 
      "Всего хорошего! 😊" 
    ] 
  }, 
  { 
    question: "прощай", 
    answers: [ 
      "Прощай! 👋", 
      "Всего доброго! 😊" 
    ] 
  } 
]; 
function getBotResponse(message) { 
  const normalizedMessage = message.toLowerCase(); 
for (const item of questionsAndAnswers) { 
    if (item.question.toLowerCase() === normalizedMessage) { 
      const randomIndex = Math.floor(Math.random() * item.answers.length); 
      return item.answers[randomIndex]; 
    } 
  } 
return "Я не понимаю. Попробуй перефразировать. 😕";
 
 
} 
  </script> 
  
  
  
</body> 
</html> 
