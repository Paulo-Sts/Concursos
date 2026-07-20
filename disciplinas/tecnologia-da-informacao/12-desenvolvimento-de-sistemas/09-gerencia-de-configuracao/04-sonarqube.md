# Anotações

# Análise Estática de Código Fonte: SonarQube

## 1.1 Conceito Geral

- **SonarQube** (também chamado apenas de Sonar) é um **agregador de métricas** usado para medir a **qualidade do código-fonte**.
- Realiza **análise estática de código** – não exige a execução do software.
- É uma ferramenta de **inspeção contínua da qualidade do código**.

> [!TIP] DICAS
> - **SAST** = *Static Application Security Testing* = análise **estática**.
> - **DAST** = *Dynamic Application Security Testing* = análise **dinâmica**.
> - O SonarQube é uma ferramenta de **SAST**, não de DAST.

## 1.2 Características Principais

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| **Linguagens suportadas** | Java, C#, PHP, JavaScript, TypeScript, C/C++, Ruby, Kotlin, Go, COBOL, PL/SQL, Python, Swift, CSS, HTML, XML, entre outras (algumas apenas com licença comercial) |
| **Licenciamento** | Gratuito sob GNU LGPL; versões corporativa e data center pagas |
| **Integrações** | Maven, Ant, Gradle, MSBuild; ferramentas CI/CD (Jenkins, Hudson, Bamboo); IDEs (Eclipse, VS, IntelliJ via SonarLint); LDAP, Active Directory, GitHub |
| **Arquitetura** | Servidor + banco de dados (normalmente PostgreSQL) + escaneadores + dashboard web |

## 1.3 Métricas Analisadas pelo SonarQube

### 1.3.1 Complexidade
- **Complexidade ciclomática:** calculada com base no **número de caminhos através do código**.
- Cada função tem complexidade mínima de 1.
- Estruturas como `if` e loops incrementam a complexidade.

### 1.3.2 Duplicações
| MÉTRICA | DESCRIÇÃO |
|---------|-----------|
| `duplicated_blocks` | Número de blocos duplicados de linhas |
| `duplicated_files` | Número de arquivos envolvidos em duplicações |
| `duplicated_lines` | Número de linhas duplicadas |
| `duplicated_lines_density` | Percentual de linhas duplicadas = `duplicated_lines/lines * 100` |

### 1.3.3 Problemas (*Issues*)
| MÉTRICA | DESCRIÇÃO |
|---------|-----------|
| `false_positive_issues` | Problemas marcados como falsos positivos |
| `open_issues` | Problemas em estado **Aberto** |
| `confirmed_issues` | Problemas em estado **Confirmado** |
| `reopened_issues` | Problemas em estado **Reaberto** |

### 1.3.4 Manutenção – Débito Técnico
- **Débito técnico (*Technical Debt*):** esforço (em minutos) para corrigir todos os *code smells*. No dashboard, é exibido em dias (considerando 8h/dia).
- **Dívida técnica no novo código:** esforço para corrigir problemas identificados pela primeira vez no código novo/alterado.

### 1.3.5 Quality Gate
- **Status do Quality Gate:** estado associado ao projeto (`ERROR`, `OK` – `WARN` removido desde a versão 7.6).
- Define um **limite aceitável** (percentual) para métricas como cobertura de testes, débito técnico, bugs, duplicações.
- Muito comum em órgãos públicos: exigência de **cobertura de teste mínima** (ex.: 100%) e **débito técnico máximo** (ex.: 3 dias).

### 1.3.6 Confiabilidade – Bugs
| CLASSIFICAÇÃO | DESCRIÇÃO |
|---------------|-----------|
| **A** | 0 erros |
| **B** | Pelo menos 1 erro menor |
| **C** | Pelo menos 1 erro grave |
| **D** | Pelo menos 1 erro crítico |
| **E** | Pelo menos 1 erro bloqueador |

### 1.3.7 Segurança – Vulnerabilidades
- `vulnerabilities`: número de problemas de vulnerabilidade.
- `new_vulnerabilities`: número de novos problemas de vulnerabilidade.

> [!CAUTION] OBSERVAÇÃO
> - **Issue com severidade CRÍTICA** → deve ser **revisada** (*reviewed*).
> - **Issue com severidade BLOQUEADORA** → deve ser **corrigida imediatamente** (*fixed*).

## 1.4 Tipos de Regras no SonarQube

| TIPO | DOMÍNIO | DESCRIÇÃO |
|------|---------|-----------|
| **Code Smell** | Manutenção | Problema relacionado à manutenibilidade do código |
| **Bug** | Confiabilidade | Problema que afeta a confiabilidade da aplicação |
| **Vulnerabilidade** | Segurança | Falha de segurança |
| **Security Hotspot** | Segurança | Ponto sensível à segurança que requer revisão |

### 1.4.1 Exemplos de Code Smells
- Código duplicado.
- Método longo.
- Classe extensa (*GodObject*).
- *Feature envy* (classe que usa excessivamente métodos de outra).
- Intimidade inapropriada.
- Legado recusado (*override* que quebra contrato da classe genérica).
- Classe preguiçosa (faz muito pouco).
- Complexidade artificial (uso forçado de *design patterns* complexos).
- Identificadores excessivamente longos.

> [!TIP] DICAS
> - **Débito técnico:** ocorre quando o código é desenvolvido sem testes ou com soluções provisórias. Controlar o débito é essencial para evitar seu acúmulo.
> - **Duplicação:** quando uma função é copiada em vez de reutilizada via herança/polimorfismo, qualquer *bug* exige correção em todos os pontos duplicados.

## 1.5 Severidade das Issues

| SEVERIDADE | AÇÃO RECOMENDADA |
|------------|------------------|
| **BLOCKER** | O código **DEVE** ser corrigido imediatamente (*MUST be immediately fixed*) |
| **CRITICAL** | O código **DEVE** ser revisado imediatamente (*MUST be immediately reviewed*) |
| **Major** | Deve ser corrigido |
| **Minor** | Pode ser corrigido |
| **Info** | Apenas informativo |

> [!CAUTION] OBSERVAÇÃO
> - Para *code smells* e bugs, espera-se **zero falsos positivos**.
> - Para vulnerabilidades, espera-se que **mais de 80%** dos problemas sejam **verdadeiros positivos**.
> - Para *security hotspots*, espera-se que **mais de 80%** sejam **revisados** rapidamente.

## 1.6 SonarQube x SAST x DAST

| ASPECTO | SONARQUBE |
|---------|-----------|
| **Tipo de análise** | Estática (SAST) |
| **Execução** | Não requer execução do software |
| **Detecta** | Bugs, code smells, vulnerabilidades, duplicações, complexidade, cobertura de testes |
| **Não detecta** | Problemas funcionais (testes dinâmicos) |

> [!TIP] DICAS
> - Análise estática e dinâmica são **complementares** – passar no SonarQube não garante que a aplicação atenda aos requisitos funcionais.
> - O SonarQube **não utiliza inteligência artificial** – baseia-se em regras algorítmicas.

## 1.7 Tabela Resumo – Métricas do SonarQube

| CATEGORIA | MÉTRICAS |
|-----------|----------|
| **Complexidade** | Complexidade ciclomática (caminhos no código) |
| **Duplicações** | Blocos, arquivos, linhas duplicadas; densidade de duplicação |
| **Problemas (Issues)** | Falsos positivos, abertos, confirmados, reabertos |
| **Manutenção** | Débito técnico (esforço para corrigir code smells) |
| **Confiabilidade** | Bugs (classificação A–E) |
| **Segurança** | Vulnerabilidades; security hotspots |
| **Tamanho** | Classes, linhas de comentário |
| **Testes** | Cobertura de condição (branch coverage) |
| **Quality Gate** | Status ERROR/OK (limite mínimo de qualidade) |

---

# Questões de Fixação

## Questão 01
(CESPE/TCE-PA/AUDITOR DE CONTROLE EXTERNO/ÁREA INFORMÁTICA/ANALISTA DE SISTEMA/2016)

Acerca de análise estática de código-fonte, uma das práticas que verifica a qualidade do código e pode ser realizada antes da execução do software, julgue o próximo item. A ferramenta SonarQube permite analisar a qualidade dos códigos-fontes que envolvem linguagens de computador e de dispositivos móveis e abrange categorias como padrões de codificação, testes e identificação de erros.

**Gabarito:** C (Correto)

## Questão 02
(CESPE/STJ/TÉCNICO JUDICIÁRIO/DESENVOLVIMENTO DE SISTEMAS/2018)

Julgue o item a seguir, acerca de eMAG, sistemas de controle de versão e SonarQube.

Uma issue gerada pelo SonarQube com severidade CRITICA requer a imediata correção do código.

**Gabarito:** E (Errado) - Issue com severidade **CRÍTICA** requer **revisão imediata**; **BLOQUEADORA** requer correção imediata.

## Questão 03
(CESPE/FUNPRESP-EXE/ESPECIALISTA/TECNOLOGIA DA INFORMAÇÃO)

A respeito da ferramenta SonarQube e da interoperabilidade de sistemas, julgue o seguinte item.

No SonarQube, mesmo com as permissões de segurança, nem todas as tags de regras podem ser removidas.

**Gabarito:** C (Correto) - Algumas tags são internas, fornecidas pelos plug-ins, e não podem ser removidas.

## Questão 04
(CESPE/CEBRASPE/MPE-GO ANALISTA EM INFORMÁTICA/2024)

Julgue o item subsequente, relativo a WebServices, SonarQube. O SonarQube detecta as vulnerabilidades de segurança no código por meio de DAST (dynamic application security testing), indicando os erros a serem eliminados antes de implantar o aplicativo.

**Gabarito:** E (Errado) - O SonarQube é uma ferramenta de **SAST** (análise estática), não de DAST.

## Questão 05
(FGV/TRF-1ª REGIÃO/ANALISTA JUDICIÁRIO/APOIO ESPECIALIZADO/ANÁLISE DE SISTEMAS DE INFORMAÇÃO/2024)

O analista Jeferson está configurando um projeto no SonarQube. Ao configurar as métricas de código que devem ser monitoradas, Jefferson adicionou ao projeto a métrica que indica o tempo necessário para corrigir todos os code smells presentes no código. Jefferson adicionou ao projeto no SonarQube a métrica:

a) technical debt.
b) quality gate status.
c) security remediation.
d) maintainability rating.
e) reliability remediation.

**Gabarito:** a

## Questão 06
(CEBRASPE/PC-DF/GESTOR DE APOIO AS ATIVIDADES POLICIAIS CIVIS/ANALISTA DE INFORMÁTICA/DESENVOLVIMENTO DE SISTEMAS/2025)

Julgue o item que se segue, referente a clean code e à ferramenta SonarQube.

O SonarQube tem uma abordagem embasada no princípio de que o código da base em produção deve ser formatado e revisado para garantir que se usem as interfaces de programação e os recursos de linguagem apropriados.

**Gabarito:** E (Errado) - A abordagem do SonarQube é baseada no princípio de que o **novo código** deve estar em conformidade com os padrões de qualidade (*clean as you code*).

## Questão 07
(CESPE/CEBRASPE/DATAPREV/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/DESENVOLVIMENTO DE SOFTWARE/2023)

Julgue o item abaixo, relacionados com JavaScript, Web Services e análise estatística de código fonte.

No SonarQube, a complexidade mede a quantidade de caminhos possíveis na execução do código.

**Gabarito:** C (Correto) - Complexidade ciclomática mede o número de caminhos possíveis no código.

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | C |
| 02 | E |
| 03 | C |
| 04 | E |
| 05 | a |
| 06 | E |
| 07 | C |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Washington Henrique Almeida.*