<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ARYA AI</title>
<style>
body {
  background: #101827;
  color: white;
  font-family: Arial;
  text-align: center;
  padding: 20px;
}
h1 { color: #42d9ff; }
#chat {
  margin-top: 30px;
  padding: 15px;
  background: #243650;
  border-radius: 12px;
}
input {
  padding: 12px;
  width: 65%;
  margin-top: 20px;
}
button {
  padding: 12px;
  background: #42d9ff;
  border: none;
}
</style>
</head>
<body>

<h1>✨ ARYA AI</h1>
<p>Your Personal AI Assistant</p>

<div id="chat">
नमस्ते! मैं ARYA हूँ। आपकी क्या मदद कर सकता हूँ?
</div>

<input id="msg" placeholder="अपना संदेश लिखें">
<button onclick="sendMessage()">Send</button>

<script>
function sendMessage() {
  let input = document.getElementById("msg");
  let chat = document.getElementById("chat");
  if (!input.value.trim()) return;
  chat.innerHTML += "<p>आप: " + input.value.replace(/</g, "&lt;").replace(/>/g, "&gt;") + "</p>";
  chat.innerHTML += "<p>ARYA: नमस्ते! आपका संदेश मिल गया।</p>";
  input.value = "";
}
</script>

</body>
</html># Arya-ai
