# Anotações – Python para Análise de Dados/IA – Pandas

## 1. Contextualização e Importância do Pandas

### 1.1 Cenário atual em concursos e negócios

- As bibliotecas Python para análise de dados e IA (principalmente **Pandas**, **NumPy** e **Matplotlib**) são amplamente cobradas em concursos públicos, não apenas na área de TI, mas também em carreiras fiscais e de controle.
- Atualmente, os próprios departamentos de negócio têm assumido a responsabilidade de gerar códigos e ler bases de dados (CSV, JSON, XML), deixando para o setor de TI as diretrizes de segurança e governança.
- Python é a linguagem preferencial devido à curva de aprendizado mais leve e ao vasto ecossistema de bibliotecas especializadas.

> ### 1.1.1 Diferencial do Pandas
> - O Pandas é amplamente utilizado para **ETL (Extração, Transformação e Carregamento)** de dados, permitindo pré-processamento, limpeza, transformação e análise de dados tabulares.

## 2. Conceituação

### 2.1 Definição

- **Pandas** = biblioteca de **código aberto** do Python, construída **sobre o NumPy**.
- Voltada para **análise e manipulação de dados** estruturados (tabelas), sendo padrão em Ciência de Dados, Machine Learning e Big Data.

### 2.2 Principais fontes de dados que o Pandas consegue ler

- Planilhas Excel.
- Arquivos CSV (delimitados por vírgula, ponto e vírgula ou tabulação).
- Tabelas extraídas de bancos de dados (via SQL).
- Relatórios de sistemas e arquivos de log.
- Conjuntos de dados públicos (Ministério da Saúde, ENEM, Portal da Transparência, IBGE, Tesouro Nacional).

## 3. Principais Funcionalidades

| FUNCIONALIDADE | DESCRIÇÃO |
| --- | --- |
| **Leitura e escrita de dados** | Suporte a CSV, Excel, JSON, SQL, Parquet |
| **Limpeza e transformação** | Remoção de valores nulos, substituições, renomeação de colunas |
| **Seleção e filtragem** | Facilidade para extrair subconjuntos de dados |
| **Operações estatísticas e matemáticas** | Aplicadas a colunas e linhas |
| **Agrupamento, junções (merge/join) e tabelas dinâmicas (pivot tables)** | Funcionalidades semelhantes a bancos de dados ou Excel |
| **Integração** | Compatível com NumPy, Matplotlib e Scikit-Learn |

> ### 3.1 Destaque
> - Embora o Pandas use o **Matplotlib como *backend* para geração de gráficos** (método `.plot()`), ele **não possui um mecanismo totalmente nativo e independente** de visualização – as bancas costumam considerar isso como uma ressalva.

## 4. Principais Estruturas de Dados

| ESTRUTURA | DESCRIÇÃO | ANALOGIA |
| --- | --- | --- |
| **Series** | Array unidimensional rotulado (indexado) | Uma **coluna** de planilha ou uma lista com rótulos |
| **DataFrame** | Estrutura bidimensional (linhas e colunas) | Uma **tabela completa** (planilha Excel, arquivo CSV) |

> ### 4.1 Relação
> - Cada coluna de um **DataFrame** é uma **Series**.
> - O DataFrame é o **conjunto de todas as Series** (colunas) alinhadas por linhas.

## 5. Exemplo Prático – Criando um DataFrame a partir de um Dicionário

### 5.1 Código

```python
import pandas as pd

notas_alunos = {
    "Nome": ["Ana", "Bruno", "Carlos"],
    "Idade": [22, 25, 21],
    "Curso": ["Python", "Java", "Python"],
    "Nota": [8.5, 7.0, 9.2]
}

df = pd.DataFrame(notas_alunos)
print(df)
```

### 5.2 Resultado da execução

```
    Nome  Idade   Curso  Nota
0    Ana     22  Python   8.5
1  Bruno     25    Java   7.0
2  Carlos   21  Python   9.2
```

> ### 5.2.1 Observações
> - As **chaves** do dicionário tornam-se os **nomes das colunas** (Series).
> - As **listas** (valores) tornam-se os **dados das linhas**.
> - Se não forem definidos índices específicos, o Pandas cria automaticamente índices numéricos sequenciais a partir de **0**.

## 6. Importação Convencional – Alias

### 6.1 Sintaxe padrão

```python
import pandas as pd
```

- **Alias convencional** amplamente adotado no mercado: `pd`.
- Diferente de outras bibliotecas: NumPy usa `np`, Pandas usa `pd`.

> ### 6.1.1 Atenção (questão IV/UFG/2026)
> - Embora o Python aceite qualquer alias (ex.: `import pandas as PND`), a **convenção** e o padrão da comunidade é `import pandas as pd`.

## 7. Pandas vs. NumPy

| BIBLIOTECA | FOCO PRINCIPAL | ESTRUTURAS | TIPO DE DADOS |
| --- | --- | --- | --- |
| **NumPy** | Computação numérica, operações vetorizadas | Arrays multidimensionais (ndarray) | Homogêneos (todos os elementos do mesmo tipo) |
| **Pandas** | Manipulação e análise de dados estruturados (tabulares) | Series e DataFrame | Podem ser heterogêneos (diferentes tipos por coluna) |

> ### 7.1 Relação
> - O Pandas é **construído sobre o NumPy** (utiliza arrays NumPy internamente).
> - Para manipulação de arrays multidimensionais homogêneos, a biblioteca correta é **NumPy**, não Pandas.

## 8. Questões de Concurso Comentadas

### 8.1 (IV/UFG/2026/UFSCAR – ESTATÍSTICO)

**Item:** Qual o código para importar a biblioteca pandas utilizando o “alias” convencional?

**Alternativa correta:** **c) import pandas as pd**.

**Comentário:** Embora outras sintaxes funcionem tecnicamente, o padrão de mercado e o mais cobrado em provas é `import pandas as pd`.

### 8.2 (QUADRIX/2024/IBICT – TECNOLOGISTA)

**Item:** "Pandas é uma biblioteca de código aberto destinada a realizar operações em arrays multidimensionais na linguagem de programação Java."

**Gabarito:** **Errado (E)**.

**Comentário:** 
- A biblioteca para arrays multidimensionais é **NumPy**, não Pandas.
- Pandas é da linguagem **Python**, não Java.

### 8.3 (FGV/2024/TCE/GO – ANALISTA DE CONTROLE EXTERNO)

**Item:** O objetivo principal da biblioteca Pandas no contexto da ciência de dados é:

**Alternativa correta:** **a) Facilitar a manipulação e análise de dados estruturados pela disponibilização de opções de estruturas de dados.**

**Comentário:** As demais alternativas referem-se a: (b) processamento de linguagem natural; (c) redes neurais (TensorFlow/PyTorch); (d) manipulação de datas (não é o foco principal); (e) cálculos numéricos com arrays (função do NumPy).

### 8.4 (FGV/2024/PREFEITURA DE CUIABÁ – AUDITOR FISCAL)

**Três afirmativas sobre NumPy, Pandas e SciPy:**

| AFIRMATIVA | ANÁLISE | V/F |
| --- | --- | --- |
| A biblioteca NumPy é baseada na manipulação de estruturas de dados multidimensionais, nas quais todos os elementos possuem o mesmo tipo. | Correta – arrays NumPy são homogêneos. | **V** |
| A biblioteca pandas possui métodos próprios para geração e visualização de gráficos. | Nuance: o Pandas tem o método `.plot()`, mas ele usa Matplotlib como *backend*. A banca considerou que o Pandas **não possui mecanismo totalmente nativo e independente** → **Falso**. | **F** |
| A biblioteca SciPy possui um pacote para manipulação de matrizes esparsas. | Correta – SciPy tem `scipy.sparse`. | **V** |

**Sequência:** V, F, V → **alternativa b**.

**Gabarito:** **b) V, F e V**.

### 8.5 (FUNDATEC/2023/PROCERGS – ANALISTA EM COMPUTAÇÃO/CIÊNCIA DE DADOS)

**Item:** Qual biblioteca Python construída sobre o NumPy permite realizar análise quantitativa de dados?

**Alternativa correta:** **d) Pandas**.

**Comentário:** Scikit-Learn, PyTorch e TensorFlow são para machine learning/deep learning; Orage3 não é biblioteca relevante. O Pandas foi construído sobre o NumPy e é especializado em análise quantitativa de dados tabulares.

## GABARITO DAS QUESTÕES

| QUESTÃO | GABARITO |
| --- | --- |
| 01 (IV/UFG/2026) | c |
| 02 (QUADRIX/2024) | E |
| 03 (FGV/2024/TCE/GO) | a |
| 04 (FGV/2024/Cuiabá) | b |
| 05 (FUNDATEC/2023) | d |

---

*Material complementar à aula "Python para Análise de Dados/IA – Pandas" (professor Rogério Araújo, Gran Concursos).*