# Anotações

# REACT NATIVE – RECURSOS DE RECARREGAMENTO E COMPONENTE IMAGE

## 1. Recursos de Recarregamento ao Vivo (Hot, Live e Fast Refresh)

### 1.1 Definição Geral

- **Ferramentas de Desenvolvimento:** Permitem que os desenvolvedores visualizem as mudanças no código em **tempo real**, sem a necessidade de recompilar toda a aplicação manualmente.
- **Objetivo:** Acelerar o ciclo de desenvolvimento e facilitar a identificação de erros.

### 1.2 Comparativo Detalhado: Hot Reloading vs. Live Reloading

| CARACTERÍSTICA | HOT RELOADING | LIVE RELOADING |
| :--- | :--- | :--- |
| **Definição** | Atualiza **componentes específicos** em tempo real, injetando as novas versões sem recarregar todo o aplicativo. | **Recarrega a aplicação inteira** sempre que um arquivo é salvo. |
| **Estado da Aplicação** | **Mantém o estado atual** dos componentes. (Ex: Dados preenchidos em um formulário ou valor de um contador são preservados). | **Reinicia/Perde o estado** da aplicação a cada recarga. (Ex: Contador volta a 0). |
| **Velocidade** | **Rápido**, pois recompila e substitui apenas os módulos modificados. | **Mais lento**, devido ao *reboot* completo da aplicação. |
| **Uso Ideal** | **Ajustes finos** na UI e lógica de um componente específico (Ex: Ajustar texto, cores ou estilos de um botão). | **Alterações estruturais** que envolvem múltiplos arquivos, configurações fundamentais ou adição de novas bibliotecas. |
| **Acionamento** | **Manual** (via menu de desenvolvimento ou atalhos de teclado). | **Automático** (ao salvar o arquivo). |

### 1.3 Fast Refresh (A Evolução)

- **Definição:** Funcionalidade moderna que combina as melhores características do *Hot Reloading* e *Live Reloading*, resolvendo inconsistências dos métodos anteriores.
- **Introdução:** Integrado por padrão no React Native a partir da versão **0.61** (2019).
- **Característica Principal:** **Automático** (acionado ao salvar) e **Preserva o Estado** (mantém o estado dos componentes sempre que possível).
- **Mecanismo:** Recarrega completamente um componente apenas quando sua estrutura é modificada de forma que não seja possível preservar o estado; caso contrário, apenas aplica a atualização rápida.

> ### 1.3.1 Questão INSTITUTO CONSULPLAN/2022
- **Enunciado:** Funcionalidade que permite o programa rodar em *background* e, ao alterar o código, fazer o *build* e mostrar as alterações rapidamente na tela.
- **Gabarito:** **Hot Reloading**.
- **Observação:** Embora o *Fast Refresh* seja o padrão atual, a descrição da questão ("rapidamente", "alterações mostradas") ainda se alinha ao conceito clássico do *Hot Reloading* em contraste com o *Live Reloading* (que é lento).

## 2. Componente `<Image>`

### 2.1 Função e Sintaxe Básica

- **Função:** Componente fundamental para exibir imagens (ícones, fotos, gráficos) no React Native.
- **Propriedade Principal:** `source` (Fonte).
- **Tipos de Fonte Suportadas:**
    1.  **Imagem de Rede (Remota):** Utiliza um objeto com a propriedade `uri`.
    2.  **Imagem Local (Estática):** Utiliza a função `require()` com o caminho relativo do arquivo.

| TIPO DE IMAGEM | SINTAXE | OBSERVAÇÃO |
| :--- | :--- | :--- |
| **Rede (Remota)** | `<Image source={{ uri: 'https://...' }} />` | Requer a definição de `width` e `height` no estilo. |
| **Local (Estática)** | `<Image source={require('./caminho/icon.png')} />` | O caminho é resolvido em tempo de compilação. |

### 2.2 Propriedade `resizeMode` (Redimensionamento)

- **Função:** Controla como a imagem será ajustada ao espaço delimitado pelo componente (`style={{width: ..., height: ...}}`).

| VALOR | COMPORTAMENTO |
| :--- | :--- |
| **`cover`** | Redimensiona para **cobrir todo o espaço**, mantendo a proporção. Pode **cortar** partes da imagem se necessário. |
| **`contain`** | Ajusta a imagem **inteiramente dentro** do espaço disponível, garantindo **visibilidade total** (sem cortes). Podem sobrar espaços vazios (bordas). |
| **`stretch`** | **Estica** a imagem para preencher completamente o espaço, **distorcendo** a proporção original. |
| **`center`** | **Centraliza** a imagem no espaço disponível sem redimensionar (mantém tamanho original). |
| **`repeat`** | **Repete** a imagem como um mosaico para cobrir o espaço. |

> ### 2.2.1 Análise de Questão: FUNCERN/2024 (IF-RN)
- **Cenário:** Adicionar imagem estática `my-icon.png` localizada na **mesma pasta** do componente.
- **Sintaxe Correta:**
    ```jsx
    <Image source={require('./my-icon.png')} />
    ```
- **Análise das Alternativas:**
    - `src`: Errado. É atributo do HTML, não do React Native.
    - `require`: Deve ser passado como valor da prop `source` entre chaves `{}`.
    - Caminho: `./` indica o mesmo diretório do arquivo atual.

## 3. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **3** (CONSULPLAN/2022) | **C** | **Hot Reloading** (atualização rápida de código em tempo real). |
| **4** (FUNCERN/2024) | **D** | `<Image source={require('./my-icon.png')} />` (Sintaxe correta para imagem estática local). |