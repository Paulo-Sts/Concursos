# Vue JS – Componentes e Filtros

## 1. Vue Js
- O Vue é um framework JavaScript progressivo e declarativo, utilizado para construir interfaces de usuário complexas.
- Sua natureza progressiva permite evolução contínua da aplicação, com adição de funcionalidades ao longo do tempo.
- Pode ser empregado tanto em aplicações simples quanto complexas, devido à sua flexibilidade e adoção incremental.
- É aplicado em pequenas partes de projetos (widgets) e em aplicações de grande escala, como Single Page Applications (SPAs).
- SPAs renderizam a página apenas uma vez; à medida que o usuário interage, apenas o componente em uso é atualizado, sem recarregar a página inteira.

### 1.1 Reatividade
- O Vue é reativo, proporcionando resposta instantânea às ações do usuário.
- A reatividade é implementada através de um sistema baseado em getters e setters do JavaScript, tornando os objetos reativos.
- Mudanças de estado nos dados são respondidas de maneira eficiente e automática, resultando em interação fluida.
- Facilita o gerenciamento de estado e a sincronização entre o modelo de dados (model) e a visualização (view).

### 1.2 Componentes
- Permitem a criação de elementos reutilizáveis, evitando reescrever código do zero.
- Podem ser combinados para construir aplicações complexas.
- Estrutura básica do componente:
  - Template: HTML que define a estrutura do componente.
  - Script: JavaScript que define a lógica (métodos, dados, propriedades computadas).
  - Estilo: CSS específico para o componente, com escopo isolado.

#### 1.2.1 Exemplo Prático
- O template contém um botão com evento de clique, declarado com o prefixo "@" (ex: @click).
- Quando o botão é clicado, o método incrementCount é chamado.
- A interpolação (dados entre duas chaves) exibe valores dinâmicos, como o count.

```
<template>
  <button @click="incrementCount">Clique aqui</button>
  <p>O contador está em {{ count }}</p>
</template>

<script>
export default {
  data() {
    return {
      count: 0
    };
  },
  methods: {
    incrementCount() {
      this.count++;
    }
  }
};
</script>

<style scoped>
button {
  margin: 10px;
  padding: 5px;
}
</style>
```

- A interpolação ({{ }}) também existe em outros frameworks, como Angular, e insere dados dinâmicos no código.
- No script, data retorna um objeto com count inicializado em zero.
- O método incrementCount é acionado no clique e incrementa count.
- O estilo com scoped é aplicado apenas ao componente específico, não afetando outros componentes.

### 1.3 Arquivo Main.Js
- Ponto de entrada da aplicação Vue, geralmente chamado de main.js, index.js ou app.js.
- Responsável pela criação e montagem da instância raiz da aplicação, utilizando a função createApp.
- Processo em três etapas:
  - Importação dos módulos (createApp e o componente App);
  - Criação da aplicação com createApp(App);
  - Montagem da aplicação com .mount('#app'), especificando o elemento no DOM.

```
import { createApp } from 'vue';
import App from './App.vue';
createApp(App).mount('#app');
```

> [!CAUTION] OBSERVAÇÃO: 
> - A renderização ocorre após a execução do método mount, que especifica a localização do componente no DOM. Sem essa especificação, o componente não será renderizado.

## 2. Filtros
- Funções especiais usadas nos templates (HTML) para aplicar formatação comum de texto ou transformação de dados.
- Ajudam a manter o componente limpo, separando a transformação de dados da lógica de negócio.
- Executam ações pré-definidas, organizando o código e evitando sobrecarga de funções em um único componente.

| FILTRO | DESCRIÇÃO | USO COMUM |
|--------|-----------|-----------|
| capitalize | Capitaliza a primeira letra de uma string | Formatar nomes e títulos |
| uppercase | Transforma todo o texto em maiúsculas | Dar ênfase ou para cabeçalhos |
| lowercase | Transforma todo o texto em minúsculas | Normalizar textos |
| currency | Formata números como valores monetários | Exibir preços e custos |
| date | Formata objetos de data | Exibir datas em um formato local |
| truncate | Trunca uma string a um tamanho específico | Resumir textos longos |
| number | Formata números com delimitadores | Exibir números grandes |

### 2.1 Exemplos de Implementação
- Um objeto filter contém diversos filtros que podem ser chamados, cada um recebendo pelo menos um valor como parâmetro.
- capitalize:
  - Se o valor for falso (vazio), retorna uma string vazia;
  - Caso contrário, converte o valor para string;
  - O primeiro caractere é convertido para maiúscula com toUpperCase;
  - O método slice obtém o restante da string após a primeira posição, mantendo tudo em minúsculas.
- currency:
  - Recebe dois parâmetros: o valor e o símbolo da moeda;
  - O valor é definido como float, aceitando números decimais;
  - Se o número for zero ou inexistente, retorna uma string vazia;
  - Caso contrário, usa template string para combinar valores e formata com toFixed (duas casas decimais).
- date:
  - Recebe o valor e o formato da data como parâmetros, retornando o valor formatado.
- truncate:
  - Limita o texto a um tamanho específico;
  - Se o valor for menor ou igual ao limite, retorna o valor completo;
  - Caso contrário, retorna uma substring até o limite com reticências.
- number:
  - Recebe um valor e retorna o valor formatado de acordo com a localidade do navegador.

> [!CAUTION] OBSERVAÇÃO: 
> - Em Angular, são utilizados pipes para operações de formatação, funcionalidade não presente no Vue.
> - Plugins no Vue são usados para inclusão de funcionalidades globais, não direcionados especificamente para reutilização em vários componentes.
> - Slots no Vue distribuem conteúdo em componentes, não estando relacionados à reatividade ou efeitos colaterais.