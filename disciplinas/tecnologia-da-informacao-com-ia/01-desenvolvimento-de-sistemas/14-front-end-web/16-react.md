# React, Jsx, Dom Virtual, Componentes

## 1. React
- Biblioteca JavaScript desenvolvida pelo Facebook em 2013.
- Popularmente usada no desenvolvimento de UIs (user interface/interface de usuário).
- Amplamente usada para criar SPAs (Single Page Applications), que são sites com uma única página contendo vários componentes atualizados dinamicamente a cada interação do usuário.
- JavaScript é a linguagem utilizada no desenvolvimento da biblioteca.

### 1.1 Principais Características
- Baseada em componentes: cada componente pode ter sua própria lógica e renderização, sendo reutilizável e combinável com outros componentes.
- Declarativa: foca no que fazer e não no como fazer (imperativa). Descreve-se o que deve ser exibido e o React cuida da atualização da interface com base nas mudanças de estado e dados.
- Foco apenas na camada de visualização (UI), preocupando-se exclusivamente com a parte visível ao usuário.

> [!TIP] DICAS: 
> - React é declarativo, não imperativo. Isso significa que você descreve a interface desejada e o React se encarrega de atualizar o DOM para refletir esse estado.
> - React se preocupa apenas com a camada de visualização (UI).

> [!CAUTION] OBSERVAÇÃO: 
> - React não manipula diretamente o DOM real; utiliza um DOM Virtual para otimizar as atualizações.

## 2. Jsx (JavaScript Syntax Extension)
- Extensão de sintaxe do JavaScript que permite escrever elementos HTML dentro de um arquivo JavaScript.
- Permite definir o que será exibido na interface de usuário de maneira mais fácil e intuitiva.
- O JSX é convertido em chamadas de funções JavaScript que criam os elementos do Virtual DOM.
- Exemplo de comparação entre JSX e JavaScript puro:
```jsx
// JSX
function Saudacao(props) {
  return <h1>Olá, {props.nome}!</h1>;
}

// JavaScript puro
function Saudacao(props) {
  return React.createElement("h1", null, "Olá, ", props.nome, "!");
}
```
  - No JavaScript puro, a função React.createElement recebe três parâmetros:
    - O nome do elemento a ser criado (h1);
    - As propriedades do elemento (null, caso não haja);
    - Os children, ou seja, o conteúdo entre as tags.
- O JSX não é de uso obrigatório no React; é possível utilizar o createElement da biblioteca React diretamente.

> [!TIP] DICAS: 
> - O JSX facilita a escrita e a adição de HTML no React, tornando o código mais conciso e legível.

> [!CAUTION] OBSERVAÇÃO: 
> - O JSX não é obrigatório; o React pode ser utilizado com JavaScript puro através de React.createElement.

## 3. Dom Virtual (Virtual Document Object Model)
- O DOM (Document Object Model) é uma representação em árvore de uma página web, construída na memória com todos os elementos, tags e seus filhos.
- O DOM Virtual é uma cópia em memória do DOM real, que o React mantém para otimizar as atualizações.
- Funcionamento do DOM Virtual:
  - O React mantém uma versão em memória do DOM real.
  - Quando o estado de um componente muda, o React atualiza o DOM Virtual.
  - O React compara a nova versão do DOM Virtual com a versão anterior (diffing).
  - Apenas as partes que foram alteradas são atualizadas no DOM real (reconciliação).
- Esse método de renderização otimizada evita re-renderizações desnecessárias e torna o React mais eficiente.

> [!TIP] DICAS: 
> - O DOM Virtual é o que torna o React eficiente, pois evita que todo o DOM seja recarregado a cada pequena alteração.

> [!CAUTION] OBSERVAÇÃO: 
> - O React manipula o DOM Virtual, e não o DOM real diretamente. As atualizações no DOM real são feitas de forma otimizada.

## 4. Componentes
- São blocos de construção da interface do usuário, representando partes isoladas e reutilizáveis.
- Podem ser combinados com outros componentes para formar a interface completa.
- No React, os componentes podem ser funcionais ou de classe.

### 4.1 Componentes Funcionais
- Definidos como funções JavaScript que recebem propriedades (props) como argumento.
- Retornam elementos JSX que serão renderizados na tela.
- São mais fáceis e simples de entender.
- Após a introdução de hooks (React 16.8), podem gerenciar estados e ciclo de vida.
- Exemplo:
```jsx
function Saudacao(props) {
  return <h1>Olá, {props.nome}!</h1>;
}
```

### 4.2 Componentes de Classe
- Antes da introdução dos hooks, eram a única forma de lidar com estado e métodos de ciclo de vida.
- Necessitam do método obrigatório render(), que retorna o JSX a ser exibido na tela.
- Devem herdar de React.Component, que é a classe base para criação de componentes no React.
- Exemplo:
```jsx
class Saudacao extends React.Component {
  render() {
    return <h1>Olá, {this.props.nome}!</h1>;
  }
}
```

> [!TIP] DICAS: 
> - Componentes funcionais são a forma mais moderna e recomendada de se criar componentes, especialmente com o uso de hooks.

> [!CAUTION] OBSERVAÇÃO: 
> - Em componentes de classe, o método render() é obrigatório. Sem ele, o componente não funciona.

### 4.3 Props (Propriedades)
- São argumentos passados para os componentes, funcionando de forma similar a parâmetros de funções em JavaScript ou atributos em HTML.
- Permitem que os componentes sejam dinâmicos e reutilizáveis com diferentes dados.

| TIPO DE COMPONENTE | DEFINIÇÃO | MÉTODO OBRIGATÓRIO | GERENCIAMENTO DE ESTADO |
|--------------------|-----------|--------------------|--------------------------|
| Funcional          | Função JavaScript que recebe props e retorna JSX | Nenhum | Com hooks (useState, useEffect) |
| De classe          | Classe que herda de React.Component | render() | Através de this.state e this.setState |

> [!CAUTION] OBSERVAÇÃO: 
> - A função createRoot() e seu método render() são utilizados para renderizar o componente principal no DOM, por exemplo: root.render(<App />).