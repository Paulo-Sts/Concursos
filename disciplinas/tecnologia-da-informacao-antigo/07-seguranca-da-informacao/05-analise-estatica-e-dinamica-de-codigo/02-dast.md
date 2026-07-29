# Anotações

# Testes de Segurança de Aplicações – DAST

## 1.1 Conceito de DAST

- ***DAST - Dynamic Application Security Testing***: abordagem de teste de segurança dinâmico.
- Avalia aplicações **em execução** para identificar vulnerabilidades exploráveis externamente.
- Simula **ataques reais** ao software, testando sua resiliência contra ameaças.
- É um teste de **caixa-preta** (*black box*), ou seja, não tem acesso ao código-fonte.
- Funciona inserindo entradas maliciosas (ex.: SQL Injection em formulários) em vez de saídas esperadas, para tentar explorar vulnerabilidades.

### 1.1.1 Exemplos de Vulnerabilidades Detectadas pelo DAST
- Injeção de SQL (*SQL Injection*).
- *Cross-Site Scripting* (XSS).
- Falhas de autenticação.
- Configuração inadequada de segurança.
- Exposição de dados sensíveis.

> [!TIP] DICAS
> - O DAST é **independente da linguagem de programação** – diferentemente do SAST, que é restrito à linguagem escolhida.
> - O DAST pode ser usado em **aplicações já implantadas**, inclusive em produção.
> - O DAST avalia a aplicação como um **usuário externo**, simulando ataques reais.

## 1.2 Funcionamento do DAST

### 1.2.1 Processo de Funcionamento
- **Varredura da aplicação:** simula um usuário mal-intencionado, explorando entradas e respostas.
- **Execução de testes de segurança:** envia requisições HTTP/HTTPS contendo pedaços de código específicos para testar injeções SQL, XSS, etc.
- **Possibilidade de ataques de negação de serviço (DoS):** enviando múltiplas requisições simultâneas.
- **Geração de relatório:** lista as vulnerabilidades, falhas e recomendações de correção.
- **Integração com DevSecOps:** faz parte do contexto de CI/CD.

> ### 1.2.2 Esquema de Funcionamento do DAST
> **Atenção/Exceção:** O processo segue um fluxo estruturado:
> 1. **Mapeamento** da aplicação.
> 2. **Escaneamento** e *crawling*.
> 3. **Tentativa de invasão** com técnicas conhecidas de DAST.
> 4. **Identificação e exploração** de vulnerabilidades.
> 5. **Relatório** com recomendações para correção.

## 1.3 Principais Características do DAST

| CARACTERÍSTICA | DESCRIÇÃO |
|----------------|-----------|
| Abordagem | Caixa-preta (sem acesso ao código-fonte) |
| Execução | Aplicação em execução |
| Independência de linguagem | Sim - não depende da linguagem de programação |
| Detecção | Falhas em tempo de execução e erros de configuração |
| Ambiente de aplicação | Pode ser usado em desenvolvimento, homologação e produção |

### 1.3.1 Ambientes de Aplicação do DAST
- **Ambiente de Desenvolvimento:** SAST é mais comum, mas DAST pode ser aplicado.
- **Ambiente de Homologação:** ambiente ideal para execução do DAST.
- **Ambiente de Produção:** possível rodar o DAST, mas com cautela.

> [!CAUTION] OBSERVAÇÃO
> - O **ambiente ideal** para o DAST é a **homologação**, pois testes como *Denial of Service* (DoS) podem derrubar o sistema.
> - Não há impedimento para rodar o DAST em produção, especialmente para sistemas que não passaram por essa análise anteriormente.
> - O DAST pode ser usado em **aplicações já implantadas**.

## 1.4 Vantagens e Desvantagens do DAST

### 1.4.1 Vantagens
- Detecta vulnerabilidades no **ambiente real de execução**.
- Testa aplicações em **produção ou homologação**.
- **Independente da linguagem de programação** (enxerga qualquer linguagem).
- Simula ataques reais, como um invasor faria.
- Integra com DevSecOps (CI/CD pipelines).

### 1.4.2 Desvantagens
- Pode causar **indisponibilidade do sistema** (especialmente com testes de DoS).
- O ideal é executar em ambiente **separado** (homologação) para evitar impactos em produção.
- Não possui acesso ao código-fonte, limitando a profundidade da análise.
- Requer atualização constante das regras à medida que o aplicativo muda.

## 1.5 Principais Ferramentas DAST

| FERRAMENTA | DESCRIÇÃO |
|------------|-----------|
| **OWASP ZAP** | Ferramenta mais utilizada para DAST e *pentests* |
| **Burp Suite** | Ferramenta popular para testes de segurança em aplicações web |
| **Acunetix** | Solução automatizada para varredura de vulnerabilidades |

## 1.6 DAST no DevSecOps

- Integra-se facilmente com *pipelines* de CI/CD.
- Algumas soluções permitem **análises periódicas** para verificar novas vulnerabilidades.
- Possibilita **monitoramento contínuo** em ambiente de produção.
- **Recomendação:** implantar o DAST preferencialmente no ambiente de homologação.

## 1.7 Comparativo SAST x DAST

| CARACTERÍSTICA | SAST | DAST |
|----------------|------|------|
| Momento do teste | Antes da execução | Durante a execução |
| Execução do software | Não é executado | Software em execução |
| Abordagem | Caixa-branca | Caixa-preta |
| Acesso ao código | Sim (código-fonte) | Não |
| Dependência de linguagem | Sim (restrito à linguagem) | Não (independente) |
| Ambiente ideal | Desenvolvimento | Homologação |
| Pode ser usado em produção | Não (código não executado) | Sim |
| Principais vulnerabilidades | SQL Injection, XSS, vazamento de credenciais, uso inseguro de bibliotecas | SQL Injection, XSS, falhas de autenticação, configuração inadequada, exposição de dados sensíveis |

> ### 1.7.1 Diagrama de Posicionamento no Ciclo DevSecOps
> **Atenção/Exceção:** No ciclo DevSecOps, o fluxo é:
> 1. **Planejamento** → **Codificação** → **Construção/Compilação**
> 2. **SAST** é aplicado durante a codificação ou após seu término (análise do código-fonte).
> 3. **Compilação** → **Testes com programa em atividade**
> 4. **DAST** é aplicado após a compilação, com o software em execução.
> 5. **Release/Implantação** → **Operação** → **Monitoramento**

## 1.8 Tabela Resumo - Testes de Segurança

| TESTE | SIGLA | MOMENTO | ABORDAGEM | EXECUÇÃO |
|-------|-------|---------|-----------|----------|
| Análise Estática | SAST | Antes da execução | Caixa-branca | Código não é executado |
| Análise Dinâmica | DAST | Em tempo de execução | Caixa-preta | Software em execução |
| Análise Interativa | IAST | Em tempo de execução | Caixa-cinza | Software em execução |

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/2023/TBG/ÊNFASE: DESENVOLVIMENTO DE SOFTWARE)

Julgue o próximo item, relativo a técnicas de desenvolvimento seguro. Ao contrário do teste de segurança estático (SAST) e do teste de segurança dinâmico (DAST), o teste interativo de segurança (IAST) opera dentro do aplicativo, além de permitir uma saída mais precisa.

**Gabarito:** C (Correto) - O IAST opera dentro do aplicativo, como se fosse um módulo de segurança.

## Questão 02
(SELECON/2022/IF-RJ/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO)

Entre os serviços para testar e monitorar a segurança de todos os seus sistemas, três são descritos a seguir.

I – Testa as interfaces expostas em busca de vulnerabilidades, sendo o teste feito de fora para dentro, da mesma forma que um invasor faria. Neste caso, a interface já é o suficiente para que o especialista realize o teste. À medida em que o aplicativo vai mudando e se atualizando, é preciso atualizar as regras dessa ferramenta, o que obriga a necessidade em investimento e acompanhamento durante todo o ciclo de vida do desenvolvimento.

II – Tem como objetivo identificar as vulnerabilidades no código-fonte antes de ele ser colocado em produção. Para tanto, são usadas técnicas de análise de código estático para procurar problemas sem precisar executar o código. Com isso, é uma ferramenta que consegue encontrar problemas com antecedência, antes da implantação e, por estar agindo no código, pode dar informações detalhadas à equipe para que os ajustes sejam feitos.

As ferramentas descritas em I e II são conhecidas, respectivamente, pelas siglas:

a) SAST e IAST.
b) DAST e SAST.
c) IAST e PENTEST.
d) PENTEST e DAST.

**Gabarito:** b

## Questão 03
(CESPE/CEBRASPE/2023/TBG/ÊNFASE: DESENVOLVIMENTO DE SOFTWARE)

Julgue o próximo item, relativo a técnicas de desenvolvimento seguro.

O teste de segurança estático (SAST) trabalha diretamente com o código e é empregado de forma complementar ao teste de segurança dinâmico (DAST).

**Gabarito:** E (Errado) - Embora ambos sejam usados no ciclo DevSecOps, o SAST não é empregado de forma complementar ao DAST, pois atuam em etapas diferentes. O SAST trabalha durante o desenvolvimento, enquanto o DAST atua na homologação.

## Questão 04
(CESPE/CEBRASPE/2024/SEBRAE/NACIONAL/ANALISTA TÉCNICO II/DESENVOLVIMENTO SOFTWARE)

Assinale a opção em que é citada a principal vantagem da integração de testes de segurança (SAST e DAST) no processo de implementação de *pipeline* de CI/CD.

a) Melhoria na documentação do código.
b) Identificação precoce de vulnerabilidades de segurança.
c) Redução do tempo de desenvolvimento.
d) Aumento da cobertura de testes funcionais.

**Gabarito:** b

## Questão 05
(CESPE/CEBRASPE/2023/DATAPREV/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO/PERFIL: SEGURANÇA CIBERNÉTICA)

De acordo com o que dispõem os conceitos de segurança da informação, julgue o item que se segue.

Uma das diferenças entre DAST e SAST é que enquanto o primeiro é uma abordagem de caixa-preta, sem acesso ao código-fonte, o outro, é uma abordagem de caixa branca, que analisa o código fonte durante a fase de desenvolvimento.

**Gabarito:** C (Correto)

## Questão 06
(PR-4/2023/UFRJ/ANALISTA DE TECNOLOGIA DA INFORMAÇÃO – SEGURANÇA)

Em relação a prática de revisão de código, analise as afirmativas abaixo:

I – DAST é uma abordagem de teste de segurança para avaliar a segurança de um software em tempo de execução.

II – SAST é útil para identificar vulnerabilidades estáticas no código-fonte de um aplicativo, como problemas de codificação, uso inadequado de APIs, vazamento de informações sensíveis e acesso não autorizado.

III – Tanto o DAST quanto o SAST desempenham papéis complementares na análise de segurança de um aplicativo, sendo recomendável utilizar ambos os métodos para obter uma cobertura abrangente e identificar uma ampla gama de vulnerabilidades.

Em relação aos itens acima, pode-se afirmar que:

a) Somente o item I é verdadeiro.
b) Todas as afirmativas são verdadeiras.
c) Somente o item II é verdadeiro.
d) Somente o item III é verdadeiro.
e) Todas as afirmativas são falsas.

**Gabarito:** b

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | C |
| 02 | b |
| 03 | E |
| 04 | b |
| 05 | C |
| 06 | b |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Vitor Kessler.*