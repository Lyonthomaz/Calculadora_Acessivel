# 🧮 Calculadora Acessível

Este é um projeto de calculadora web focado em acessibilidade, projetado para facilitar o uso por pessoas com deficiência visual. O projeto utiliza a **Web Speech API** para narração em tempo real e oferece múltiplos temas de cor para diferentes necessidades visuais.

Além disso, o projeto se conecta ao **Firebase Firestore** para salvar e consultar um histórico de cálculos, permitindo que o usuário nunca perca seus resultados.

## ✨ Funcionalidades Principais

### 1. Acessibilidade Auditiva (Text-to-Speech)
A calculadora usa a API de Síntese de Voz do navegador para fornecer feedback auditivo completo:
* **Narração de Botões:** Ao passar o mouse sobre qualquer botão (números, operadores, funções), o valor é falado em português (ex: "*" é lido como "multiplicar").
* **Narração de Resultados:** Ao pressionar "Igual", o resultado final é narrado em voz alta.
* **Feedback de Ações:** Alterar o tema de cor ou o tamanho da fonte também fornece feedback em áudio.

### 2. Acessibilidade Visual
* **Temas de Cor:** Um seletor de temas permite ao usuário escolher entre 4 modos:
    * **Padrão:** Tema claro padrão.
    * **Alto Contraste:** Tema escuro com cores de alto contraste (preto e amarelo).
    * **Deuteranopia:** Tema otimizado para daltonismo (tons de azul e turquesa).
    * **Tritanopia:** Tema otimizado para daltonismo (tons de vermelho e laranja).
* **Controle de Fonte:** O usuário pode aumentar ou diminuir o tamanho da fonte de toda a aplicação. A preferência é salva no `localStorage` do navegador.
* **Feedback de Hover:** Os botões usam um efeito de zoom (`scale`) ao passar o mouse, facilitando a identificação do item selecionado.

### 3. Histórico de Cálculos (com Firebase)
* **Salvar Cálculos:** Após obter um resultado, o usuário pode clicar em "Salvar Dados" para armazenar a expressão e o resultado no Firebase Firestore.
* **Consultar Histórico:** O botão "Consultar Dados" abre um modal que exibe uma lista de todos os cálculos salvos.
* **Carregar do Histórico:** Clicar em um item do histórico o carrega de volta no visor da calculadora.

### 4. Suporte a Teclado
A calculadora pode ser totalmente utilizada através do teclado físico, mapeando todas as teclas numéricas, operadores, "Enter" (=), "Backspace" (C) e "Delete" (AC).

## 💻 Tecnologias Utilizadas

* **HTML5:** Estrutura semântica do projeto.
* **CSS3:** Estilização, incluindo Variáveis CSS para os temas.
* **JavaScript (ES6+):** Lógica principal da calculadora e manipulação do DOM.
* **Tailwind CSS:** Framework de design para layout e responsividade.
* **Google Fonts (Inter):** Para a tipografia.
* **Web Speech API:** Para as funcionalidades de Text-to-Speech (TTS).
* **Firebase (Firestore):** Como banco de dados NoSQL para o histórico de cálculos.

## 🚀 Como Executar o Projeto

1.  Clone este repositório:
    ```bash
    git clone [https://github.com/Lyonthomaz/Calculadora_Acessivel.git](https://github.com/Lyonthomaz/Calculadora_Acessivel.git)
    ```
2.  Navegue até a pasta do projeto e abra o arquivo `index.html` em seu navegador.

### Configuração do Firebase
Para que as funções "Salvar Dados" e "Consultar Dados" funcionem, você **precisa** configurar seu próprio projeto do Firebase:

1.  Crie um projeto no [console do Firebase](https://console.firebase.google.com/).
2.  Adicione um aplicativo Web ao seu projeto.
3.  Crie um banco de dados **Firestore**.
4.  O Firebase fornecerá um objeto de configuração `firebaseConfig`.
5.  **⚠️ IMPORTANTE:** Substitua o objeto `firebaseConfig` no topo do arquivo `js/script.js` pelas credenciais do *seu* projeto.

```javascript
// Em js/script.js
const firebaseConfig = {
    apiKey: "SUA_API_KEY",
    authDomain: "SEU_AUTH_DOMAIN",
    projectId: "SEU_PROJECT_ID",
    storageBucket: "SEU_STORAGE_BUCKET",
    messagingSenderId: "SEU_MESSAGING_SENDER_ID",
    appId: "SEU_APP_ID"
};
