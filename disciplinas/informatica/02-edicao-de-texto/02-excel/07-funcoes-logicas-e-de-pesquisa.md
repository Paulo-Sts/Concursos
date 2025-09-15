Aqui está um resumo estruturado em markdown das funções lógicas e de pesquisa do Excel, com base no conteúdo fornecido:

```markdown
# Funções Lógicas e de Pesquisa - Excel

## 1. Funções Lógicas

### 1.1. Função E()
- **Sintaxe**: `=E(exp1; exp2; exp3)`
- **Funcionamento**: Retorna VERDADEIRO apenas se TODAS as expressões forem verdadeiras
- **Exemplo**: `=E(A2>A3; A2<A4)`

### 1.2. Função OU()
- **Sintaxe**: `=OU(exp1; exp2; exp3)`
- **Funcionamento**: Retorna VERDADEIRO se PELO MENOS UMA expressão for verdadeira
- **Exemplo**: `=OU(A2>A3; A2<A4)`

### 1.3. Função NÃO()
- **Sintaxe**: `=NÃO(exp)`
- **Funcionamento**: Inverte o valor lógico (VERDADEIRO ↔ FALSO)
- **Exemplo**: `=NÃO(A2+A3=24)`

### 1.4. Função SE()
- **Sintaxe**: `=SE(condição; resultado_se_verdadeiro; resultado_se_falso)`
- **Funcionamento**: Testa uma condição e retorna resultados diferentes
- **Exemplo aninhado**: 
```excel
=SE(B4<6; "RECUPERAÇÃO"; SE(B4<9; "PROVA FINAL"; "APROVADO"))
```

### 1.5. Função SES()
- **Sintaxe**: `=SES(critério1; resultado1; critério2; resultado2; ...)`
- **Funcionamento**: Retorna o resultado do PRIMEIRO critério verdadeiro
- **Vantagem**: Substitui múltiplas funções SE aninhadas

## 2. Funções de Pesquisa

### 2.1. PROCV() - Procura Vertical
- **Sintaxe**: `=PROCV(valor_procurado; matriz; coluna_desejada; [aproximada])`
- **Características**:
  - Busca na PRIMEIRA coluna da matriz
  - `FALSO`: busca exata | `VERDADEIRO`: busca aproximada
- **Exemplo**: `=PROCV("Luz"; A4:E9; 4; FALSO)`

### 2.2. PROCH() - Procura Horizontal
- **Sintaxe**: `=PROCH(valor_procurado; matriz; linha_desejada; [aproximada])`
- **Funcionamento**: Similar ao PROCV, mas busca na horizontal

## 3. Combinações Avançadas

### 3.1. PROCV com MÍNIMO
- **Exemplo**: `=PROCV(MÍNIMO(I15:I16); I15:K16; 3; FALSO)`
- **Aplicação**: Encontra o menor valor e retorna informação correspondente

## 4. Exemplos Práticos

### 4.1. Classificação de Alunos
```excel
=SE(B4<6; "RECUPERAÇÃO"; SE(B4<9; "PROVA FINAL"; "APROVADO"))
```
- < 6: Recuperação
- 6-8: Prova Final
- ≥ 9: Aprovado

### 4.2. Busca em Tabela de Dados
```excel
=PROCV("Luz"; A4:E9; 4; FALSO)
```
- Busca "Luz" na coluna A
- Retorna valor da 4ª coluna (Fevereiro)

## 5. Dicas Importantes

1. **Percentagem**: 9% = 0,09 (convertido automaticamente)
2. **Aninhamento**: Funções SE podem ser combinadas para múltiplas condições
3. **Busca Exata**: Sempre que possível, use `FALSO` no PROCV para busca exata
4. **Matriz**: No PROCV, a matriz deve incluir a coluna de busca e a coluna desejada
5. **SES**: Mais eficiente que múltiplos SE aninhados para muitas condições

## 6. Resumo de Sintaxes

| Função | Sintaxe | Uso |
|--------|---------|-----|
| E | `=E(exp1; exp2; ...)` | Todas verdadeiras |
| OU | `=OU(exp1; exp2; ...)` | Pelo menos uma verdadeira |
| NÃO | `=NÃO(exp)` | Inversão lógica |
| SE | `=SE(cond; verd; falso)` | Condicional simples |
| SES | `=SES(crit1; res1; crit2; res2; ...)` | Múltiplas condições |
| PROCV | `=PROCV(valor; matriz; col; aprox)` | Busca vertical |
| PROCH | `=PROCH(valor; matriz; lin; aprox)` | Busca horizontal |

Este resumo cobre as principais funções lógicas e de pesquisa do Excel, essenciais para concursos públicos.
```