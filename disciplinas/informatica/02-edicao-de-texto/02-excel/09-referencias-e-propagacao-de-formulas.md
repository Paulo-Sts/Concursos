# Resumo: Excel 365 – Referências e Propagação de Fórmulas

## 1. Referência a Células
1.1. Mesmo arquivo e mesma planilha:
    - `A1`

1.2. Mesmo arquivo e outra planilha:
    - `NOME_DA_PLANILHA!A1`

1.3. Outro arquivo e outra planilha:
    - `[NOME_DO_ARQUIVO.XLSX]NOME_DA_PLANILHA!A1`

## 2. Tipos de Referência
2.1. Referência Relativa:
    - Aponta para a posição relativa da célula.
    - A referência se ajusta ao copiar a fórmula.
    - Exemplo: `=B2+B5`

2.2. Referência Absoluta:
    - Aponta para uma posição fixa da célula.
    - A referência não se altera ao copiar a fórmula.
    - Representação: `=$B$2+$B$5`
    - Tecla de atalho: `F4` (cicla entre os tipos de referência)

2.3. Referência Mista:
    - Combinação de parte absoluta e parte relativa.
    - Coluna fixa e linha livre: `=$B2+$B5`
    - Coluna livre e linha fixa: `=B$2+B$5`

## 3. Referência Circular
3.1. Ocorre quando uma fórmula referencia a própria célula em que está inserida, direta ou indiretamente.
3.2. Exemplo: Inserir `=SOMA(A1:A3)` na célula `A3`.
3.3. O Excel exibe um aviso de erro, pois a fórmula não pode ser calculada corretamente.

## 4. Propagação de Fórmulas
4.1. Ocorre quando uma fórmula é copiada (Ctrl+C) e colada (Ctrl+V) em outra célula.
4.2. Não ocorre quando a célula é recortada (Ctrl+X) e colada.

4.3. Tipos de Propagação:
    - Entre Linhas: A fórmula é copiada para outra linha.
        - As referências de linha relativas se ajustam.
        - Referências absolutas (`$`) permanecem fixas.
    - Entre Colunas: A fórmula é copiada para outra coluna.
        - As referências de coluna relativas se ajustam.
        - Referências absolutas (`$`) permanecem fixas.
    - Diagonal: A fórmula é copiada para outra linha e outra coluna.
        - Referências de linha e coluna relativas se ajustam.
        - Referências absolutas (`$`) permanecem fixas.

4.4. Regra Geral: Durante a propagação, as referências com `$` não se alteram. As demais se ajustam com base no deslocamento (número de linhas e colunas) entre a célula de origem e a de destino.