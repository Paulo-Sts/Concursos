# Anotações

# TYPESCRIPT II

## 1. Conceitos Fundamentais

### 1.1 Definição e Natureza

- **TypeScript** é um ***superset*** (superconjunto) sintático de **JavaScript**.
- **Criador:** **Microsoft**.
- **Funcionalidade Principal:** Adiciona **tipagem estática** ao JavaScript.
- **Linguagem:** É uma linguagem **compilada** (ou *transpilada*), diferentemente do JavaScript, que é uma linguagem de *script* interpretada.
- **Arquivo:** `.ts` (TypeScript) é convertido para `.js` (JavaScript) através do compilador `tsc` (*TypeScript Compiler*).

> ### 1.1.1 Relação com JavaScript (FCC/2018)
- **Compatibilidade:** **Qualquer código JavaScript é perfeitamente aceito** em um programa TypeScript. Isso ocorre porque TypeScript é um superconjunto (tudo que é JS, é TS, mas o contrário não é verdadeiro devido às tipagens).

### 1.2 Tipagem Estática vs. Dinâmica

| CARACTERÍSTICA | TYPESCRIPT | JAVASCRIPT |
| :--- | :--- | :--- |
| **Tipo de Tipagem** | **Estática** (Forte) | **Dinâmica** (Fraca) |
| **Momento da Verificação** | **Tempo de Compilação** (*Compile-time*) | **Tempo de Execução** (*Runtime*) |
| **Detecção de Erros de Tipo** | **Antes** da execução do código. | **Durante** a execução do código (ou não detecta). |

- **Exemplo Prático:**
    - **Código:** `function somar(a: number, b: number) { return a + b; } console.log(somar(3, "5"));`
    - **TypeScript:** **Erro na compilação**. O argumento `"5"` (string) não é atribuível ao parâmetro `b` (number).
    - **JavaScript:** Executa sem erros de tipo. Resultado: `"35"` (concatenação) ou comportamento inesperado.

## 2. Funcionamento do Compilador TypeScript (Transpiler)

### 2.1 Processo de Compilação (Transpilação)

- **Mecanismo:** O código TypeScript (`.ts`) é passado pelo compilador **`tsc`**, que **remove todas as tipagens** e gera um código **JavaScript puro** (`.js`).
- **Termo Técnico:** Esse processo de tradução de uma linguagem de alto nível para outra de nível similar é chamado de ***Transpilação*** (*Translate + Compile*).

### 2.2 Comportamento na Presença de Erros

- **Regra de Ouro:** O TypeScript **NUNCA altera o comportamento de execução** do programa com base nos tipos inferidos.
- **Configuração Padrão vs. Estrita:**
    - Por padrão, mesmo que o TypeScript **alerte sobre erros de tipo** durante a compilação, ele **ainda assim gerará o arquivo `.js`** (a menos que configurado em modo estrito com `--noEmitOnError`).
    - Isso significa que os erros de tipo não impedem a geração do JavaScript, mas alertam o desenvolvedor sobre inconsistências.

> ### 2.2.1 Análise de Questões CESPE/QUADRIX
- **CESPE/2025 (TRF 6ª Região):** "Assim como no JavaScript, erros de tipagem de variáveis no TypeScript somente são identificados em tempo de execução do código."
    - **Análise:** **ERRADO**. A principal diferença do TypeScript é a identificação de erros de tipo em **tempo de compilação**.
- **QUADRIX/2024:** "Uma característica do TypeScript é o suporte a tipos estáticos, isto é, as variáveis [...] têm tipos definidos em tempo de compilação."
    - **Análise:** **CERTO**. Define precisamente o conceito de tipagem estática.
- **FUNDATEC/2023:** Afirmativa INCORRETA: "É baseada em tipagem dinâmica...".
    - **Análise:** TypeScript é baseado em **tipagem estática**.

### 2.3 Ausência de Overhead de Runtime

- **Bibliotecas:** O TypeScript **não adiciona** nenhuma biblioteca extra em tempo de execução.
- **Ambiente:** O código gerado é JavaScript padrão e será executado nos mesmos ambientes (*browsers*, Node.js) sem necessidade de um *runtime* específico do TypeScript.

## 3. Frameworks e Ecossistema TypeScript

### 3.1 Principais Adotantes

| FRAMEWORK/BIBLIOTECA | RELAÇÃO COM TYPESCRIPT |
| :--- | :--- |
| **Angular** | **Linguagem Oficial e Obrigatória**. Totalmente escrito em TypeScript. |
| **React** | **Suporte Nativo e Amplamente Utilizado**. Pode ser usado com JS ou TS. |
| **Vue.js** | **Suporte Aprimorado** a partir da versão 3 (API de Composição). |
| **Ionic** | Utiliza TypeScript junto com Angular para desenvolvimento de apps híbridos. |

### 3.2 Questão CESGRANRIO/2021 (Banco do Brasil)

- **Afirmativas:**
    - I - Angular é um framework e plataforma baseada em TypeScript. (**CERTO**)
    - II - React é uma *library* baseada em JavaScript. (**CERTO**)
    - III - Angular e React são *open source*. (**CERTO**)
- **Gabarito:** I, II e III.

## 4. Revisão de Questões Correlatas (FGV/2025 - TCE-PI)

| AFIRMATIVA DA QUESTÃO | ANÁLISE E CORREÇÃO |
| :--- | :--- |
| *"O Bootstrap utiliza jQuery ao invés de Sass..."* | **ERRADO**. O Bootstrap utiliza **Sass** para modularização. |
| *"O AJAX foi originalmente concebido com JSON, porém agora é mais utilizado com XML..."* | **ERRADO**. A ordem está invertida. AJAX = *Asynchronous JavaScript And **XML***. Hoje usa-se mais **JSON**. |
| *"Mostrar ou ocultar partes de componentes [...] é a principal característica do modelo PWA."* | **ERRADO**. Essa é a característica de uma **SPA** (*Single Page Application*). |
| *"SPA tem como maior objetivo oferecer experiência [...] semelhante à de um aplicativo nativo..."* | **ERRADO**. Esse é o objetivo do **PWA** (*Progressive Web App*). |
| *"TypeScript é uma linguagem [...] fortemente tipada [...] detecção de erros antes da execução."* | **CERTO**. É a definição precisa da linguagem. |

## 5. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FGV/2025) | **E** | TypeScript é fortemente tipado e detecta erros antes da execução. |
| **02** (QUADRIX/2024) | **C** | TypeScript suporta **tipos estáticos** (verificação em tempo de compilação). |
| **03** (FUNDATEC/2023) | **C** | **Incorreta**. TypeScript é baseado em tipagem **estática**, não dinâmica. |
| **04** (FCC/2018) | **B** | Sequência: V (Ionic), F (Node.js é *server-side*), V (JS é válido em TS). |
| **05** (CESPE/2025) | **E** | TypeScript identifica erros em tempo de **compilação**. |
| **06** (CESGRANRIO/2021) | **D** (I, II, III) | Angular (TS), React (JS), ambos *open source*. |