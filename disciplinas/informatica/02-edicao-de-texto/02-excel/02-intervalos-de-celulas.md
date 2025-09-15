# Resumo: Excel 365 - Intervalos de Células

## 1. Células
- Interseção entre linhas (horizontais) e colunas (verticais)
- Sistema de coordenadas: colunas (A-Z, AA-AZ, BA-BZ, ..., XFD) + linhas (1-1048576)
- Caixa de nome: exibe e permite renomear célula selecionada

## 2. Estrutura Hierárquica
- **Célula**: unidade básica (ex: A1, B5)
- **Planilha**: tabela com múltiplas células
- **Pasta de Trabalho**: arquivo contendo uma ou mais planilhas
- Configurável: número inicial de planilhas por pasta de trabalho

## 3. Tipos de Intervalos

### 3.1. Intervalos Contínuos
- **Mesma coluna**: A1:A3 (células A1, A2, A3)
- **Mesma linha**: A1:C1 (células A1, B1, C1)
- **Múltiplas colunas/linhas**: A1:B2 (A1, A2, B1, B2)
- **Coluna inteira**: A:A (todas as células da coluna A)
- **Linha inteira**: 1:1 (todas as células da linha 1)
- **Símbolo ":"**: significa "até"

### 3.2. Intervalos Aleatórios (Não Contíguos)
- Células não adjacentes: A1;C2;D3
- **Símbolo ";"**: significa "e"
- Seleção: manter Ctrl pressionado enquanto clica nas células

### 3.3. Intervalos Mistos
- Combinação de intervalos contínuos e aleatórios
- Exemplo: A1;B2:C3 (A1 + B2, B3, C2, C3)

## 4. Técnicas de Seleção
- **Contínuo**: clique na primeira célula + Shift + clique na última célula
- **Aleatório**: Ctrl + clique em cada célula desejada
- **Invertido**: Excel automaticamente corrige ordem (A4:B1 → A1:B4)

## 5. Mensagens de Erro Comuns
- `#VALOR!`: argumento de fórmula incorreto
- `#REF!`: referência a célula excluída ou inexistente
- `#NUM!`: erro aritmético (ex: raiz de número negativo)
- `#NOME?`: nome de função inválido
- `#N/D`: valor não determinado (comum em PROCV/PROCH)
- `#DIV/0!`: divisão por zero
- `#####`: conteúdo maior que largura da célula (não é erro)