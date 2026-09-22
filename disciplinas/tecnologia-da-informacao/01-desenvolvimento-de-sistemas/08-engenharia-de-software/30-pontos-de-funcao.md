# Engenharia de Software - Pontos de Função

## 1. Análise de Pontos de Função (APF)
- Métrica criada por Allan Albrecht, da IBM, em 1979.
- Surgiu como alternativa às métricas baseadas em Linhas de Código (LOC).
- A métrica PF mede o que o software faz, independentemente de como foi construído.
- Independe da linguagem de programação.
- Fundamentada em avaliação padronizada dos requisitos lógicos do usuário.

### 1.1 IFPUG
- Fundado em 1986.
- International Function Point Users Group.
- Entidade sem fins lucrativos composta por pessoas e empresas de diversos países.
- Finalidade: manter, atualizar e promover a métrica.

### 1.2 IN-04
- Norma do governo federal brasileiro que recomenda o uso de pontos de função em contratações de serviços.
- Permite mensuração dos resultados.
- Foi reformulada e passou a se chamar IN-01.

### 1.3 Pontos de Função (PF)
- Técnica de medição do tamanho funcional de um software.
- Funções são operações extraídas dos requisitos funcionais a partir da visão do usuário.
- Unidade de medida da técnica.
- Permite estimar o esforço para implementação do sistema.

> [!CAUTION] OBSERVAÇÃO:
> - Em concursos da esfera civil, normalmente não aparece o tema fator de ajuste.
> - O fator de ajuste costuma aparecer em concursos do meio militar.
> - A fronteira da aplicação deve ser bem definida, pois influencia diretamente a contagem das funções de dados ALI e AIE.
> - No governo federal, o Ministério do Planejamento fixa o valor do fator de ajuste em 1,00, não utilizando a avaliação das características gerais do sistema.

## 2. Tipos de Função
- A medição consiste em decompor o projeto em uma análise Top-Down em componentes funcionais.

| TIPO DE FUNÇÃO | CLASSIFICAÇÃO | COMPONENTE FUNCIONAL BÁSICO |
|---|---|---|
| Função de transação | Entrada externa (EE) | Interação |
| Função de transação | Saída externa (SE) | Interação |
| Função de transação | Consulta externa (CE) | Interação |
| Função de dados | Arquivo lógico interno (ALI) | Armazenamento |
| Função de dados | Arquivo de interface externa (AIE) | Armazenamento |

### 2.1 Funções de Dados
- Arquivos Lógicos Internos (ALI): grupos de dados logicamente relacionados (do ponto de vista do usuário) e mantidos pela própria aplicação.
- Arquivos de Interface Externa (AIE): grupos de dados logicamente relacionados (do ponto de vista do usuário) e apenas referenciados de outras aplicações.

### 2.2 Funções de Transação
- Entradas Externas (EE): transações com o objetivo de atualizar arquivos lógicos internos ou modificar o comportamento do sistema.
- Consultas Externas (CE): transações que representam simples recuperação de dados de arquivos lógicos internos e/ou arquivos de interface externa.
- Saídas Externas (SE): transações com o objetivo de apresentação de informação, porém envolvendo lógica de processamento adicional a uma consulta externa.

## 3. Processo de Contagem
- O processo de contagem é padronizado e segue as diretrizes do IFPUG.

### 3.1 Tipo de Contagem
- Projeto de desenvolvimento: mede todas as funções que o projeto entregará e eventuais funções de conversão de dados.
- Projeto de melhoria: mede as funções alteradas, incluídas e excluídas pelo projeto e eventuais funções de conversão de dados.
- Aplicação: mede as funções de um software instalado.

> [!CAUTION] OBSERVAÇÃO:
> - No governo brasileiro, foram editadas portarias e normas que criaram um manual próprio de contagem, extirpando algumas regras do manual IFPUG.
> - Exemplo: no projeto de melhoria, o manual IFPUG geraria uma contagem muito alta, pois contaria novamente uma série de itens.

## 4. Tabela de Contribuição Funcional
- A tabela é padronizada pelo IFPUG.
- Todos os usuários da técnica utilizam os mesmos valores.
- EE e CE possuem os mesmos valores.
- SE possui valores maiores que EE e CE por ser mais complexa.

| TIPO DE FUNÇÃO | SIMPLES | MÉDIA | COMPLEXA |
|---|---|---|---|
| ALI | 7 | 10 | 15 |
| AIE | 5 | 7 | 10 |
| EE | 3 | 4 | 6 |
| SE | 4 | 5 | 7 |
| CE | 3 | 4 | 6 |

> [!TIP] DICAS:
> - Para memorizar: EE e CE têm os mesmos valores (3, 4, 6).
> - SE tem valor um pouco maior que EE/CE (4, 5, 7).
> - ALI (7, 10, 15) e AIE (5, 7, 10).

## 5. Tabela de Complexidade
- Utilizada para determinar a complexidade (baixa, média ou alta) de cada função.
- Padronizada pelo IFPUG.
- Critério: número de arquivos referenciados e número de tipos de dados.

### 5.1 Complexidade para ALI e AIE
- Baixa: menos de 2 arquivos referenciados e menos de 5 tipos de dados.

### 5.2 Complexidade para SE e CE
- Segue tabela específica do IFPUG para determinação da complexidade.

## 6. Fator de Ajuste (VAF)
- Considera que outros fatores afetam o tamanho funcional do sistema.
- Fatores relacionados a características da aplicação.
- No cálculo dos PF brutos não é levada em conta a tecnologia usada nem os requisitos não funcionais.
- Baseado em 14 características gerais de sistema.

### 6.1 Características Gerais do Sistema
- Comunicação de dados.
- Processamento distribuído.
- Performance.
- Utilização de equipamento.
- Volume de transações.
- Entrada de dados online.
- Eficiência do usuário final.
- Atualização online.
- Processamento complexo.
- Reutilização de código.
- Facilidade de implantação.
- Facilidade operacional.
- Múltiplos locais.
- Facilidade de mudanças.

### 6.2 Fórmula do Fator de Ajuste
- PFA = PFNA × FA
- Pontos de função ajustados = pontos de função não ajustados multiplicados pelo fator de ajuste calculado.

> [!CAUTION] OBSERVAÇÃO:
> - O Ministério do Planejamento não utiliza a avaliação do VAF em suas medições.
> - O VAF é fixado em 1,00 para contagens do governo federal.
> - Isso significa que as características gerais do sistema não afetam o tamanho dos PF obtidos nessas contagens.

## 7. Tabela de Contribuição para Dados
- Após identificar a complexidade de cada ALI e AIE, determina-se sua contribuição para a contagem dos PF.

| TIPO DE FUNÇÃO | BAIXA | MÉDIA | ALTA |
|---|---|---|---|
| ALI | 7 PF | 10 PF | 15 PF |
| AIE | 5 PF | 7 PF | 10 PF |