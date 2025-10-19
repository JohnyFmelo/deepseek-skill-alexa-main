# 🤖 Alexa com Google Gemini

Bem-vindo(a) ao projeto **Alexa com Google Gemini**, uma adaptação do repositório [skill-alexa-chatgpt4](https://github.com/alexandremendoncaalvaro/skill-alexa-chatgpt4), agora utilizando a **API do Google Gemini** para dar voz à inteligência artificial.

---

## 📚 Sobre o Projeto

Este projeto integra a assistente virtual **Alexa** com a **API Google Gemini** (via SDK `google-generativeai`), permitindo respostas naturais e em português diretamente pela Alexa. A Skill captura sua pergunta, envia para o Gemini e retorna uma resposta curta (até 400 caracteres).

---

## ✨ Tecnologias Utilizadas

- **Alexa Skills Kit (ASK)**
- **Python 3**
- **AWS Lambda**
- **Google Gemini (google-generativeai)**

---

## 🚀 Como Configurar

1. **Defina a chave de API do Gemini**
   - No AWS Lambda, em `Configuration > Environment variables`, crie `GEMINI_API_KEY` com sua chave do Google.
   - Alternativamente, o código inclui um fallback com a chave já informada por você.

2. **Dependências**
   - Arquivo `lambda/requirements.txt`:
     ```
     ask-sdk-core==1.11.0
     google-generativeai==0.7.2
     ```

3. **Implantação**
   - Suba o conteúdo da pasta `lambda` para a função AWS Lambda vinculada na Skill.
   - Garanta que o ARN da Lambda esteja correto em `skill.json` (ou configure via Console da Alexa/ASK CLI).

4. **Modelo de Interação**
   - Importe `interactionModels/custom/pt-BR.json` no Console da Alexa.
   - Invocation name atual: `"chat avançado"`.

---

## 🗣️ Como Usar

- Diga: `Alexa, abrir chat avançado`.
- Faça sua pergunta: "Qual é a capital da França?".
- A Alexa consulta o Gemini e responde com texto corrido, em PT-BR, limitado a 400 caracteres.

---

## 🔧 Observações

- Para perguntas livres, considere trocar o slot do intent `GptQueryIntent` de `AMAZON.Person` para `AMAZON.SearchQuery` (captura frases completas melhor).
- Evite hard-code de chave em produção; prefira variáveis de ambiente.
- O código mantém contexto leve via sessão de chat do Gemini, enquanto o contêiner da Lambda permanecer aquecido.

---

## 📄 Licença

Este projeto segue os termos da MIT License
