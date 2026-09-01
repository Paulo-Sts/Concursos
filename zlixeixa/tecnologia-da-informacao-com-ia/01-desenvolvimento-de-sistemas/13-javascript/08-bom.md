# BOM

## 1. Browser Object Model (BOM)
- O BOM é a manipulação da página que inclui o navegador como um todo.
- Diferença entre BOM e DOM:
  - DOM (Document Object Model) manipula apenas o documento ou a página;
  - BOM manipula o navegador também, interagindo com toda a janela e não apenas com o site.
- O BOM inclui o DOM, acrescentando a capacidade de interagir com o navegador.

### 1.1 O Que é BOM?
- Browser Object Model é o Modelo de Objeto do Navegador.
- É uma interface do navegador que permite que o usuário interaja com a janela do navegador, e não somente com a página.
- Inclui vários objetos e métodos essenciais para interagir com o navegador e o ambiente de execução.

## 2. Window
- O Window é o principal objeto do BOM, representando a janela do navegador.
- É o objeto global do qual outros objetos derivam.
- A janela é o objeto raiz, a base ou fundamento para os demais objetos e métodos.

### 2.1 Funções Principais do Window
- Controlar a janela do navegador (abrir, fechar, redimensionar);
- Acessar informações sobre o navegador e o sistema operacional;
- Manipular timers (cronômetros) - assunto mais cobrado em concursos;
- Gerenciar o armazenamento local e de sessão.

### 2.2 Controlar a Janela do Navegador (Abrir, Fechar, Redimensionar)
- Exemplo de abrir e fechar uma nova aba:
  - Declara-se uma variável fora das funções (ex.: `let minhaAba`) para guardar o endereço da aba aberta, pois sem isso a informação seria perdida.
  - Função de abrir: `minhaAba = window.open('https://www.example.com', '_blank')`.
    - O método `window.open` abre uma nova aba.
    - O primeiro parâmetro é o link do site.
    - O segundo parâmetro `_blank` especifica a abertura em nova aba.
  - Função de fechar: `minhaAba.close()`.
    - O método `close` fecha a aba referenciada pela variável.

### 2.3 Manipular Timers (setTimeout e clearTimeout)
- Este é o assunto mais frequente em provas de concurso.

#### 2.3.1 setTimeout
- O método `setTimeout` executa uma função (callback) após um determinado período de tempo, definido em milissegundos.
- Sintaxe: `setTimeout(() => { código }, milissegundos)`.
- Exemplo prático:
  - Um parágrafo (`<p id="message"></p>`) e dois botões (Iniciar Timeout e Cancelar Timeout).
  - Ao clicar em "Iniciar Timeout", a mensagem "Timeout iniciado - aguarde 3 segundos..." é exibida.
  - Após 3000 milissegundos (3 segundos), a mensagem é alterada para "Timeout concluído!".

```javascript
let timeoutId;
const messageElement = document.getElementById('message');

document.getElementById('startTimeout').onclick = function() {
  messageElement.textContent = "Timeout iniciado - aguarde 3 segundos...";
  timeoutId = setTimeout(() => {
    messageElement.textContent = "Timeout concluído!";
  }, 3000);
};
```

> [!TIP] DICAS:
> - O `setTimeout` aguarda o tempo estipulado para chamar a função de callback.
> - A principal diferença entre `setTimeout` e `setInterval` é que o primeiro executa a função apenas uma vez após o tempo determinado, enquanto o segundo a executa repetidamente a cada intervalo.

#### 2.3.2 clearTimeout
- O método `clearTimeout` cancela um timer previamente definido com `setTimeout`.
- Sintaxe: `clearTimeout(timeoutId)`.
- Exemplo prático:
  - Ao clicar no botão "Cancelar Timeout", a função `clearTimeout` é chamada.
  - A mensagem "Timeout cancelado." é exibida, e o timeout previamente definido não será executado.

```javascript
document.getElementById('cancelTimeout').onclick = function() {
  clearTimeout(timeoutId);
  messageElement.textContent = "Timeout cancelado.";
};
```

### 2.4 Manipular Timers (setInterval e clearInterval)

#### 2.4.1 setInterval
- O método `setInterval` executa uma função repetidamente em intervalos de tempo definidos, em milissegundos.
- Sintaxe: `setInterval(() => { código }, milissegundos)`.
- Exemplo prático:
  - Um parágrafo (`<p id="timeDisplay"></p>`) e dois botões (Iniciar Intervalo e Parar Intervalo).
  - Ao clicar em "Iniciar Intervalo", a mensagem "Intervalo iniciado - o tempo será atualizado a cada segundo." é exibida.
  - A cada 1000 milissegundos (1 segundo), a hora atual é atualizada no parágrafo usando `new Date().toLocaleTimeString()`.

```javascript
let intervalId;
const timeDisplay = document.getElementById('timeDisplay');

document.getElementById('startInterval').onclick = function() {
  timeDisplay.textContent = "Intervalo iniciado - o tempo será atualizado a cada segundo.";
  intervalId = setInterval(() => {
    let currentTime = new Date().toLocaleTimeString();
    timeDisplay.textContent = "Hora atual: " + currentTime;
  }, 1000);
};
```

#### 2.4.2 clearInterval
- O método `clearInterval` para a execução de um intervalo criado com `setInterval`.
- Sintaxe: `clearInterval(intervalId)`.
- Exemplo prático:
  - Ao clicar no botão "Parar Intervalo", a função `clearInterval` é chamada.
  - O texto " - Intervalo parado." é adicionado ao parágrafo, e a atualização da hora é interrompida.

```javascript
document.getElementById('stopInterval').onclick = function() {
  clearInterval(intervalId);
  timeDisplay.textContent += " - Intervalo parado.";
};
```

> [!CAUTION] OBSERVAÇÃO:
> - O `setTimeout` executa a função uma única vez após o tempo definido.
> - O `setInterval` executa a função repetidamente em intervalos regulares.
> - Em provas, a banca costuma explorar a diferença entre `setTimeout` e `setInterval`, assim como o uso de `clearTimeout` e `clearInterval` para cancelar os timers.

## 3. Gerenciar o Armazenamento Local e de Sessão
- O HTML5 possui APIs de armazenamento web, e a especificação Web Storage fornece mecanismos para os navegadores armazenarem pares chave/valor de forma eficiente.
- Define dois objetos principais:

| CARACTERÍSTICA | LOCALSTORAGE | SESSIONSTORAGE |
|----------------|--------------|----------------|
| Persistência | Dados permanecem até serem explicitamente removidos | Dados persistem apenas durante a sessão da página |
| Ciclo de vida | Não expiram com o fechamento da janela ou aba | Ao fechar a aba ou página, as informações são perdidas |
| Exemplo de uso | Carrinho de e-commerce (amazon) | Formulário de várias etapas |
| Escopo | Origin do documento (protocolo, porta e host) | Origin do documento |

### 3.1 localStorage
- Armazena dados de forma persistente no navegador.
- Os dados permanecem disponíveis mesmo após o fechamento do navegador, até que sejam removidos manualmente.
- Exemplo: carrinho de compras em e-commerce. O usuário pode adicionar itens, fechar o navegador e, ao retornar, as informações ainda estarão lá.

### 3.2 sessionStorage
- Os dados persistem apenas durante a sessão da página.
- Ao fechar a aba ou a página, todas as informações armazenadas são perdidas.
- Exemplo: formulário de várias etapas. Se a internet cair e a página for recarregada, as informações não se perdem. Porém, se a aba for fechada, os dados são perdidos.

> [!CAUTION] OBSERVAÇÃO:
> - O localStorage e o sessionStorage são específicos do navegador. Se o usuário mudar de navegador (ex.: Firefox para Chrome), os dados do localStorage não estarão acessíveis.
> - O escopo do localStorage é a origem do documento, definida por protocolo, porta e host. Criptografia não faz parte do escopo.