# SAST (Static Application Security Testing)

## 1. Definição
- Abordagem de testes de segurança estáticos.
- Analisa o código-fonte, bytecode ou código compilado de um software sem executá-lo.
- Seu objetivo é identificar vulnerabilidades de segurança ainda na fase de desenvolvimento, reduzindo riscos antes da implantação da aplicação.

### 1.2 Funcionamento

#### Análise Estática
- O código é escaneado em busca de vulnerabilidades conhecidas, sem precisar executar o software.
 
#### Detecção de Vulnerabilidades
- Identifica falhas como injeção de SQL, XSS (Cross-Site Scripting), vazamento de dados sensíveis, uso inseguro de bibliotecas e erros de configuração.

#### Relatório de Segurança
- Gera insights para os desenvolvedores corrigirem as falhas antes da implantação.

#### Integração com CI/CD
- Incorporadas em pipelines DevSecOps para garantir verificações automáticas a cada atualização de código.

### 1.3 Principais Características
- Teste sem execução: Não depende da execução do software, diferentemente do DAST (Dynamic Application Security Testing).
- Detecta vulnerabilidades no código-fonte: Permite correção precoce, reduzindo custos de segurança.
- Integração com DevSecOps: Pode ser usado junto com ferramentas de CI/CD para análises automáticas.
- Cobertura de código: Avalia toda a base de código, incluindo caminhos de execução raramente testados manualmente.
- Análise de bibliotecas e dependências: Identifica vulnerabilidades em pacotes externos.

### 1.4 Vantagens
- Detecta vulnerabilidades cedo, reduzindo custos de correção.
- Cobertura completa do código, incluindo caminhos raramente testados.
- Integração com pipelines de CI/CD para segurança contínua.

### 1.5 Desvantagens
- Pode gerar falsos positivos, exigindo ajustes finos.
- Difícil para linguagens dinâmicas, como JavaScript e Python, onde o comportamento depende do ambiente de execução.
- Não detecta erros de configuração ou vulnerabilidades resultantes da interação da aplicação com outros sistemas.

### 1.6 Exemplos de Vulnerabilidades Detectadas
- Injeção de SQL.
- Cross-Site Scripting (XSS).
- Uso de funções inseguras.
- Vazamento de credenciais.
- Erros de controle de acesso.

### 1.7 Principais Ferramentas SAST
- SonarQube: Análise de código estático para detectar vulnerabilidades e falhas de qualidade.
- Checkmarx: Avaliação profunda de segurança de código.
- Fortify Static Code Analyzer: Ferramenta da Micro Focus para análise de segurança em grandes projetos.
- Veracode: Solução SaaS que fornece testes de segurança contínuos.
- CodeQL: Análise de código da GitHub para encontrar vulnerabilidades.

### 1.8 Integração do SAST com DevSecOps
- CI/CD Pipelines: Ferramentas como Jenkins, GitHub Actions e GitLab CI/CD podem executar verificações SAST automaticamente.
- Pré-commit Hooks: Integrado no ambiente do desenvolvedor para verificar código antes do commit.
- Segurança Shift-Left: Aplicação do SAST nas primeiras fases do desenvolvimento evita problemas críticos na produção.

> [!TIP] DICAS: 
> - SAST = Sem execução = Código-fonte = Caixa Branca.