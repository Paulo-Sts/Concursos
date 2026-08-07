# AJAX

## 1. Introdução ao Ajax
- O Ajax é uma técnica de desenvolvimento web que permite a criação de aplicações interativas e responsivas.
- O termo significa Asynchronous JavaScript and XML.
- As requisições assíncronas ocorrem quando há uma página já carregada no browser e, em segundo plano, ocorrem requisições ao servidor sem recarregar a página.
- O Ajax pode ser entendido como uma coleção de tecnologias básicas:
  - HTML;
  - CSS;
  - JS (DOM);
  - Ajax;
  - XML (JSON).
- Atualmente, trabalha-se com Ajax utilizando o JSON, formato mais simples para escrever dados (listas, objetos etc.).
- Outro formato possível é o XML, que utiliza tags personalizadas e validação de arquivo.
- O XML é mais poderoso que o JSON, porém é muito mais burocrático.
- As primeiras definições do Gmail foram construídas usando JavaScript rico, o que caracteriza o modelo de requisições assíncronas do Ajax.

> [!TIP] DICAS: 
> - Ajax não é uma linguagem de programação, mas sim uma técnica que combina várias tecnologias.
> - A principal característica do Ajax é a atualização de partes da página sem recarregá-la completamente.

> [!CAUTION] OBSERVAÇÃO: 
> - O Ajax utiliza JavaScript, não Java. Java é uma linguagem usada com serviços web, enquanto JavaScript é executado no browser.

## 2. Processo do Ajax
- O Ajax permite enviar e receber dados do servidor de forma assíncrona, sem interromper a experiência do usuário.
- O fluxo de trabalho ocorre de forma fluida, sem interrupções ou novos carregamentos da página.
- O processo segue os seguintes passos:
  - No navegador, é feita uma requisição que inicia a ação;
  - No JavaScript, é feita uma ação de solicitação dos dados assíncronos ao servidor;
  - O servidor envia a resposta;
  - Obtendo a resposta, o JavaScript atualiza o DOM (página) com os dados novos.

## 3. Componentes do Ajax
- Utiliza combinações de HTML e CSS para a apresentação.
- Utiliza o DOM (Document Object Model) para interação dinâmica.
- Utiliza JavaScript para lógica de aplicação.
- Utiliza o objeto XMLHttpRequest para comunicação com o servidor.

### 3.1 Document Object Model (DOM)
- O DOM é o modelo do objeto do documento ao acessar uma página na web.
- Há uma série de APIs, JS, tags, HTML etc. que compõem o DOM.
- O DOM é manipulado por meio do JavaScript.

### 3.2 XMLHttpRequest (XHR)
- O XMLHttpRequest é uma API disponível em navegadores web que fornece funcionalidades cliente-servidor.
- Pode ser usado para enviar e receber dados de um servidor após a página ter sido carregada, atualizando sem recarregá-la (XHR assíncrono).
- O XHR é uma classe disponível no DOM.

## 4. Ajax na Prática (Frontend)
- O frontend é composto por um documento HTML com título "Ajax".
- A página contém basicamente duas tags: um button com o conteúdo "carregar dados" e uma div com id "resultado".
- No JavaScript, é chamado um document (DOM) e acrescentado um ouvinte ("DOMContentLoaded") para quando a página for carregada.
- A função pega o elemento "getElementById" que contém "loadData" (botão) e acrescenta o ouvinte "click".
- No momento do clique, uma função é disparada:
  - Instancia-se um objeto da classe XMLHttpRequest, fazendo uma requisição assíncrona (Ajax).
  - O método "open" indica que se faz uma requisição usando o método get do HTTP para a URL, tratando-se de uma requisição assíncrona.
  - Primeiro é necessário configurar tudo: método HTTP, URL, se a requisição será assíncrona e o que será feito quando finalizar.
- Na div aparece "dados carregados com sucesso" sem a necessidade de carregamento completo da página.

### 4.1 Exemplo de Código Frontend
```javascript
document.addEventListener("DOMContentLoaded", function() {
  document.getElementById("loadData").addEventListener("click", function() {
    var xhr = new XMLHttpRequest();
    xhr.open("GET", "http://localhost:3000/data", true);
    xhr.onreadystatechange = function() {
      if (xhr.readyState == 4 && xhr.status == 200) {
        document.getElementById("resultado").innerHTML = "Dados carregados com sucesso";
      }
    };
    xhr.send();
  });
});
```

> [!TIP] DICAS: 
> - O evento "DOMContentLoaded" garante que o JavaScript só seja executado após o carregamento completo do DOM.
> - O terceiro parâmetro do método open (true) indica que a requisição será assíncrona.

## 5. XMLHttpRequest na Prática (Backend)
- O backend é um serviço feito em node.js que responde às requisições Ajax.

### 5.1 Exemplo de Código Backend (node.js)
```javascript
const http = require('http');
const server = http.createServer((req, res) => {
  res.writeHead(200, {'Content-Type': 'application/json'});
  res.end(JSON.stringify({ message: 'Dados carregados com sucesso' }));
});
server.listen(3000);
```

## 6. Métodos e Propriedades do XMLHttpRequest

### 6.1 Método open
- Configura a requisição Ajax.
- Parâmetros:
  - Método HTTP (ex: GET, POST);
  - URL da requisição;
  - Boolean indicando se a requisição é assíncrona (true) ou síncrona (false).

### 6.2 Propriedade onreadystatechange
- Propriedade fundamental para compreender o fluxo da requisição.
- Quando o readyState muda, a função atribuída a esta propriedade é executada.
- Verifica se o readyState é 4 e o status é 200 para considerar a requisição concluída com sucesso.

### 6.3 Propriedade responseText
- Contém a resposta do servidor em formato de texto.
- É o campo utilizado para acessar a resposta enviada pelo servidor.

### 6.4 Método send
- Envia a requisição ao servidor.

## 7. Propriedade readyState
- Representa o estado da requisição do objeto XMLHttpRequest.
- É essencial para gerenciar requisições e respostas Ajax.

### 7.1 Estados do readyState
| VALOR | ESTADO | DESCRIÇÃO |
|-------|--------|-----------|
| 0 | Unsent | Um cliente foi criado, mas o método open() não foi chamado ainda |
| 1 | Opened | O método open() foi chamado |
| 2 | Headers received | O método send() foi chamado e os cabeçalhos e status estão disponíveis |
| 3 | Loading | Baixando e responseText contém os dados parciais |
| 4 | Done | Operação concluída |

> [!TIP] DICAS: 
> - readyState 4 e status 200 indicam que a requisição foi concluída com sucesso.
> - O XMLHttpRequest possui 5 estágios (0 a 4) em todos os navegadores.

> [!CAUTION] OBSERVAÇÃO: 
> - O XMLHttpRequest é igual para todos os browsers, possuindo 5 estágios.
> - O status 200 indica sucesso na requisição.

## 8. JSON (JavaScript Object Notation)
- É um formato leve de troca de dados.
- É fácil para humanos lerem e escreverem e fácil para máquinas parsearem e gerarem.
- Tornou-se o formato mais popular para troca de dados assíncrona devido à sua simplicidade e natividade com JavaScript.

### 8.1 Vantagens do JSON
- Facilmente utilizado com JavaScript no cliente sem necessidade de parsing ou serialização complexa.
- Suporta estruturas de dados básicas como objetos e arrays, facilitando a modelagem de dados complexos.

### 8.2 Métodos da API JSON
- JSON.parse: transforma uma string em um objeto JavaScript (deve estar no formato JSON).
- JSON.stringify: transforma um objeto JavaScript em uma string JSON.

## 9. XML (eXtensible Markup Language)
- É um formato que define um conjunto de regras para codificação de documentos de forma legível tanto por humanos quanto por máquinas.
- Historicamente popular para Ajax, mas tem sido gradualmente substituído por JSON.

### 9.1 Vantagens do XML
- Estruturado e extensível, permitindo a definição de tags personalizadas.
- Suporta namespaces, facilitando a integração de diferentes sistemas e padrões.

> [!TIP] DICAS: 
> - Embora o XML seja mais poderoso que o JSON, o JSON é mais utilizado atualmente devido à sua simplicidade.
> - O formato JSON é nativo do JavaScript, o que facilita seu uso em aplicações web.

> [!CAUTION] OBSERVAÇÃO: 
> - O campo responseText do XMLHttpRequest é utilizado para acessar a resposta do servidor, seja em JSON ou XML.
> - Para trabalhar com JSON, utiliza-se JSON.parse() para converter a string recebida em objeto JavaScript.