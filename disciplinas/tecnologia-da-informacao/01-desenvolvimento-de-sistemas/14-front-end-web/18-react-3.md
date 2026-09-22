# React e Hooks

## 1. Integração React com Outras Tecnologias
- O React é compatível com outras bibliotecas e frameworks, como Redux e AngularJS.
- Para integrar React com AngularJS, é necessário criar um componente React e renderizá-lo dentro de um elemento usando o método ReactDOM.render().

### 1.1 Mudança Importante no React 18
- A partir da versão 18 (2022), o método ReactDOM.render() foi substituído pelo método createRoot().
- Esta mudança representa uma atualização significativa na forma de renderizar aplicações React.

## 2. Hooks no React
- Foram introduzidos na versão 16.8 do React.
- Permitem o uso de estado e ciclo de vida em componentes funcionais.
- Substituem a necessidade de classes para gerenciar estado e efeitos colaterais.

### 2.1 Hook useState
- Permite adicionar estado a componentes funcionais.
- Retorna um array com duas posições: o valor atual do estado e uma função para atualizá-lo.
- Sintaxe:
```javascript
const [estado, setEstado] = useState(valorInicial);
```

- Componentes da sintaxe:
- estado: Variável que armazena o valor atual do estado.
- setEstado: Função usada para atualizar o valor do estado.
- valorInicial: Valor inicial do estado.
- Exemplo prático:
```javascript
import { useState } from 'react';

function ExemploContador() {
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
```

### 2.2 Hook useEffect
- Permite realizar efeitos colaterais em componentes funcionais.
- Exemplos de uso: buscar dados de uma API, atualizar o DOM, configurar temporizadores.
- Executa uma função após cada renderização (por padrão) ou apenas quando dependências específicas mudam.
- Sintaxe:
```javascript
useEffect(() => {
  // Lógica do efeito
  return () => {
    // Limpeza do efeito (opcional)
  };
}, [dependencias]);
```

- Parâmetros importantes:
- dependencias: Array opcional que define quais valores precisam mudar para o efeito ser executado novamente.
- Se o array estiver vazio ([]), o efeito só será executado uma vez, após a montagem do componente.
- Exemplo prático:
```javascript
import { useState, useEffect } from 'react';

function ExemploTitulo() {
  const [contador, setContador] = useState(0);
  
  useEffect(() => {
    document.title = `Você clicou ${contador} vezes`;
  }, [contador]);
  
  return (
    <div>
      <p>Você clicou {contador} vezes</p>
      <button onClick={() => setContador(contador + 1)}>
        Clique aqui
      </button>
    </div>
  );
}
```

### 2.3 Hook useMemo
- Memoriza o resultado de uma função computacionalmente cara.
- Evita recálculos desnecessários em cada renderização.
- Útil para otimizar performance em componentes complexos.
- Sintaxe:
```javascript
const valorMemorizado = useMemo(() => {
  return computacaoPesada(valor);
}, [valor]);
```

- Componentes da sintaxe:
- computacaoPesada: Função cujos resultados se deseja memorizar.
- valor: Valor de dependência. O cálculo será refeito apenas se esse valor mudar.
- O useMemo é um dos hooks mais importantes, frequentemente utilizado em conjunto com outros hooks.

### 2.4 Hook useCallback
- Memoriza uma função para que ela não seja recriada a cada renderização.
- A diferença fundamental: useMemo memoriza o valor retornado; useCallback memoriza a própria função.
- Útil para evitar recriação desnecessária de funções passadas para componentes filhos, evitando re-renderizações desnecessárias.
- Sintaxe:
```javascript
const funcaoMemorizada = useCallback(() => {
  // Função a ser memorizada
}, [dependencias]);
```

- Parâmetros:
  - dependencias: Lista de valores dos quais a função depende. A função será recriada apenas se algum desses valores mudar.
- Exemplo prático:
```javascript
import { useState, useCallback } from 'react';

function ExemploCallback() {
  const [contador, setContador] = useState(0);
  
  const incrementar = useCallback(() => {
    setContador((c) => c + 1);
  }, []);
  
  return (
    <div>
      <p>Você clicou {contador} vezes</p>
      <button onClick={incrementar}>
        Clique aqui
      </button>
    </div>
  );
}
```

### 2.5 Hook useContext
- Permite acessar dados compartilhados entre vários componentes sem precisar passar props manualmente por todos os níveis da árvore.
- Simplifica o compartilhamento de dados globais como temas, preferências de usuário, autenticação.
- Sintaxe:
```javascript
const valorDoContexto = useContext(NomeDoContexto);
```

- Componentes da sintaxe:
  - NomeDoContexto: O contexto criado com createContext.
  - valorDoContexto: O valor atual do contexto, que pode ser usado dentro do componente.
- Exemplo prático:
```javascript
import React, { useContext } from 'react';

const TemaContext = React.createContext('claro');

function App() {
  return (
    <TemaContext.Provider value="escuro">
      <Componente />
    </TemaContext.Provider>
  );
}

function Componente() {
  const tema = useContext(TemaContext);
  return <p>O tema atual é {tema}</p>;
}
```

## 3. Características Gerais do ReactJS
- Criado originalmente pelo Facebook e amplamente utilizado no mercado corporativo.
- Biblioteca JavaScript popular para desenvolvimento de aplicações web e dispositivos móveis.
- Permite a criação de componentes personalizados combinando HTML, CSS e JavaScript.

### 3.1 Ciclo de Vida de um Componente
- O ciclo de vida de um componente consiste em três fases principais:
  - Montagem: Quando o componente é inserido no DOM.
  - Atualização: Quando o componente é re-renderizado devido a mudanças em props ou estado.
  - Desmontagem: Quando o componente é removido do DOM.

### 3.2 Comparativo entre Hooks
| HOOK | PROPÓSITO | QUANDO USAR |
|------|-----------|-------------|
| useState | Gerenciar estado local | Para dados que mudam dentro do componente |
| useEffect | Realizar efeitos colaterais | Para operações assíncronas, manipulação do DOM |
| useMemo | Memorizar valores calculados | Para otimizar cálculos pesados |
| useCallback | Memorizar funções | Para evitar recriação de funções em componentes filhos |
| useContext | Compartilhar dados globais | Para temas, autenticação, preferências |

> [!TIP] DICAS:
> - Use useCallback quando passar funções para componentes filhos que dependem de referência estável.
> - Use useMemo para valores derivados que exigem processamento pesado e são usados em renderizações.
> - O useEffect com array vazio ([]) executa apenas uma vez, simulando componentDidMount.
> - O useEffect com dependências específicas executa sempre que essas dependências mudam.

> [!CAUTION] OBSERVAÇÃO:
> - O método ReactDOM.render() foi substituído pelo createRoot() no React 18.
> - useMemo memoriza o resultado de uma função, useCallback memoriza a função em si.
> - O ciclo de vida mencionado (montar, atualizar, desmontar) refere-se ao componente, não apenas ao effect.