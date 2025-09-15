# Resumo: Excel 365 - Funções Estatísticas

## 1. Funções de Extremos

### 1.1. Valores Mínimos e Máximos
- `=MINIMO(intervalo)`: retorna o menor valor numérico
- `=MENOR(intervalo; k)`: retorna o k-ésimo menor valor (ex: 2º menor)
- `=MAXIMO(intervalo)`: retorna o maior valor numérico
- `=MAIOR(intervalo; k)`: retorna o k-ésimo maior valor (ex: 3º maior)

### 1.2. Versões Condicionais
- `=MAXIMOSES(intervalo_máximo; int_crit1; crit1; ...)`: maior valor que atende a critérios
- `=MINIMOSES()`: menor valor que atende a critérios (lógica similar)

## 2. Funções de Contagem

### 2.1. Contagem Básica
- `=CONT.NÚM(intervalo)`: conta células com valores numéricos
- `=CONT.VALORES(intervalo)`: conta células não vazias (qualquer conteúdo)
- `=CONTAR.VAZIO(intervalo)`: conta células vazias

### 2.2. Contagem Condicional
- `=CONT.SE(intervalo; critério)`: conta células que atendem a UM critério
- `=CONT.SES(int_crit1; crit1; int_crit2; crit2; ...)`: conta linhas onde TODOS os critérios são verdadeiros

## 3. Funções de Média

### 3.1. Média Aritmética
- `=MÉDIA(intervalo)`: calcula média (soma/quantidade)
- Considera apenas células numéricas (inclui zero)
- Equivalente a: `=SOMA(intervalo)/CONT.NÚM(intervalo)`

### 3.2. Médias Condicionais
- `=MÉDIASE(intervalo; critério)`: média quando UM critério é atendido
- `=MÉDIASES(int_média; int_crit1; crit1; int_crit2; crit2; ...)`: média quando TODOS os critérios são atendidos

## 4. Função Mediana
- `=MED(intervalo)`: calcula o valor central da distribuição
- Para quantidade ímpar: valor central
- Para quantidade par: média dos dois valores centrais
- Requer ordenação prévia dos valores

## 5. Exemplos Práticos

### 5.1. MÉDIASES com Múltiplos Critérios
- `=MÉDIASES(D2:D1001; B2:B1001;">18"; C2:C1001;"Centro")`
- Calcula média da renda (D) onde:
  - Idade (B) > 18
  - Bairro (C) = "Centro"

### 5.2. Cálculo de Mediana
- Valores: 1000, 2000, 5000, 6000
- `=MED(A1:A4)` → (2000+5000)/2 = 3500

## 6. Observações Importantes
- Funções com "SE" usam um critério; com "SES" usam múltiplos critérios
- Critérios textuais devem estar entre aspas: `"Centro"`, `">5"`
- Funções ignoram automaticamente células não numéricas
- Mediana não é afetada por valores extremos (diferente da média)
- CONT.VALORES conta células com qualquer conteúdo (texto, números, fórmulas)
- CONT.NÚM conta apenas células com valores numéricos