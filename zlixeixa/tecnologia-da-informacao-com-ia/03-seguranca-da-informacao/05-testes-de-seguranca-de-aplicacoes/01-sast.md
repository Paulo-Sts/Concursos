# Sast

## 1. Introdução ao DevSecOps e Testes de Segurança
- Evolução histórica da metodologia DevOps para o DevSecOps com o objetivo de integrar a segurança em todas as fases do desenvolvimento.
- Implementação da estratégia de segurança conhecida como Shift-Left que busca antecipar a identificação de falhas antes da produção.
- Divisão fundamental entre análise estática que examina o código sem executá-lo e análise dinâmica que avalia o software em execução.

## 2. Conceito e Funcionamento do Sast
- SAST (Static Application Security Testing) é uma técnica de teste de caixa branca que analisa o código-fonte, bytecode ou código compilado.
- Realização de escaneamento automatizado em busca de vulnerabilidades conhecidas sem a necessidade de rodar a aplicação.
- Identificação de falhas críticas como SQL Injection, XSS (Cross-Site Scripting), vazamento de credenciais e uso de funções inseguras.
- Geração de relatórios detalhados com insights para que os desenvolvedores corrijam as falhas antes da implantação.

## 3. Impacto de Custos no Desenvolvimento
- A detecção precoce de problemas reduz significativamente os custos e minimiza os riscos operacionais.
- O custo de correção aumenta de forma exponencial conforme o estágio em que o bug é identificado ⟶ o valor em produção é o mais elevado.

### 3.1 Custos por Estágio de Identificação de Bug
| ESTÁGIO DE IDENTIFICAÇÃO | CUSTO POR BUG |
|---|---|
| Architecture design | 10 |
| Development and unit testing | 100 |
| System testing | 1000 |
| Acceptance testing | 10000 |
| Production and post release | 100000 |

## 4. Características e Integração
- Cobertura completa de código permitindo avaliar caminhos de execução que raramente são testados de forma manual.
- Integração direta com pipelines de CI/CD (Jenkins, GitHub Actions) e pré-commit hooks para garantir verificações automáticas.
- Análise detalhada de bibliotecas, dependências e pacotes externos para verificar possíveis riscos na cadeia de suprimentos.

### 4.1 Principais Ferramentas Sast
| FERRAMENTA | CARACTERÍSTICA |
|---|---|
| Sonarqube | Análise de código estático para detectar vulnerabilidades e falhas de qualidade |
| Checkmarx | Avaliação profunda de segurança de código |
| Fortify | Análise de segurança para grandes projetos |
| Veracode | Solução saas que fornece testes de segurança contínuos |
| Codeql | Análise de código da github para encontrar vulnerabilidades |

## 5. Vantagens e Desvantagens do Sast
- Redução de custos e riscos através da identificação prematura de falhas no ciclo de vida.
- Tendência a gerar um alto número de falsos positivos que podem exigir ajustes finos para não identificar riscos inexistentes.
- Dificuldade na análise de linguagens dinâmicas como JavaScript e Python onde o comportamento depende da execução;
- Incapacidade de detectar erros de configuração ou vulnerabilidades resultantes da interação com outros sistemas.

### 5.1 Comparação de Tipos de Teste
| SIGLA | NOME COMPLETO | TIPO DE CAIXA |
|---|---|---|
| Sast | Static application security testing | Caixa branca |
| Dast | Dynamic application security testing | Caixa preta |
| Iast | Interactive application security testing | Caixa cinza |

> [!TIP] DICAS: 
> - Guarde a regra: SAST = Sem execução = Código-fonte = Caixa Branca.
> - A estratégia de antecipar a segurança no desenvolvimento é o Shift-Left.

> [!CAUTION] OBSERVAÇÃO: 
> - O SAST deve ser realizado no início do processo e não após o sistema entrar em produção.
> - Embora o SAST analise a estrutura interna, ele não detecta falhas que só aparecem com o software rodando (como erros de ambiente).