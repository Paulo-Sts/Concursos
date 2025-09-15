# Resumo: Funções de Data e Texto no Excel

## 1. Sintaxe Geral das Funções
- `=NOMEDAFUNÇÃO(argumento1; argumento2; ...)`
- Podem começar com `=` ou `@`
- Nome exato da função obrigatório
- Argumentos separados por ponto e vírgula
- Parênteses obrigatórios, mesmo sem argumentos

## 2. Funções de Data

### 2.1. Data do Sistema
- `=HOJE()`: retorna a data atual do sistema
- `CTRL+;`: insere data atual diretamente (não é função)

### 2.2. Data e Hora
- `=AGORA()`: retorna data e hora atuais do sistema

### 2.3. Componentes de Data
- `=DIA(data)`: extrai o dia (1-31) de uma data
- `=MÊS(data)`: extrai o mês (1-12) de uma data  
- `=ANO(data)`: extrai o ano de uma data

### 2.4. Cálculo entre Datas
- `=DIAS(data_final; data_inicial)`: calcula número de dias entre duas datas

## 3. Funções de Texto

### 3.1. Formatação de Texto
- `=ARRUMAR(texto)`: remove espaços excedentes, mantendo apenas espaços simples entre palavras

### 3.2. Extração de Texto
- `=DIREITA(texto; núm_caracteres)`: extrai caracteres do final do texto
- `=ESQUERDA(texto; núm_caracteres)`: extrai caracteres do início do texto
- `=EXT.TEXTO(texto; posição_início; tamanho)`: extrai trecho específico do texto

### 3.3. Combinação de Textos
- `=CONCATENAR(texto1; texto2; ...)`: une vários textos em um único (equivalente ao operador `&`)

### 3.4. Localização no Texto
- `=LOCALIZAR(texto_procurado; no_texto; posição_inicial)`: encontra posição de um texto dentro de outro (não diferencia maiúsculas/minúsculas)
- `=PROCURAR()`: similar à LOCALIZAR, mas diferencia maiúsculas/minúsculas

## 4. Exemplos Práticos

### 4.1. Extração com EXT.TEXTO
- `=EXT.TEXTO("O CARRO VERDE É NOVO"; 9; 5)` → "VERDE"
- Posição 9: início da palavra "VERDE"
- Tamanho 5: 5 caracteres a extrair

### 4.2. Combinação com CONCATENAR
- `=CONCATENAR(B2; B1; B3)` onde:
  - B2 = "CO"
  - B1 = "MI" 
  - B3 = "DA"
- Resultado: "COMIDA"

### 4.3. Extração com DIREITA e PROCURAR
- `=DIREITA(A1;PROCURAR("-";A1)-2)` onde A1 = "12345-6789"
- PROCURAR("-";A1) → posição 6 do hífen
- 6-2 = 4 caracteres a extrair do final
- Resultado: "6789"

## 5. Observações Importantes
- Funções de texto são úteis para manipulação de strings
- Funções de data facilitam cálculos temporais
- A combinação de funções permite operações complexas
- Cópia de fórmulas ajusta automaticamente as referências de células