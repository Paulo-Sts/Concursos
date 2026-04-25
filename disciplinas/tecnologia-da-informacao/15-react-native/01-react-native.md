# Anotações

# REACT NATIVE

## 1. Conceitos Fundamentais e Definição

### 1.1 O que é React Native

- **Definição:** *Framework* de desenvolvimento *mobile* ***open-source***.
- **Origem:** Desenvolvido pela equipe do **Facebook**.
- **Linguagem Base:** Permite construir aplicativos para **iOS** e **Android** utilizando **JavaScript** e a biblioteca **React**.
- **Filosofia:** "Aprenda uma vez, escreva em qualquer lugar" (*Learn once, write anywhere*).

> ### 1.1.1 Relação com React (Web)
- **Similaridade:** Compartilha características fundamentais com o React, facilitando a transição do desenvolvedor *web* para o *mobile*.
- **Diferença Estrutural:** Enquanto o React utiliza **tags HTML** (`<div>`, `<span>`) e interage com o **DOM** do navegador, o React Native utiliza **componentes específicos** que mapeiam diretamente para componentes nativos do sistema operacional (*iOS/Android*).

### 1.2 Componentes Básicos (Equivalências)

| REACT NATIVE | EQUIVALENTE WEB (REACT/HTML) | FUNÇÃO |
| :--- | :--- | :--- |
| **`<View>`** | `<div>` | *Container* básico para layout e agrupamento de outros componentes. |
| **`<Text>`** | `<p>`, `<span>`, `<h1>` | Exibição de textos. Todo texto deve estar contido em uma tag `<Text>`. |
| **`<Image>`** | `<img>` | Exibição de imagens (locais ou remotas via `uri`). |
| **`<Button>`** | `<button>` | Botão clicável com evento `onPress`. |
| **`<ActivityIndicator>`** | *Spinner/Loader* | Indicador visual de carregamento/progresso. |

## 2. Estilização (StyleSheet)

### 2.1 Abordagem e Sintaxe

- **Mecanismo:** Utiliza ***JavaScript*** para definir estilos, através do componente `StyleSheet`.
- **Sintaxe:** Similar ao **CSS**, porém com diferenças cruciais ditadas pelo *CamelCase*.
- **Regra de Nomenclatura:**
    - **Palavra única:** Mantida em minúsculo (Ex: `margin`, `width`, `color`).
    - **Palavra composta:** Utiliza ***CamelCase*** em vez de hífen.
        - `background-color` (CSS) -> `backgroundColor` (React Native).
        - `justify-content` (CSS) -> `justifyContent` (React Native).
        - `text-align` (CSS) -> `textAlign` (React Native).

### 2.2 Formas de Aplicação

- **Externa (Recomendada):** `const styles = StyleSheet.create({...})`.
- **Inline (Suportada):** `<View style={{flex: 1, justifyContent: 'center'}}>`.

## 3. Gerenciamento de Estado com Hooks

### 3.1 `useState`

- **Contexto:** Introduzido no React Native 0.59.
- **Função:** Permite **manter um estado local** em uma **função de um componente funcional** (CESGRANRIO/2023).
- **Mecânica:** Retorna um par: o valor do estado atual (`state`) e uma função para atualizá-lo (`setState`).
    - `const [count, setCount] = useState(0);`

> ### 3.1.1 Diferenciação Crucial: Props vs. State (CESPE/2019)
- **Afirmativa da Banca:** "existem dois tipos de dados que controlam um componente: **state**, definido pelo pai e fixado; e **props**, utilizado para dados que irão mudar."
- **Análise:** **ERRADO**. As definições estão **invertidas**.
- **Definição Correta:**
    - ***Props* (Propriedades):** São **definidas pelo componente pai** e são **imutáveis** (fixas) durante o ciclo de vida do componente que as recebe.
    - ***State* (Estado):** É **interno ao componente** e utilizado para os dados que **irão mudar** ao longo do tempo (ex: após interação do usuário).

## 4. Comparativo Direto: React (Web) vs. React Native (Mobile)

| CARACTERÍSTICA | REACT (WEB) | REACT NATIVE (MOBILE) |
| :--- | :--- | :--- |
| **Ambiente de Execução** | Navegadores (*Browsers*). | Plataformas Móveis (iOS, Android). |
| **Renderização** | `ReactDOM.render(<App />, document.getElementById('root'));` | `AppRegistry.registerComponent('App', () => App);` |
| **Componentes Base** | HTML e DOM (`<div>`, `<p>`, `<img>`). | Componentes Nativos (`<View>`, `<Text>`, `<Image>`). |
| **Estilização** | Arquivos **.css** importados. | `StyleSheet.create({...})` em **JavaScript**. |
| **Evento de Clique** | `onClick` | `onPress` |

## 5. Integração com APIs Externas (Fetch API)

### 5.1 Mecanismo Principal

- **Método Padrão:** Utilização da ***Fetch API*** (embutida no React Native).
- **Vantagem sobre XMLHttpRequest:** Menos verbosa e baseada em ***Promises***.
- **Funcionalidade:** Realizar requisições HTTP para buscar ou enviar dados a serviços *web* (*web services*).

### 5.2 Estrutura de uma Requisição com Fetch

- **Hooks Utilizados:** `useState` (para armazenar `data`, `loading`, `error`) e `useEffect` (para disparar a requisição no carregamento do componente).
- **Fluxo da *Promise*:**
    1.  `fetch(url)`
    2.  `.then(response => response.json())` // Converte a resposta para JSON.
    3.  `.then(data => setData(data))` // Armazena os dados no estado.
    4.  `.catch(error => setError(error))` // Captura e trata erros de rede/API.
    5.  `.finally(() => setLoading(false))` // Finaliza o estado de carregamento.

> ### 5.2.1 Tratamento de Estados de UI
- **`loading === true`:** Renderiza `<ActivityIndicator />`.
- **`error === true`:** Renderiza `<Text>Error: {error.message}</Text>`.
- **Sucesso:** Renderiza os dados recebidos (ex: `{JSON.stringify(data)}`).

### 5.3 Questão FGV/2023 (TCE-SP)

- **Enunciado:** API embutida no React Native, especializada na transferência de recursos mediante ***Promises***.
- **Resposta:** **Fetch API**.
- **Justificativa:** A palavra-chave para distinguir do `XMLHttpRequest` é o uso nativo de ***Promises***.

## 6. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **1** (FCC/2019) | **E** | React Native (Framework do Facebook para mobile com JS). |
| **2** (CESGRANRIO/2023) | **E** | `useState` mantém estado local em componente funcional. |
| **3** (CESPE/2019) | **E** | `props` = definido pelo pai (imutável); `state` = dados que mudam. |
| **4** (FGV/2023) | **B** | Fetch API (transferência de recursos mediante *Promises*). |