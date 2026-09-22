# Android 2

## 1. Persistência e Armazenamento (SQLite)

### 1.1 Características do SQLite
- Definição: Banco de dados relacional embutido no Android.
- Suporte a transações: Suporta ACID (Atomicidade, Consistência, Isolamento, Durabilidade).
- Dependência de servidor: Não necessita de um servidor de banco de dados separado. É serverless.
- Instalação: Já está integrado ao sistema, não requer instalação ou configuração complexa de arquivos.
- Alternativa incorreta: O Android não usa MongoDB para armazenamento nativo (usa SQLite).

> [!CAUTION] OBSERVAÇÃO: 
> - SQLite é serverless e já vem integrado ao Android.
> - O Android não utiliza MongoDB como banco nativo.

## 2. Ciclo de Vida da Atividade (Activity Lifecycle)

### 2.1 Estados e Métodos de Callback
- O sistema operacional gerencia o estado da atividade através de uma pilha, invocando métodos de callback específicos.

| ESTADO | MÉTODO INVOCADO | DESCRIÇÃO / VISIBILIDADE |
| :--- | :--- | :--- |
| Created (Criada) | onCreate() | Estado inicial. Configuração estática (layout, dados). Não visível. Geralmente chamado uma vez. |
| Started (Iniciada) | onStart() | Prepara para ir ao primeiro plano. Atividade torna-se visível, mas ainda não interativa. |
| Resumed (Retomada) | onResume() | Atividade em primeiro plano e interativa. Está no topo da pilha. Estado principal de uso. |
| Paused (Pausada) | onPause() | Atividade parcialmente visível, mas perdeu o foco (ex: pop-up). Execução rápida. Pode ir para Stopped ou Resumed. |
| Stopped (Parada) | onStop() | Atividade não está mais visível. Ainda em memória. Pode ir para Destroyed ou Restart. |
| Destroyed (Destruída) | onDestroy() | Invocado antes da atividade ser removida da memória (finalizada pelo usuário ou sistema). |
| Reiniciada | onRestart() | Chamado quando a atividade sai do estado Stopped para voltar a ser Started. |

#### 2.1.1 Fluxo de Transição de Estados
- Abertura do app: onCreate() ⟶ onStart() ⟶ onResume().
- Chegada de um pop-up (pausa parcial): onResume() ⟶ onPause(). (Se voltar: onResume()).
- Ida para home/outro app: onPause() ⟶ onStop().
- Retorno da home (se ainda em memória): onRestart() ⟶ onStart() ⟶ onResume().
- Fechamento/encerramento: onPause() ⟶ onStop() ⟶ onDestroy().

### 2.2 Conceitos-Chave e Otimização
- Objeto Bundle:
  - Utilizado para armazenar e restaurar o estado da atividade.
  - Garante que, em situações de interrupção (rotação de tela, recriação), os dados da tela sejam preservados (ex: texto digitado).
- Boas práticas:
  - onPause(): Deve ter execução rápida. Liberar recursos mínimos. Nunca colocar operações pesadas aqui para não travar a UI.
  - onDestroy(): Momento para limpeza final de todos os recursos e observadores.
  - Se a atividade não for recriada, o método onCleared (em ViewModels) é chamado para limpar os dados.

> [!CAUTION] OBSERVAÇÃO: 
> - onPause() deve ser rápido; operações pesadas travam a interface.
> - onDestroy() é para limpeza final de recursos.
> - Bundle preserva o estado da atividade em recriações (ex: rotação de tela).