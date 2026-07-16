# Anotações

# Testes de Segurança de Aplicações – SAST

## 1.1 Contexto e Evolução

- Historicamente, o desenvolvimento de software ocorria separadamente da operação, gerando conflitos em produção.
- A metodologia **DevOps** integrou as equipes de desenvolvimento e operação, reduzindo esses conflitos.
- Posteriormente, percebeu-se a necessidade de incluir a segurança da informação desde o início do desenvolvimento, surgindo a prática de **DevSecOps**.
- Com o **DevSecOps**, a segurança é considerada em todas as fases do desenvolvimento.

> [!TIP] DICAS
> - **Quanto mais avançado estiver o processo de desenvolvimento, mais caro e complexo será corrigir falhas de segurança.**
> - A detecção precoce de problemas reduz custos e minimiza riscos.
> - Encontrar e corrigir vulnerabilidades ainda no desenvolvimento é mais barato e seguro do que identificá-las após a implementação.

## 1.2 Conceito de SAST

- ***SAST - Static Application Security Testing***: teste de segurança de aplicações que examina o código **sem executá-lo**.
- Permite a identificação de vulnerabilidades de segurança **antes da implementação** do software.
- Analisa o código-fonte, *bytecode* ou código compilado de um software sem executá-lo.
- É um teste de **caixa branca** (*white box*), pois analisa a estrutura interna do código.

### 1.2.1 Comparativo com Outros Testes

| TESTE | SIGLA | MOMENTO | ABORDAGEM | EXECUÇÃO |
|-------|-------|---------|-----------|----------|
| Análise Estática | SAST | Antes da execução | Caixa branca | Código não é executado |
| Análise Dinâmica | DAST | Em tempo de execução | Caixa preta | Software em execução |
| Análise Interativa | IAST | Em tempo de execução | Caixa cinza | Software em execução |

> ### 1.2.2 Características Essenciais do SAST
> **Atenção/Exceção:** O SAST é um teste **interno** que não se limita a verificar a execução da funcionalidade, mas investiga diretamente o código em busca de vulnerabilidades. Essa abordagem permite a análise detalhada de bibliotecas, dependências e pacotes externos.

## 1.3 Funcionamento do SAST

### 1.3.1 Etapas do Processo
- **Análise Estática:** o código é escaneado em busca de vulnerabilidades conhecidas, sem precisar executar o software.
- **Detecção de Vulnerabilidades:** identifica falhas como injeção de SQL, XSS (*Cross-Site Scripting*), vazamento de dados sensíveis, uso inseguro de bibliotecas e erros de configuração.
- **Relatório de Segurança:** gera *insights* para os desenvolvedores corrigirem as falhas antes da implantação.
- **Integração com CI/CD:** incorporada em *pipelines* DevSecOps para garantir verificações automáticas a cada atualização de código.

## 1.4 Principais Características do SAST

### 1.4.1 Características Técnicas
- **Teste sem execução:** não depende da execução do software, diferentemente do DAST.
- **Detecta vulnerabilidades no código-fonte:** permite correção precoce, reduzindo custos de segurança.
- **Integração com DevSecOps:** pode ser usado junto com ferramentas de CI/CD para análises automáticas.
- **Cobertura de Código:** avalia toda a base de código, incluindo caminhos de execução raramente testados manualmente.
- **Análise de Bibliotecas e Dependências:** identifica vulnerabilidades em pacotes externos.

### 1.4.2 Exemplos de Vulnerabilidades Detectadas
- Injeção de SQL (*SQL Injection*).
- *Cross-Site Scripting* (XSS).
- Uso de funções inseguras.
- Vazamento de credenciais.
- Erros de controle de acesso.

## 1.5 Principais Ferramentas SAST

| FERRAMENTA | DESCRIÇÃO |
|------------|-----------|
| **SonarQube** | Análise de código estático para detectar vulnerabilidades e falhas de qualidade |
| **Checkmarx** | Avaliação profunda de segurança de código |
| **Fortify Static Code Analyzer** | Ferramenta da Micro Focus para análise de segurança em grandes projetos |
| **Veracode** | Solução SaaS que fornece testes de segurança contínuos |
| **CodeQL** | Análise de código da GitHub para encontrar vulnerabilidades |

## 1.6 Integração do SAST com DevSecOps

### 1.6.1 Formas de Integração
- **CI/CD Pipelines:** ferramentas como Jenkins, GitHub Actions e GitLab CI/CD podem executar verificações SAST automaticamente.
- **Pré-commit Hooks:** integrado no ambiente do desenvolvedor para verificar código antes do *commit*.
- **Segurança Shift-Left:** aplicação do SAST nas primeiras fases do desenvolvimento evita problemas críticos na produção.

> [!CAUTION] OBSERVAÇÃO
> **Shift-Left:** estratégia de segurança que busca **antecipar a identificação de falhas** antes que o sistema avance para a produção. O SAST é uma ferramenta fundamental para essa abordagem.

## 1.7 Vantagens e Desvantagens do SAST

### 1.7.1 Vantagens
- Detecta vulnerabilidades cedo, reduzindo custos de correção.
- Cobertura completa do código, incluindo caminhos raramente testados.
- Integração com *pipelines* de CI/CD para segurança contínua.

### 1.7.2 Desvantagens
- Pode gerar **falsos positivos**, exigindo ajustes finos.
- Dificuldade para linguagens dinâmicas (JavaScript, Python), onde o comportamento depende do ambiente de execução.
- Não detecta erros de configuração ou vulnerabilidades resultantes da interação da aplicação com outros sistemas.

> [!TIP] DICAS
> - O SAST tende a gerar um alto número de **falsos positivos**, pois pode identificar trechos do código como vulneráveis sem que representem, de fato, um risco real.
> - Por ser um teste de **caixa branca**, examina o código estático, mas pode apresentar dificuldades na análise de linguagens dinâmicas.
> - O SAST **deve ser realizado no início do processo, durante o desenvolvimento**, e não quando o sistema já está em produção.

## 1.8 Comparativo SAST x DAST

| CARACTERÍSTICA | SAST | DAST |
|----------------|------|------|
| Momento do teste | Antes da execução | Durante a execução |
| Execução do software | Não é executado | Software em execução |
| Abordagem | Caixa branca | Caixa preta |
| Análise | Código-fonte, *bytecode* ou compilado | Interfaces expostas |
| Momento ideal | Desenvolvimento (Shift-Left) | Pós-implantação/Produção |
| Principais vulnerabilidades | SQL Injection, XSS, vazamento de credenciais | Problemas de configuração, autenticação, autorização |

---

# Questões de Fixação

## Questão 01
(FGV/2024/EPE/ANALISTA DE GESTÃO CORPORATIVA/TECNOLOGIA DA INFORMAÇÃO/SOLUÇÕES)

Desenvolvimento seguro é um conjunto de práticas que visam incorporar a segurança em todas as fases do ciclo de vida do desenvolvimento de software. As técnicas de análise de segurança de aplicações desempenham um papel crucial na identificação e mitigação de vulnerabilidades.

Assinale a opção que indica a técnica usada para analisar o código-fonte de uma aplicação em busca de vulnerabilidades, sem executar essa aplicação.

a) DAST (*Dynamic Application Security Testing*).
b) SAST (*Static Application Security Testing*).
c) IAST (*Interactive Application Security Testing*).
d) *Black Box Testing*.
e) *Fuzz Testing*.

**Gabarito:** b

## Questão 02
(CESPE-CEBRASPE/2024/MPO/ANALISTA DE PLANEJAMENTO E ORÇAMENTO/ESPECIALIDADE: GESTÃO DA SEGURANÇA DA INFORMAÇÃO ORÇAMENTÁRIA)

Em referência às principais características de testes de segurança em *pipelines* de automação de códigos e infraestrutura, julgue o item seguinte.

Testes estáticos (SAST) têm a função de tentar encontrar falhas de segurança no código de uma aplicação após o sistema entrar em produção.

**Gabarito:** E (Errado) - O SAST deve ser realizado no início do processo, durante o desenvolvimento, e não quando o sistema já está em produção.

## Questão 03
(FGV/2023/SEFAZ-MG/AUDITOR FISCAL DA RECEITA ESTADUAL/TECNOLOGIA DA INFORMAÇÃO/TARDE)

Visando a melhorar a segurança de suas aplicações, os responsáveis pela empresa XPTO decidiram contratar uma empresa para fazer a análise do código fonte.

A consultoria utilizou uma ferramenta que fez a análise automática do código fonte e indicou o seguinte código como vulnerável:

```php
<?php
$db = new SQLite3('test.db');
$count = $db->querySingle('select count(*) from secrets where id = '. $_GET['id']);
echo "O resultado é: ".$count;
```

Baseado no resultado, assinale a opção que mostra corretamente: o nome da categoria a que pertence a ferramenta e a categoria da vulnerabilidade.

a) *Dynamic Application Security Testing* (DAST) e *Cross-site Scripting*.
b) *Static Application Security Testing* (SAST) e SQL Injection.
c) *Interactive Application Security Testing* (IAST) e *Buffer Overflow*.
d) *Dynamic Application Security Testing* (DAST) e SQL Injection.
e) *Interactive Application Security Testing* (IAST) e *Cross-site Scripting*.

**Gabarito:** b

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | b |
| 02 | E |
| 03 | b |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*