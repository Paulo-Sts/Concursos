# Resumo: Excel 365 - Operadores

## 1. Inicialização de Fórmulas
- Fórmulas devem começar com: `=`, `+`, `-`, ou `@`
- `@` usado apenas antes de funções, não em fórmulas com operadores
- Sem esses caracteres, o Excel interpreta como texto

## 2. Operadores Aritméticos
- `+` Adição
- `-` Subtração
- `*` Multiplicação
- `/` Divisão
- `^` Potência (ex: `2^3 = 8`)
- `%` Porcentagem (divide por 100)

## 3. Precedência dos Operadores Aritméticos
1. `^` Potência
2. `*` ou `/` (o que aparecer primeiro)
3. `+` ou `-` (o que aparecer primeiro)

## 4. Uso de Parênteses
- Parênteses forçam a precedência e são resolvidos primeiro
- Alteram completamente o resultado da fórmula
- Exemplo: `=2+(18/3)^2*5 = 182`

## 5. Operador de Concatenação
- `&` (E comercial) - une textos lado a lado
- Exemplo: `=A1&"@"&A2` resulta em "fulano@stj.jus.br"
- Textos fixos devem estar entre aspas

## 6. Operadores Lógicos
- `>` Maior que (ex: `=5>7` → FALSO)
- `<` Menor que (ex: `=5<7` → VERDADEIRO)
- `>=` Maior ou igual (ex: `=5>=7` → FALSO)
- `<=` Menor ou igual (ex: `=5<=7` → VERDADEIRO)
- `=` Igual (ex: `=5=7` → FALSO)
- `<>` Diferente (ex: `=5<>7` → VERDADEIRO)

## 7. Observações Importantes
- Operadores aritméticos: cálculos manuais
- Funções: cálculos automáticos com procedimentos internos
- Expressões lógicas retornam VERDADEIRO ou FALSO
- Não existe operador `≠` no Excel - usar `<>`
- Porcentagem tem mesma precedência que divisão/multiplicação