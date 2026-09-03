# DAST (Dynamic Application Security Testing)

## 1. Definição
- Abordagem de teste de segurança dinâmico.
- Avalia aplicações em execução para identificar vulnerabilidades exploráveis externamente.

### 1.1 Funcionamento
- Varredura da Aplicação.
- Interage com a aplicação como um usuário mal-intencionado, explorando entradas e respostas.
- Execução de Testes de Segurança
- São enviadas requisições HTTP/HTTPS para testar vulnerabilidades, como injeções SQL, falhas de autenticação, XSS e ataques de negação de serviço (DoS).
- Relatório de Vulnerabilidades.
- Relatório apontando falhas detectadas e recomendações de correção.
- Integração com DevSecOps.
- Integrado em pipelines de CI/CD para testes contínuos.

### 1.2 Principais Características
- Avalia a aplicação como um usuário externo, simulando ataques reais.
- Não precisa de acesso ao código-fonte, funcionando em qualquer linguagem.
- Detecta falhas de segurança em tempo de execução, incluindo erros de configuração.
- Pode ser usado em aplicações já implantadas, sem impactar o desenvolvimento.

### 1.3 Vantagens
- Detecta vulnerabilidades no ambiente real de execução.
- Testa aplicações em produção ou em ambiente de homologação.
- Identifica falhas independentes da linguagem de programação.
- Integração com DevSecOps, permitindo testes contínuos.

### 1.4 Desvantagens
- Não analisa o código-fonte, podendo perder vulnerabilidades internas.
- Gera falsos negativos, pois não vê partes do código que não são executadas durante os testes.
- Pode ser demorado, pois realiza testes interativos e de força bruta.
- Necessidade de ambiente de testes, para evitar impactos em produção.

### 1.5 Principais Ferramentas
- OWASP ZAP: Ferramenta gratuita e popular para pentests e análise dinâmica.
- Burp Suite: Utilizado para testes manuais e automáticos de segurança web.
- Acunetix: Varredura de vulnerabilidades em aplicações web.
- IBM AppScan: Solução corporativa para testes dinâmicos de segurança.
- Tenable Nessus: Focado em análise de segurança e compliance.

### 1.6 Exemplos de vulnerabilidades encontradas
- Injeção de SQL.
- Cross-Site Scripting (XSS).
- Falhas de Autenticação.
- Erro de Configuração de Segurança.
- Exposição de Dados Sensíveis.

### 1.7 DAST no DevSecOps
- Pipelines de CI/CD: DAST pode ser integrado em ferramentas como Jenkins, GitHub Actions e GitLab CI/CD para testes automatizados.
- Monitoramento Contínuo: Algumas soluções permitem análises periódicas para verificar novas vulnerabilidades.
- Teste em Ambientes de Homologação: Ideal para evitar riscos de impacto em produção.

> [!TIP] DICAS: 
> - Teste recomendado por ambiente:
>   - Desenvolvimento: Sast (Análise estática do código-fonte);
>   - Homologação: Dast (Teste dinâmico antes da implantação);
>   - Produção: Dast (Monitoramento contínuo de vulnerabilidades).
> - O IAST (Interactive Application Security Testing) diferencia-se por operar dentro do aplicativo, funcionando como um módulo de segurança interno.