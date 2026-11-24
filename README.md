
<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ARYA AI - Personal Assistant</title>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
}

body{
  font-family:Arial,sans-serif;
  background:#080f1d;
  color:white;
  min-height:100vh;
  display:flex;
  flex-direction:column;
}

header{
  background:#111d30;
  padding:18px;
  text-align:center;
  border-bottom:1px solid #263750;
}

.logo{
  color:#38bdf8;
  font-size:30px;
  font-weight:bold;
  letter-spacing:2px;
}

.subtitle{
  color:#94a3b8;
  font-size:12px;
  margin-top:5px;
}

.status{
  color:#22c55e;
  font-size:12px;
  margin-top:8px;
}

#chat{
  flex:1;
  padding:18px;
  overflow-y:auto;
  width:100%;
  max-width:850px;
  margin:auto;
  padding-bottom:110px;
}

.welcome{
  text-align:center;
  margin:35px 0;
}

.welcome h2{
  color:#38bdf8;
  font-size:25px;
  margin-bottom:10px;
}

.welcome p{
  color:#94a3b8;
  line-height:1.6;
}

.msg{
  max-width:85%;
  padding:13px 16px;
  margin:13px 0;
  border-radius:16px;
  line-height:1.6;
  white-space:pre-wrap;
  overflow-wrap:anywhere;
}

.user{
  background:#075985;
  margin-left:auto;
  border-bottom-right-radius:4px;
}

.bot{
  background:#1e293b;
  margin-right:auto;
  border:1px solid #334155;
  border-bottom-left-radius:4px;
}

.controls{
  position:fixed;
  bottom:0;
  left:0;
  width:100%;
  background:#111d30;
  padding:13px;
  display:flex;
  gap:8px;
  border-top:1px solid #263750;
}

.controls input{
  flex:1;
  min-width:0;
  padding:14px;
  border-radius:12px;
  border:1px solid #475569;
  background:#080f1d;
  color:white;
  outline:none;
  font-size:15px;
}

button{
  border:0;
  padding:12px 15px;
  border-radius:12px;
  color:white;
  background:#0284c7;
  font-weight:bold;
  cursor:pointer;
}

.clear{
  background:#475569;
}

footer{
  text-align:center;
  padding:8px;
  color:#64748b;
  font-size:11px;
  background:#111d30;
}

@media(max-width:450px){
  .controls{padding:9px;gap:5px}
  button{padding:11px 10px}
  .msg{max-width:92%}
}
</style>
</head>

<body>

<header>
  <div class="logo">ARYA AI</div>
  <div class="subtitle">YOUR PERSONAL AI ASSISTANT</div>
  <div class="status">● ONLINE - DEMO MODE</div>
</header>

<main id="chat">

  <div class="welcome" id="welcome">
    <h2>नमस्ते! Hello!</h2>
    <p>
      मैं ARYA हूँ। आपका Personal Assistant.<br>
      आप मुझसे हिंदी या English में बात कर सकते हैं।
    </p>
  </div>

  <div class="msg bot">
    नमस्ते! मैं ARYA हूँ। आज मैं आपकी क्या सहायता कर सकता हूँ?
  </div>

</main>

<div class="controls">
  <input
    type="text"
    id="question"
    placeholder="अपना सवाल लिखें..."
    autocomplete="off"
  >
  <button onclick="send()">Send</button>
  <button class="clear" onclick="clearChat()">Clear</button>
</div>

<footer>
  ARYA AI © 2026 | Learning Version
</footer>

<script>

const chat = document.getElementById("chat");
const input = document.getElementById("question");

function addMessage(text,type){

  const div = document.createElement("div");

  div.className = "msg " + type;

  div.textContent = text;

  chat.appendChild(div);

  chat.scrollTop = chat.scrollHeight;

}

function isHindi(text){

  return /[\u0900-\u097F]/.test(text);

}

function getReply(question){

  const q = question.toLowerCase();

  const hindi = isHindi(question);

  if(hindi){

    if(q.includes("नमस्ते") || q.includes("हेलो")){
      return "नमस्ते! मैं ARYA हूँ। आप कैसे हैं? बताइए, मैं आपकी क्या सहायता करूँ?";
    }

    if(q.includes("नाम")){
      return "मेरा नाम ARYA AI है। मैं आपका Personal AI Assistant हूँ।";
    }

    if(q.includes("तुम कौन")){
      return "मैं ARYA AI हूँ, आपका Personal Assistant।";
    }

    if(q.includes("भारत")){
      return "भारत दक्षिण एशिया में स्थित एक देश है। इसकी राजधानी नई दिल्ली है।";
    }

    if(q.includes("विज्ञान")){
      return "विज्ञान प्रकृति, पदार्थ, ऊर्जा और हमारे आसपास की दुनिया का व्यवस्थित अध्ययन है।";
    }

    if(q.includes("धन्यवाद")){
      return "आपका स्वागत है! 😊";
    }

    if(q.includes("कैसे हो")){
      return "मैं बिल्कुल ठीक हूँ और आपकी सहायता के लिए तैयार हूँ!";
    }

    return "आपका सवाल मुझे मिल गया है। मैं अभी Demo Mode में हूँ, इसलिए हर सवाल का वास्तविक AI उत्तर नहीं दे सकता। असली AI सुविधा अगले चरण में जोड़ी जाएगी।";

  }else{

    if(q.includes("hello") || q.includes("hi")){
      return "Hello! I am ARYA AI. How can I help you today?";
    }

    if(q.includes("your name") || q.includes("who are you")){
      return "My name is ARYA AI. I am your personal AI assistant.";
    }

    if(q.includes("india")){
      return "India is a country in South Asia. Its capital is New Delhi.";
    }

    if(q.includes("science")){
      return "Science is the systematic study of the natural world through observation and experiments.";
    }

    if(q.includes("thank")){
      return "You're welcome! I am always ready to help.";
    }

    if(q.includes("how are you")){
      return "I am doing well! How can I assist you?";
    }

    return "I received your message! I am currently in Demo Mode. My real AI brain will be connected in a future version.";

  }

}

function send(){

  const q = input.value.trim();

  if(!q) return;

  addMessage(q,"user");

  input.value = "";

  const reply = getReply(q);

  addMessage(reply,"bot");

}

function clearChat(){

  chat.innerHTML = "";

  const welcome = document.createElement("div");

  welcome.className = "msg bot";

  welcome.textContent = "नमस्ते! Hello! मैं ARYA हूँ। How can I help you?";

  chat.appendChild(welcome);

}

input.addEventListener("keydown",function(event){

  if(event.key === "Enter"){

    send();

  }

});

</script>

</body>
</html>

