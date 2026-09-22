# React – Estado e Props

## 1. Props
- São uma forma de passar dados de um componente pai para um componente filho.
- As props são passadas no momento em que um componente é utilizado.
- A sintaxe para receber props em um componente funcional é `function NomeComponente(props) { return <h1>{props.nome}</h1>; }`.
- Para passar uma prop, utiliza-se a sintaxe de atributo HTML: `<Saudacao nome="Ana" />`.

### 1.1 Características das Props
- Imutabilidade:
  - Os componentes filhos não podem alterar suas próprias props.
  - O fluxo de dados é unidirecional (pai → filho).
- Tipos de dados:
  - Podem ser de qualquer tipo: strings, números, funções, objetos, arrays e até mesmo outros componentes.
- Passagem de dados:
  - São passadas como atributos em JSX.

### 1.2 Passagem de Funções como Props
- Qualquer tipo de dado pode ser passado como prop, incluindo funções.
- Exemplo de código:
```jsx
function Botao(props) {
  return <button onClick={props.onClick}>Clique aqui</button>;
}

function App() {
  function handleClick() {
    alert('Botão clicado');
  }
  return <Botao onClick={handleClick} />;
}
```
- Nesse exemplo, a função `handleClick` é passada como prop para o componente `Botao`.
- Dentro de `Botao`, a função é vinculada ao evento `onClick` do botão.

## 2. Estado (State)
- Estrutura que permite que um componente mantenha e gerencie dados que podem mudar ao longo do tempo.
- Quando o estado de um componente muda, o React re-renderiza esse componente e seus filhos automaticamente.

### 2.1 Características do Estado
- Mutável:
  - Permite que o componente reaja a interações do usuário, como cliques e entradas em campos de formulário.
- Local:
  - O estado é específico para o componente em que foi definido.
  - Não é possível acessar o estado de outro componente diretamente.
- Controlado pelo componente:
  - O componente controla como e quando o estado deve ser atualizado.

### 2.2 Gerenciamento do Estado com `useState`
- O estado é gerenciado usando o hook `useState`.
- Estrutura básica: `const [estado, setEstado] = useState(valorInicial);`
  - `estado`: variável que armazena o valor atual do estado.
  - `setEstado`: função usada para atualizar o valor do estado.
  - `valorInicial`: o valor inicial do estado.
- Ao chamar `setEstado`, o valor do estado é atualizado, substituindo o valor anterior, e o componente é re-renderizado.

### 2.3 Exemplo de Contador com `useState`
- Código exemplo:
```jsx
import React, { useState } from 'react';

function App() {
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>Você clicou {contador} vezes</p>
      <button onClick={() => setContador(contador + 1)}>
        Clique aqui
      </button>
    </div>
  );
}

export default App;
```
- Explicação:
  - O estado `contador` é inicializado com 0.
  - O parágrafo exibe o valor atual de `contador`.
  - O botão possui um evento `onClick` que, ao ser clicado, chama `setContador(contador + 1)`, incrementando o valor do estado.

> [!TIP] DICAS: 
> - A convenção de nomenclatura para a função de atualização do estado é utilizar o prefixo "set" seguido do nome da variável do estado (ex.: `setContador`).

> [!CAUTION] OBSERVAÇÃO: 
> - As props são imutáveis, enquanto o estado é mutável. Essa é uma diferença fundamental entre os dois conceitos.

## 3. Pacotes e Dependências
- Pacotes são coleções de código reutilizáveis que podem ser instalados para adicionar funcionalidades a um projeto.
- Os gerenciadores de pacotes mais utilizados no ambiente Node.js são o `npm` e o `yarn`.

### 3.1 Comandos Principais
- Instalar um pacote:
  - `npm install nome-do-pacote`
  - `yarn add nome-do-pacote`
- Iniciar um novo projeto:
  - `npm init`
  - `yarn init`
- Importar módulos ou componentes:
  - `import { componente } from 'biblioteca';`