# SonarQube

## 1. Conceito Geral

### 1.1 Definição e Funcionamento
- SonarQube (também chamado apenas de Sonar) é um agregador de métricas usado para medir a qualidade do código-fonte.
- Realiza análise estática de código – não exige a execução do software.
- É uma ferramenta de inspeção contínua da qualidade do código.

> [!TIP] DICAS:
> - SAST = Static Application Security Testing = análise estática.
> - DAST = Dynamic Application Security Testing = análise dinâmica.
> - O SonarQube é uma ferramenta de SAST, não de DAST.

## 2. Características Principais

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| Linguagens suportadas | Java, C#, PHP, JavaScript, TypeScript, C/C++, Ruby, Kotlin, Go, COBOL, PL/SQL, Python, Swift, CSS, HTML, XML, entre outras (algumas apenas com licença comercial). |
| Licenciamento | Gratuito sob GNU LGPL; versões corporativa e data center pagas. |
| Integrações | Maven, Ant, Gradle, MSBuild; ferramentas CI/CD (Jenkins, Hudson, Bamboo); IDEs (Eclipse, VS, IntelliJ via SonarLint); LDAP, Active Directory, GitHub. |
| Arquitetura | Servidor + banco de dados (normalmente PostgreSQL) + escaneadores + dashboard web. |

## 3. Métricas Analisadas pelo SonarQube

### 3.1 Complexidade
- Complexidade ciclomática: calculada com base no número de caminhos através do código.
- Cada função tem complexidade mínima de 1.
- Estruturas como `if` e loops incrementam a complexidade.

### 3.2 Duplicações

| MÉTRICA | DESCRIÇÃO |
|---------|-----------|
| `duplicated_blocks` | Número de blocos duplicados de linhas. |
| `duplicated_files` | Número de arquivos envolvidos em duplicações. |
| `duplicated_lines` | Número de linhas duplicadas. |
| `duplicated_lines_density` | Percentual de linhas duplicadas = `duplicated_lines/lines * 100`. |

### 3.3 Problemas (Issues)

| MÉTRICA | DESCRIÇÃO |
|---------|-----------|
| `false_positive_issues` | Problemas marcados como falsos positivos. |
| `open_issues` | Problemas em estado Aberto. |
| `confirmed_issues` | Problemas em estado Confirmado. |
| `reopened_issues` | Problemas em estado Reaberto. |

### 3.4 Manutenção – Débito Técnico
- Débito técnico (Technical Debt): esforço (em minutos) para corrigir todos os code smells. No dashboard, é exibido em dias (considerando 8h/dia).
- Dívida técnica no novo código: esforço para corrigir problemas identificados pela primeira vez no código novo/alterado.

> [!TIP] DICAS:
> - Débito técnico ocorre quando o código é desenvolvido sem testes ou com soluções provisórias. Controlar o débito é essencial para evitar seu acúmulo.
> - Duplicação: quando uma função é copiada em vez de reutilizada via herança/polimorfismo, qualquer bug exige correção em todos os pontos duplicados.

### 3.5 Quality Gate
- Status do Quality Gate: estado associado ao projeto (`ERROR`, `OK` – `WARN` removido desde a versão 7.6).
- Define um limite aceitável (percentual) para métricas como cobertura de testes, débito técnico, bugs, duplicações.
- Muito comum em órgãos públicos: exigência de cobertura de teste mínima (ex.: 100%) e débito técnico máximo (ex.: 3 dias).

### 3.6 Confiabilidade – Bugs

| CLASSIFICAÇÃO | DESCRIÇÃO |
|---------------|-----------|
| A | 0 erros. |
| B | Pelo menos 1 erro menor. |
| C | Pelo menos 1 erro grave. |
| D | Pelo menos 1 erro crítico. |
| E | Pelo menos 1 erro bloqueador. |

### 3.7 Segurança – Vulnerabilidades
- `vulnerabilities`: número de problemas de vulnerabilidade.
- `new_vulnerabilities`: número de novos problemas de vulnerabilidade.

## 4. Tipos de Regras no SonarQube

### 4.1 Classificação por Domínio

| TIPO | DOMÍNIO | DESCRIÇÃO |
|------|---------|-----------|
| Code Smell | Manutenção | Problema relacionado à manutenibilidade do código. |
| Bug | Confiabilidade | Problema que afeta a confiabilidade da aplicação. |
| Vulnerabilidade | Segurança | Falha de segurança. |
| Security Hotspot | Segurança | Ponto sensível à segurança que requer revisão. |

### 4.2 Exemplos de Code Smells
- Código duplicado;
- Método longo;
- Classe extensa (GodObject);
- Feature envy (classe que usa excessivamente métodos de outra);
- Intimidade inapropriada;
- Legado recusado (override que quebra contrato da classe genérica);
- Classe preguiçosa (faz muito pouco);
- Complexidade artificial (uso forçado de design patterns complexos);
- Identificadores excessivamente longos.

## 5. Severidade das Issues

| SEVERIDADE | AÇÃO RECOMENDADA |
|------------|------------------|
| BLOCKER | O código DEVE ser corrigido imediatamente (MUST be immediately fixed). |
| CRITICAL | O código DEVE ser revisado imediatamente (MUST be immediately reviewed). |
| Major | Deve ser corrigido. |
| Minor | Pode ser corrigido. |
| Info | Apenas informativo. |

> [!CAUTION] OBSERVAÇÃO:
> - Issue com severidade CRÍTICA → deve ser revisada (reviewed).
> - Issue com severidade BLOQUEADORA → deve ser corrigida imediatamente (fixed).
> - Para code smells e bugs, espera-se zero falsos positivos.
> - Para vulnerabilidades, espera-se que mais de 80% dos problemas sejam verdadeiros positivos.
> - Para security hotspots, espera-se que mais de 80% sejam revisados rapidamente.

## 6. SonarQube x SAST x DAST

| ASPECTO | SONARQUBE |
|---------|-----------|
| Tipo de análise | Estática (SAST). |
| Execução | Não requer execução do software. |
| Detecta | Bugs, code smells, vulnerabilidades, duplicações, complexidade, cobertura de testes. |
| Não detecta | Problemas funcionais (testes dinâmicos). |

> [!TIP] DICAS:
> - Análise estática e dinâmica são complementares – passar no SonarQube não garante que a aplicação atenda aos requisitos funcionais.
> - O SonarQube não utiliza inteligência artificial – baseia-se em regras algorítmicas.

## 7. Tabela Resumo – Métricas do SonarQube

| CATEGORIA | MÉTRICAS |
|-----------|----------|
| Complexidade | Complexidade ciclomática (caminhos no código). |
| Duplicações | Blocos, arquivos, linhas duplicadas; densidade de duplicação. |
| Problemas (Issues) | Falsos positivos, abertos, confirmados, reabertos. |
| Manutenção | Débito técnico (esforço para corrigir code smells). |
| Confiabilidade | Bugs (classificação A–E). |
| Segurança | Vulnerabilidades; security hotspots. |
| Tamanho | Classes, linhas de comentário. |
| Testes | Cobertura de condição (branch coverage). |
| Quality Gate | Status ERROR/OK (limite mínimo de qualidade). |