# React Native

## 1. Definição

### 1.1 O que é React Native
- Framework de desenvolvimento mobile open-source.
- Desenvolvido pela equipe do Facebook.
- Permite construir aplicativos para iOS e Android utilizando JavaScript e a biblioteca React.
- Filosofia: "Aprenda uma vez, escreva em qualquer lugar" (Learn once, write anywhere).

### 1.2 Relação com React (Web)
- Similaridade: compartilha características fundamentais com o React, facilitando a transição do desenvolvedor web para o mobile.
- Diferença Estrutural: enquanto o React utiliza tags HTML (`<div>`, `<span>`) e interage com o DOM do navegador, o React Native utiliza componentes específicos que mapeiam diretamente para componentes nativos do sistema operacional (iOS/Android).

## 2. Componentes e Estilização

### 2.1 Componentes Básicos (Equivalências)

| REACT NATIVE | EQUIVALENTE WEB (REACT/HTML) | FUNÇÃO |
|--------------|-------------------------------|--------|
| `<View>` | `<div>` | Container básico para layout e agrupamento de outros componentes. |
| `<Text>` | `<p>`, `<span>`, `<h1>` | Exibição de textos. Todo texto deve estar contido em uma tag `<Text>`. |
| `<Image>` | `<img>` | Exibição de imagens (locais ou remotas via `uri`). |
| `<Button>` | `<button>` | Botão clicável com evento `onPress`. |
| `<ActivityIndicator>` | Spinner/Loader | Indicador visual de carregamento/progresso. |

### 2.2 Estilização (StyleSheet)

#### 2.2.1 Abordagem e Sintaxe
- Mecanismo: utiliza JavaScript para definir estilos, através do componente `StyleSheet`.
- Sintaxe: similar ao CSS, porém com diferenças cruciais ditadas pelo CamelCase.

#### 2.2.2 Regra de Nomenclatura
- Palavra única: mantida em minúsculo (Ex: `margin`, `width`, `color`).
- Palavra composta: utiliza CamelCase em vez de hífen.
  - `background-color` (CSS) -> `backgroundColor` (React Native);
  - `justify-content` (CSS) -> `justifyContent` (React Native);
  - `text-align` (CSS) -> `textAlign` (React Native).

#### 2.2.3 Formas de Aplicação
- Externa (Recomendada): `const styles = StyleSheet.create({...})`.
- Inline (Suportada): `<View style={{flex: 1, justifyContent: 'center'}}>`.

## 3. Gerenciamento de Estado com Hooks

### 3.1 useState
- Contexto: introduzido no React Native 0.59.
- Função: permite manter um estado local em uma função de um componente funcional.
- Mecânica: retorna um par: o valor do estado atual (`state`) e uma função para atualizá-lo (`setState`).
  - `const [count, setCount] = useState(0);`

### 3.2 Diferenciação Crucial: Props vs. State

| ASPECTO | PROPS | STATE |
|---------|-------|-------|
| Definição | Definidas pelo componente pai. | Interna ao componente. |
| Mutabilidade | Imutáveis (fixas). | Mutáveis (podem mudar). |
| Uso | Dados que vêm de fora. | Dados que mudam ao longo do tempo. |
| Exemplo | Título, dados de API recebidos. | Contador, input de formulário. |

> [!TIP] DICA: 
> - Props são imutáveis e definidas pelo componente pai.
> - State é interno ao componente e utilizado para dados que irão mudar ao longo do tempo (ex: após interação do usuário).

## 4. Comparativo Direto: React (Web) vs. React Native (Mobile)

| CARACTERÍSTICA | REACT (WEB) | REACT NATIVE (MOBILE) |
|----------------|-------------|-----------------------|
| Ambiente de Execução | Navegadores (Browsers). | Plataformas Móveis (iOS, Android). |
| Renderização | `ReactDOM.render(<App />, document.getElementById('root'));` | `AppRegistry.registerComponent('App', () => App);` |
| Componentes Base | HTML e DOM (`<div>`, `<p>`, `<img>`). | Componentes Nativos (`<View>`, `<Text>`, `<Image>`). |
| Estilização | Arquivos .css importados. | `StyleSheet.create({...})` em JavaScript. |
| Evento de Clique | `onClick` | `onPress` |

## 5. Integração com APIs Externas (Fetch API)

### 5.1 Mecanismo Principal
- Método Padrão: utilização da Fetch API (embutida no React Native).
- Vantagem sobre XMLHttpRequest: menos verbosa e baseada em Promises.
- Funcionalidade: realizar requisições HTTP para buscar ou enviar dados a serviços web (web services).

### 5.2 Estrutura de uma Requisição com Fetch
- Hooks Utilizados: `useState` (para armazenar `data`, `loading`, `error`) e `useEffect` (para disparar a requisição no carregamento do componente).
- Fluxo da Promise:
  1. `fetch(url)`;
  2. `.then(response => response.json())` // Converte a resposta para JSON;
  3. `.then(data => setData(data))` // Armazena os dados no estado;
  4. `.catch(error => setError(error))` // Captura e trata erros de rede/API;
  5. `.finally(() => setLoading(false))` // Finaliza o estado de carregamento.

### 5.3 Tratamento de Estados de UI
- `loading === true`: renderiza `<ActivityIndicator />`;
- `error === true`: renderiza `<Text>Error: {error.message}</Text>`;
- Sucesso: renderiza os dados recebidos (ex: `{JSON.stringify(data)}`).