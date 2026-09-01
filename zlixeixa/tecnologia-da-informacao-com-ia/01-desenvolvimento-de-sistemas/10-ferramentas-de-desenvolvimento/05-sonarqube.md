# Análise Estática de Código Fonte com SonarQube

## 1. Conceito e Análise Estática
- SonarQube é um agregador de métricas utilizado para medir a qualidade do código de um sistema.
- A ferramenta realiza a análise estática de código, que consiste em um tipo de teste que não exige a execução do software.
- É desenvolvido em Java e capaz de rodar métricas para mais de 20 linguagens de programação, incluindo Java, C++, JavaScript, CSS, PHP e linguagens para dispositivos móveis.
- A solução implementa o conceito de clean as you code, sinalizando problemas sempre que detectados em códigos novos ou modificados.

> [!TIP] DICAS: 
> - A análise estática permite observar o código-fonte a partir de parâmetros específicos para identificar problemas sem rodar a aplicação.
> - Antigamente essa verificação era feita de forma manual por meio de check lists.

## 2. Diferenciação entre SAST e DAST
- SAST (Static Application Security Testing) ⟶ termo em inglês que corresponde à análise estática de código.
- DAST (Dynamic Application Security Testing) ⟶ corresponde à análise dinâmica, que envolve a execução do software para identificar falhas.
- As análises estática e dinâmica são técnicas complementares, pois a análise estática sozinha não garante que a aplicação atenda aos requisitos funcionais do usuário.

## 3. Arquitetura e Formas de Uso
- O SonarQube possui versões em nuvem (SonarQube Cloud) ou pode ser executado através de uma instância de servidor local (SonarQube Server).
- Pode ser acoplado diretamente às IDEs como Eclipse, Visual Studio e IntelliJ IDEA por meio do plugin SonarLint, permitindo a análise durante a programação.
- O uso básico consiste em gerar métricas via plugins (como o Maven para projetos Java) e consultar os resultados no painel do servidor.
- Integra-se com ferramentas de versionamento de código, como Git e GitLab, e com servidores de integração contínua como Jenkins e Hudson.

| VERSÃO | CARACTERÍSTICA |
|---|---|
| Community | Versão gratuita com recursos de análise estática padrão |
| Commercial | Versão paga com suporte a plugins específicos e recursos corporativos |
| Data Center | Edição que suporta alta disponibilidade |

## 4. Métricas e Qualidade do Código
- Complexidade Ciclomática ⟶ mede a quantidade de caminhos possíveis na execução do código com base em estruturas como ifs e loops.
- Débito Técnico (Technical Debt) ⟶ representa o esforço estimado, geralmente em tempo, necessário para corrigir pendências e odores de código identificados.
- Code Smells (Odores de Código) ⟶ indica um código de má qualidade que prejudica a manutenibilidade, como métodos longos ou classes excessivamente extensas.
- Duplicações ⟶ identifica blocos ou arquivos de código copiados que dificultam a manutenção e favorecem a propagação de bugs.
- Quality Gate ⟶ funciona como um índice de aprovação que define limites aceitáveis para métricas como cobertura de teste e percentual de duplicação.

> [!CAUTION] OBSERVAÇÃO: 
> - Cada função possui uma complexidade ciclomática mínima de 1.
> - O débito técnico ocorre principalmente em métodos ágeis devido às entregas incrementais que podem gerar soluções provisórias.

## 5. Regras e Severidade de Problemas
- As regras do SonarQube são divididas em quatro domínios: cheiro de código (manutenção), bug (confiabilidade), vulnerabilidade (segurança) e ponto de acesso de segurança (segurança).
- A classificação de confiabilidade varia de A (0 erros) até E (pelo menos 1 erro bloqueador).
- A ferramenta realiza análise de segurança incluindo itens listados no Top 10 da OWASP, como problemas de injection.

| SEVERIDADE | DEFINIÇÃO E AÇÃO |
|---|---|
| Blocker | Bug com alta probabilidade de impacto em produção; deve ser corrigido imediatamente |
| Critical | Bug com baixa probabilidade de impacto ou falha de segurança; deve ser revisado imediatamente |

> [!CAUTION] OBSERVAÇÃO: 
> - Nem todas as tags de regras podem ser removidas pelo usuário, pois algumas são fornecidas internamente pelos plugins.
> - A decisão final sobre a urgência da correção de uma issue cabe ao usuário da ferramenta.