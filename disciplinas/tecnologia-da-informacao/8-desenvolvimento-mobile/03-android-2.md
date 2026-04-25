# Anotações

# DESENVOLVIMENTO DE APLICAÇÕES MÓVEIS – ANDROID II

## 1. Componentes do Aplicativo (Revisão e Questões)

### 1.1 Os Quatro Componentes Básicos (FEPESE/2022)

- **Atividades (*Activities*):** Ponto de entrada para a interação com o usuário; cada tela é uma atividade.
- **Serviços (*Services*):** Executam operações em **segundo plano**, **sem interface gráfica**.
- ***Broadcast Receivers:*** Respondem a **anúncios de transmissão** do sistema ou de outros apps.
- **Provedores de Conteúdo (*Content Providers*):** Gerenciam um **conjunto compartilhado de dados**.

### 1.2 Análise de Assertivas (Questões)

- **Aplicação Móvel Módulo Único (CESGRANRIO/2023):**
    - O módulo responsável por uma tela e sua funcionalidade é a **Atividade** (*Activity*).
- **Execução em Segundo Plano (AOCP/2019):**
    - Componente executado em *background* sem interface gráfica: **Serviços** (*Services*).
- **Assertiva FUMARC/2023:**
    - **II (Errada):** Provedor de conteúdo gerencia dados, não entrega eventos gerados por *Intents*. Quem responde a eventos/transmissões é o *Broadcast Receiver*.

### 1.3 Intents (AOCP/2020)

- **Intenção Explícita:** Usada para iniciar um componente **específico do próprio aplicativo**.
- **Intenção Implícita:** Declara uma ação geral, permitindo que **outro aplicativo** a processe.

## 2. Persistência e Armazenamento (SQLite)

### 2.1 Características do SQLite

- **Definição:** Banco de dados relacional embutido no Android.
- **Suporte a Transações:** Suporta **ACID** (Atomicidade, Consistência, Isolamento, Durabilidade).
- **Dependência de Servidor:** **Não** necessita de um servidor de banco de dados separado. É *serverless*.
- **Instalação:** Já está integrado ao sistema, **não requer instalação** ou configuração complexa de arquivos.
- **Alternativa Incorreta:** O Android **não** usa MongoDB para armazenamento nativo (usa SQLite).
- **Resposta FGV/TJ-RO:** Apenas a afirmativa **II** está correta.

## 3. Ciclo de Vida da Atividade (Activity Lifecycle)

### 3.1 Estados e Métodos de Callback

O sistema operacional gerencia o estado da atividade através de uma pilha, invocando métodos de *callback* específicos.

| ESTADO | MÉTODO INVOCADO | DESCRIÇÃO / VISIBILIDADE |
| :--- | :--- | :--- |
| **Created (Criada)** | `onCreate()` | **Estado inicial.** Configuração estática (layout, dados). Não visível. Geralmente chamado uma vez. |
| **Started (Iniciada)** | `onStart()` | Prepara para ir ao primeiro plano. Atividade torna-se **visível**, mas ainda não interativa. |
| **Resumed (Retomada)** | `onResume()` | Atividade em **primeiro plano e interativa**. Está no topo da pilha. Estado principal de uso. |
| **Paused (Pausada)** | `onPause()` | Atividade **parcialmente visível**, mas **perdeu o foco** (ex: pop-up). Execução rápida. Pode ir para Stopped ou Resumed. |
| **Stopped (Parada)** | `onStop()` | Atividade **não está mais visível**. Ainda em memória. Pode ir para Destroyed ou Restart. |
| **Destroyed (Destruída)** | `onDestroy()` | Invocado antes da atividade ser **removida da memória** (finalizada pelo usuário ou sistema). |
| **Reiniciada** | `onRestart()` | Chamado quando a atividade sai do estado *Stopped* para voltar a ser *Started*. |

> ### 3.1.1 Fluxo de Transição de Estados
- **Abertura do App:** `onCreate()` -> `onStart()` -> `onResume()`.
- **Chegada de um Pop-up (pausa parcial):** `onResume()` -> `onPause()`. (Se voltar: `onResume()`).
- **Ida para Home/Outro App:** `onPause()` -> `onStop()`.
- **Retorno da Home (se ainda em memória):** `onRestart()` -> `onStart()` -> `onResume()`.
- **Fechamento/Encerramento:** `onPause()` -> `onStop()` -> `onDestroy()`.

### 3.2 Conceitos-Chave e Otimização

- **Objeto `Bundle`:**
    - Utilizado para **armazenar e restaurar o estado** da atividade.
    - Garante que, em situações de interrupção (rotação de tela, recriação), os dados da tela sejam preservados (ex: texto digitado).
- **Boas Práticas:**
    - **`onPause()`:** Deve ter **execução rápida**. Liberar recursos mínimos. Nunca colocar operações pesadas aqui para não travar a UI.
    - **`onDestroy()`:** Momento para **limpeza final** de todos os recursos e observadores.
    - Se a atividade não for recriada, o método `onCleared` (em ViewModels) é chamado para limpar os dados.

## 4. Gabarito das Questões

| Questão | Gabarito | Observação Relevante |
| :--- | :--- | :--- |
| **01** (FEPESE/2022) | **A** | Atividades, Serviços, *Broadcast Receivers*, Provedores de Conteúdo. |
| **02** (AOCP/2021) | **C** | Definições corretas dos 4 componentes. |
| **03** (CESGRANRIO/2023) | **A** | Módulo único e autônomo = *Activity*. |
| **04** (FUMARC/2023) | **B** | I e III. *Content Provider* provê dados, não eventos de *Intent*. |
| **05** (AOCP/2019) | **B** | *Services* executam em *background* sem interface gráfica. |
| **06** (IBFC/2019) | **D** | Android usa **SQLite**, não MongoDB. |
| **07** (FGV) | **B** | SQLite suporta **ACID** (II). Não precisa de servidor separado nem instalação complexa. |
| **08** (AOCP/2020) | **B** | Definição correta de *Broadcast Receiver*. |