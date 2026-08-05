# Dast

## 1. Conceito e Definição de Dast
- Abordagem de teste de segurança dinâmico que avalia aplicações em execução.
- Identificação de vulnerabilidades exploráveis externamente através da simulação de ataques reais para testar a resiliência do software.
- Classificação como teste de caixa-preta, no qual se avalia a interação entre entradas e saídas com o software rodando.
- Exemplos de ameaças detectadas: 
  - Injeção de SQL;
  - XSS (Cross-Site Scripting);
  - Falhas de autenticação;
  - Configuração inadequada.

## 2. Integração no Ciclo DevSecOps
- Inserção das estratégias de segurança dentro do ciclo de desenvolvimento e operações.
- O ciclo compreende as fases de planejamento ⟶ codificação ⟶ construção ⟶ compilação ⟶ teste ⟶ release ⟶ implantação ⟶ operação ⟶ monitoramento.
- O SAST (Static Application Security Testing) ocorre durante ou ao fim da codificação para análise automatizada do código-fonte.
- O DAST é executado após a compilação, com o programa em atividade e antes da entrada definitiva em produção.

### 2.1 Diferenças entre Abordagens de Teste
| CARACTERÍSTICA | SAST | DAST |
|---|---|---|
| Nome | Static application security testing | Dynamic application security testing |
| Tipo de caixa | Caixa branca | Caixa preta |
| Momento de execução | Durante o desenvolvimento | Em tempo de execução |
| Acesso ao código | Possui acesso ao código-fonte | Não possui acesso ao código-fonte |

## 3. Funcionamento e Processo de Execução
- Realização de varredura de aplicação simulando o comportamento de um usuário mal-intencionado para explorar entradas e respostas.
- Execução de testes de segurança através do envio de requisições HTTP e HTTPS com pedaços de código específicos para testes de injeção.
- Possibilidade de realizar ataques de negação de serviço (DoS) enviando múltiplas requisições simultâneas.
- Fluxo de trabalho esquemático: 
  - Mapeamento da aplicação;
  - Escaneamento e crawling;
  - Detecção de vulnerabilidades;
  - Exploração das falhas;
  - Relatório e recomendações de remediação.

## 4. Características Principais do Método
- Avaliação do sistema sob a perspectiva de um usuário externo.
- Independência da linguagem de programação, pois foca nas interfaces expostas e não na estrutura do código.
- Detecção de falhas que ocorrem especificamente em tempo de execução, incluindo erros de configuração de segurança.
- Aplicabilidade tanto em sistemas já implantados quanto em ambiente de homologação.

### 4.1 Gestão de Ambientes de Teste
| AMBIENTE | TESTE RECOMENDADO | AÇÃO REALIZADA |
|---|---|---|
| Desenvolvimento | Sast | Análise estática do código-fonte |
| Homologação | Dast | Teste dinâmico antes da implantação |
| Produção | Dast | Monitoramento contínuo de vulnerabilidades |

## 5. Vantagens e Desvantagens do Dast
- Identificação de vulnerabilidades no ambiente real de execução e integração facilitada com pipelines de CI/CD.
- Independência tecnológica permitindo a análise de qualquer linguagem de programação.
- Ausência de visão do código-fonte, o que impede a identificação de falhas na lógica interna ou códigos de apoio.
- Tendência à geração de falsos negativos devido à cobertura parcial do código não executado.
- Procedimento considerado mais demorado que o SAST, especialmente quando utiliza técnicas de força bruta para testes.

## 6. Ferramentas e Vulnerabilidades Comuns
- Utilização de softwares especializados para automação do processo: 
  - OWASP ZAP (ferramenta mais utilizada para DAST e pentests);
  - Burp Suite;
  - Acunetix;
  - IBM AppScan;
  - Tenable Nessus.
- Exemplos de falhas recorrentes identificadas: 
  - Exposição de dados sensíveis;
  - Injeção de SQL;
  - Cross-site scripting (XSS);
  - Falhas de autenticação;
  - Erros de configuração de segurança.

> [!TIP] DICAS: 
> - A principal vantagem da integração de SAST e DAST no pipeline de CI/CD é a identificação precoce de vulnerabilidades de segurança.
> - O DAST testa as interfaces expostas de fora para dentro, simulando o comportamento de um invasor.

> [!CAUTION] OBSERVAÇÃO: 
> - É recomendável que o DAST seja realizado em ambiente de homologação separado para evitar que ataques simulados (como DoS) derrubem o sistema em produção.
> - SAST e DAST desempenham papéis complementares, sendo recomendável o uso de ambos para obter cobertura abrangente.
> - O IAST (Interactive Application Security Testing) diferencia-se por operar dentro do aplicativo, funcionando como um módulo de segurança interno.