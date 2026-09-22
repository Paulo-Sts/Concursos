# Operações Assíncronas e Armazenamento Local

## 1. Promises

### 1.1 Definição
- Objeto que representa a eventual conclusão (sucesso) ou falha (erro) de uma operação assíncrona.
- Função: permite tratar operações assíncronas de maneira mais previsível, encadeando ações após a conclusão ou falha, evitando o "Callback Hell".

### 1.2 Estados de uma Promise

| ESTADO | DESCRIÇÃO |
|--------|-----------|
| Pendente (Pending) | Estado inicial, ainda não resolvida nem rejeitada. |
| Resolvida (Fulfilled) | Operação concluída com sucesso. |
| Rejeitada (Rejected) | Operação concluída com falha. |

### 1.3 Estrutura e Sintaxe

| MÉTODO | FUNÇÃO |
|--------|--------|
| `new Promise((resolve, reject) => {...})` | Cria uma nova Promise. `resolve` é chamado em caso de sucesso; `reject` em caso de erro. |
| `.then(resultado => {...})` | Executa uma função quando a Promise é resolvida (sucesso). |
| `.catch(erro => {...})` | Executa uma função quando a Promise é rejeitada (falha). |

## 2. Async/Await (Açúcar Sintático)

### 2.1 Definição
- Construções de linguagem que simplificam o trabalho com Promises, permitindo escrever código assíncrono com comportamento visual síncrono (sequencial).
- Facilidade: melhora a leitura e escrita do código, evitando encadeamentos longos de `.then()`.

### 2.2 Palavras-Chave e Tratamento de Erros

| PALAVRA-CHAVE | FUNÇÃO |
|---------------|--------|
| `async` | Declara uma função assíncrona. Indica que a função retornará uma Promise. |
| `await` | Pausa a execução da função `async` até que uma Promise seja resolvida ou rejeitada. Só pode ser usada dentro de funções `async`. |
| `try...catch` | Bloco utilizado dentro da função `async` para tratar erros. O `try` tenta executar o `await`; se falhar, o `catch` captura o erro. |

> [!TIP] DICA:
> - Async/Await é "açúcar sintático" sobre Promises – não substitui Promises, mas simplifica sua escrita.
> - `await` só pode ser usado dentro de funções declaradas com `async`.

### 2.3 Exemplo Prático com Fetch API
- Contexto: interação com Web Service.
- Código Padrão:
```javascript
async function fetchData(url) {
    try {
        const response = await fetch(url); // 1. Aguarda a resposta da rede
        if (!response.ok) { // 2. Verifica se o status HTTP é de sucesso (200-299)
            throw new Error(`HTTP error! Status: ${response.status}`);
        }
        const data = await response.json(); // 3. Aguarda a conversão para JSON
        console.log(data);
    } catch (error) {
        console.error("Erro ao buscar dados:", error);
    }
}
```

## 3. Armazenamento Local Persistente (AsyncStorage)

### 3.1 Definição e Características
- Interface para armazenar dados localmente no dispositivo móvel de forma persistente.
- Persistência: os dados não são perdidos quando o aplicativo é fechado ou o dispositivo é reiniciado.
- Modelo de Dados: baseado em Chave-Valor (similar ao LocalStorage da Web).

### 3.2 Características Técnicas

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| Assíncrono | Operações de leitura/escrita não bloqueiam a thread principal da interface do usuário (UI). |
| Não Encriptado | Os dados NÃO são criptografados por padrão. Para dados sensíveis (ex: token), é necessário implementar criptografia manualmente ou usar soluções mais seguras (ex: Keystore). |
| Baseado em Chave-Valor | Cada dado é salvo associado a uma chave única (string). |

> [!CAUTION] OBSERVAÇÃO: 
> - AsyncStorage não é criptografado por padrão – dados sensíveis exigem tratamento adicional.
> - AsyncStorage é assíncrono – as operações não bloqueiam a UI.

### 3.3 Principais Métodos da API

| MÉTODO | FUNÇÃO | EXEMPLO |
|--------|--------|---------|
| `setItem()` | Salva/Atualiza um par chave-valor. | `await AsyncStorage.setItem('chave', 'valor');` |
| `getItem()` | Recupera o valor associado a uma chave. | `const valor = await AsyncStorage.getItem('chave');` |
| `removeItem()` | Remove um item específico. | `await AsyncStorage.removeItem('chave');` |
| `clear()` | Apaga todos os dados do armazenamento. | `await AsyncStorage.clear();` |

### 3.4 Fluxo de Implementação (Exemplo Didático)
1. Importação: `import AsyncStorage from '@react-native-async-storage/async-storage';`
2. Salvar Dados:
   - Envolver `await AsyncStorage.setItem('@app_key', inputValue)` em um bloco `try...catch`.
3. Carregar Dados:
   - Envolver `const value = await AsyncStorage.getItem('@app_key')` em um bloco `try...catch`.
   - Verificar se `value !== null` antes de usar.
4. Integração com UI:
   - Utilizar `useEffect` com array de dependências vazio (`[]`) para carregar os dados salvos apenas uma vez, na inicialização da tela.
   - Utilizar `useState` para refletir os valores salvos na interface (`TextInput`, `Text`).