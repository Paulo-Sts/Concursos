# Anotações

# Low-Code e No-Code II

## 1.1 No-Code – Aprofundamento

### 1.1.1 Conceito
- Abordagem de desenvolvimento que **dispensa completamente** o uso de linguagens de programação tradicionais.
- Aplicações criadas exclusivamente por **interfaces gráficas**, com blocos visuais, menus de configuração e modelos prontos.
- Baseado no conceito de **desenvolvimento declarativo** (o usuário declara o que deseja, e a plataforma gera o código).

### 1.1.2 Público-alvo
- **Cidadãos desenvolvedores** (*citizen developers*) – usuários de negócio (RH, financeiro, jurídico).
- Colaboradores que não atuam diretamente com TI, mas desejam digitalizar processos internos.
- Equipes de inovação e transformação digital.

### 1.1.3 Citizen Developer – Definição Gartner
> **Atenção/Exceção:** A Gartner define *citizen developer* como:
> - Colaborador que cria funcionalidades de aplicativos para uso próprio ou de terceiros.
> - Utiliza ferramentas que **não são explicitamente proibidas** pelas áreas de TI ou pelas unidades de negócio.
> - É uma **persona** (perfil de usuário), não um cargo formal ou função designada.
> - Está vinculado a uma unidade de negócio ou área funcional que **não pertence ao setor de TI**.

### 1.1.4 Características do No-Code
- **100% visual:** todo o processo de construção (UI, lógica, banco, automações) é feito com blocos visuais.
- **Sem código-fonte visível:** não há necessidade nem opção de digitar código tradicional.
- **Blocos de funcionalidades:** comandos de lógica, fluxos, integrações e bancos de dados encapsulados em componentes prontos.
- **Modelos reutilizáveis:** *templates* prontos e configuráveis para sistemas comuns (cadastro, controle, CRM etc.).
- **Conectores nativos:** integração com planilhas, bancos, APIs REST/SOAP, redes sociais e ferramentas como Google Workspace ou Microsoft 365.

### 1.1.5 Vantagens do No-Code
- Desenvolvimento **extremamente ágil** – aplicações criadas em minutos ou poucas horas.
- **Zero conhecimento técnico** necessário – ideal para usuários que não sabem programar.
- **Baixo custo inicial** – sem necessidade de contratar desenvolvedores.
- **Autonomia do setor de negócio** – libera a TI de demandas mais simples.
- **Automação de tarefas repetitivas** – ideal para processos simples e rotinas administrativas.

### 1.1.6 Desvantagens do No-Code
- **Baixa flexibilidade:** aplicações limitadas a blocos disponíveis na plataforma.
- **Customização restrita:** não permite regras de negócio complexas fora do que é suportado.
- **Risco de Shadow IT:** soluções paralelas sem validação técnica pela equipe de TI.
- **Dependência da plataforma:** forte *vendor lock-in* (dificuldade de migração futura).
- **Dificuldade de escalabilidade:** não recomendado para sistemas críticos, complexos ou com alto volume de dados.
- **Vulnerabilidades da plataforma.**

> [!CAUTION] OBSERVAÇÃO
> **As plataformas *no-code* NÃO eliminam completamente os riscos relacionados à segurança.** Embora utilizem interfaces visuais e intuitivas, ainda estão sujeitas a vulnerabilidades.

### 1.1.7 Ferramentas No-Code
- Exemplos: **Bubble**, **Airtable**, **Glide**, **Adalo**, **Zapier** (automações), **Make** (antiga Integromat).

## 1.2 Comparativo Detalhado – Low-Code x No-Code

| ASPECTO | LOW-CODE | NO-CODE |
|---------|----------|---------|
| **Conhecimento necessário** | Básico/intermediário de programação | Nenhum |
| **Escrita de código** | Permite trechos de código | Não permite |
| **Customização** | Alta (dentro dos limites) | Mínima/restrita |
| **Público-alvo** | Programadores, analistas técnicos | Usuários de negócio, *citizen developers* |
| **Flexibilidade** | Média/alta | Baixa |
| **Ideal para** | MVPs, transformação digital, sistemas de média complexidade | Automação de processos simples, prototipagem rápida |

## 1.3 Considerações sobre Segurança em Low-Code/No-Code

- A segurança **não depende unicamente** da infraestrutura de *cloud* dos fornecedores.
- Aplicações desenvolvidas com essas plataformas **possuem código** que é executado pelo computador – a ausência de escrita manual não significa ausência de código.
- A integração com sistemas existentes **pode introduzir vulnerabilidades específicas**.
- **Não há segurança nativa que elimina todos os riscos.**

> [!TIP] DICAS
> - **A compatibilidade com diversas plataformas e dispositivos é uma VANTAGEM, não uma limitação,** das plataformas *low-code* e *no-code*.
> - As abordagens *low-code/no-code* permitem o **lançamento mais rápido de protótipos e MVPs** em comparação com o desenvolvimento tradicional.

## 1.4 Aplicações Adequadas para Low-Code/No-Code

### 1.4.1 Aplicações Típicas
- Assistentes virtuais e ferramentas de *chatbot*.
- Ferramentas RPA para automação de processos administrativos de *back-office*.
- Aplicativos para divulgação de campanhas de *e-mail marketing*.
- Automação de fluxos de trabalho internos (solicitações de férias, gestão de inventário de TI, coleta de dados por questionários, *dashboards* para relatórios gerenciais).

### 1.4.2 Aplicações NÃO Recomendadas
- **Apps de *internet banking*** (alta segurança, complexidade e personalização).
- **Cálculo automatizado de sentenças judiciais** (sistemas críticos que demandam alto grau de customização e segurança).
- **Sistemas de controle de processos judiciais em tempo real** com lógicas precisas de automação de decisões.
- **Ferramentas para controle automatizado de carro autônomo** (alta complexidade).
- **Migração de sistemas legados de *mainframes* para *cloud*** com recursos customizados de controle sobre desempenho e segurança.

## 1.5 Boas Práticas para Low-Code/No-Code

- **Implementar governança de TI** que inclua:
  - Revisões de segurança e conformidade das aplicações desenvolvidas.
  - Políticas de controle de versão.
- Avaliar caso a caso se aplicações críticas devem ser desenvolvidas em paralelo com métodos tradicionais – não é uma prática recomendada de forma geral.

## 1.6 Tabela Resumo – Low-Code x No-Code

| ASPECTO | LOW-CODE | NO-CODE |
|---------|----------|---------|
| **Escrita de código** | Mínima (permite personalização) | Nenhuma |
| **Conhecimento técnico** | Básico | Nenhum |
| **Customização** | Alta | Baixa |
| **Flexibilidade** | Média | Baixa |
| **Velocidade** | Rápida | Muito rápida |
| **Público-alvo** | Programadores/analistas | *Citizen developers* |
| **Risco de Shadow IT** | Médio | Alto |

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/2025/TRF/6ª REGIÃO/TÉCNICO JUDICIÁRIO/ÁREA: APOIO ESPECIALIZADO/ESPECIALIDADE: DESENVOLVIMENTO DE SISTEMAS DE INFORMAÇÃO)

Acerca de ferramentas de codeless e nocode, julgue o item subsequente:

Uma das vantagens das ferramentas de nocode é a possibilidade de customizações específicas para cada aplicação.

**Gabarito:** E (Errado) - Uma das limitações das ferramentas *nocode* é justamente a restrição quanto a customizações muito específicas.

## Questão 02
(CESPE/CEBRASPE/2025/TRF/6ª REGIÃO/TÉCNICO JUDICIÁRIO/ÁREA: APOIO ESPECIALIZADO/ESPECIALIDADE: DESENVOLVIMENTO DE SISTEMAS DE INFORMAÇÃO)

Acerca de ferramentas de codeless e nocode, julgue o item subsequente.

As plataformas nocode permitem a utilização de componentes gráficos de front-end e back-end, bem como possibilitam integrações com sistemas externos.

**Gabarito:** C (Correto)

## Questão 03
(CESPE/CEBRASPE/2023/SERPRO/ANALISTA/ESPECIALIZAÇÃO: TECNOLOGIA)

Acerca das abordagens low-code e no-code, julgue o item subsequente.

Low-code e no-code são abordagens que utilizam plataformas visuais e intuitivas para facilitar o desenvolvimento de aplicativos de forma segura, sem oferecer riscos.

**Gabarito:** E (Errado) - Embora utilizem plataformas visuais e intuitivas, não eliminam completamente os riscos relacionados à segurança.

## Questão 04
(CS-UFG/2024/TJ-AC/ANALISTA JUDICIÁRIO/ANALISTA DE MONITORAMENTO DE TI)

Leia o texto a seguir.

No geral, o surgimento do low-code e do no-code reflete uma mudança nas abordagens tradicionais de desenvolvimento de software, visando maior velocidade, agilidade e participação dos usuários finais no processo de criação de soluções digitais.

A diferença entre desenvolvimento de software usando low-code e no-code está descrita em:

a) o desenvolvimento no-code não envolve a escrita de código tradicional, enquanto o desenvolvimento low-code permite a integração de código personalizado, se necessário.
b) o desenvolvimento low-code permite a personalização e a extensão do código fonte, enquanto o desenvolvimento no-code geralmente está restrito a modelos predefinidos.
c) o desenvolvimento no-code é mais complexo e requer habilidades avançadas de programação, enquanto o desenvolvimento low-code é mais simples e acessível a usuários não técnicos.
d) o desenvolvimento low-code exige conhecimentos avançados de linguagens de programação, enquanto o desenvolvimento no-code não requer conhecimento técnico prévio.

**Gabarito:** a

## Questão 05
(FGV/2024/MF/AUDITOR FEDERAL DE FINANÇAS E CONTROLE/ÁREA DE TECNOLOGIA DA INFORMAÇÃO/TRANSFORMAÇÃO DIGITAL/MANHÃ)

As plataformas no-code e low-code têm transformado o desenvolvimento de software, permitindo que usuários com pouca ou nenhuma habilidade de programação criem aplicativos e soluções digitais. Considerando a emergência e o impacto dessas tecnologias, analise as afirmações a seguir sobre ferramentas no-code e low-code.

I – Plataformas no-code permitem que profissionais não técnicos desenvolvam aplicativos complexos sem escrever uma única linha de código, utilizando interfaces gráficas e funcionalidades de arrastar e soltar.

II – Embora as ferramentas low-code reduzam a necessidade de codificação, elas ainda exigem algum conhecimento técnico para a implementação de funcionalidades personalizadas e integração com outros sistemas.

III – A escalabilidade e a segurança de soluções desenvolvidas com ferramentas no-code e low-code dependem unicamente das infraestruturas de cloud providas pelos fornecedores dessas plataformas, sem espaço para otimizações específicas ao contexto de uso.

IV – Embora ferramentas no-code e low-code facilitem a prototipagem e o desenvolvimento rápido, elas exigem uma compreensão detalhada dos processos de negócio para que as aplicações finais atendam efetivamente às necessidades dos usuários sem gerar redundâncias funcionais.

Está correto o que se afirma em:

a) I e IV, apenas.
b) II e III, apenas.
c) I, II e IV, apenas.
d) II, III e IV, apenas.
e) I, II, III e IV.

**Gabarito:** c

## Questão 06
(FCC/2025/TRT/15ª REGIÃO SP/ANALISTA JUDICIÁRIO/ÁREA APOIO ESPECIALIZADO/ESPECIALIDADE TECNOLOGIA DA INFORMAÇÃO)

Um Tribunal Regional do Trabalho implementou uma plataforma no-code para permitir que diferentes departamentos criem seus próprios aplicativos de gestão de tarefas e projetos. Após seis meses de uso, a administração avaliou que os resultados obtidos no uso de plataformas no-code está em consonância com o que é frequentemente associado com:

a) o aumento da dependência da equipe de TI para manutenção de sistemas.
b) a redução na capacidade de personalização das soluções.
c) a maior complexidade na integração com sistemas existentes.
d) a necessidade contínua de treinamento intensivo para todos os funcionários.
e) a redução do tempo de desenvolvimento e entrega de soluções, permitindo uma resposta mais rápida às necessidades do negócio.

**Gabarito:** e

## Questão 07
(CESPE/CEBRASPE/2024/TSE/ANALISTA JUDICIÁRIO/ÁREA: APOIO ESPECIALIZADO/ESPECIALIDADE: TECNOLOGIA DA INFORMAÇÃO)

No que diz respeito à resiliência de aplicações na engenharia de software e ao desenvolvimento de software low-code e no-code, julgue o item que se segue.

A compatibilidade de funcionalidades prontas para o uso com diversas plataformas e dispositivos dos usuários é uma característica limitante do uso das plataformas de low-code e(ou) no-code.

**Gabarito:** E (Errado) - A compatibilidade com diversas plataformas e dispositivos é uma **vantagem**, não uma limitação.

## Questão 08
(IBFC/2024/TRF/5ª REGIÃO/ANALISTA JUDICIÁRIO/ÁREA APOIO ESPECIALIZADO/ESPECIALIDADE: ANÁLISE DE SISTEMAS DE INFORMAÇÃO)

Assinale a alternativa que apresenta a principal diferença entre as plataformas de desenvolvimento Low-Code e No-Code.

a) Plataformas Low-Code exigem conhecimento avançado de codificação, enquanto No-Code requer habilidades básicas de programação.
b) Plataformas Low-Code permitem o desenvolvimento sem qualquer necessidade de codificação, enquanto No-Code exige habilidades de programação para aplicações complexas.
c) Plataformas Low-Code requerem habilidades básicas de codificação para desenvolver aplicações, enquanto No-Code não exige nenhum conhecimento de programação.
d) Tanto Low-Code quanto No-Code exigem conhecimento técnico profundo para a criação de aplicações simples e complexas.

**Gabarito:** c

## Questão 09
(CESPE/CEBRASPE/2025/TRF/6ª REGIÃO/TÉCNICO JUDICIÁRIO/ÁREA: APOIO ESPECIALIZADO/ESPECIALIDADE: DESENVOLVIMENTO DE SISTEMAS DE INFORMAÇÃO)

Acerca de ferramentas de codeless e nocode, julgue o item subsequente. Aplicações desenvolvidas com os conceitos de codeless não possuem nenhuma linha de código que seja executada pelo computador.

**Gabarito:** E (Errado) - Embora o usuário não precise escrever código, a aplicação gerada pelas ferramentas *codeless* depende de **código** para ser executada pelo computador.

## Questão 10
(CESPE/CEBRASPE/2022/PGE-RJ/ANALISTA DE SISTEMAS E MÉTODOS)

A respeito de engenharia de software e de requisitos, julgue o item.

Uma das vantagens dos conceitos codeless e nocode sobre o desenvolvimento tradicional é o lançamento mais rápido de protótipos e do MVP (mínimo produto viável) do sistema.

**Gabarito:** C (Correto)

## Questão 11
(FCC/2022/PGE-AM/TÉCNICO EM GESTÃO PROCURATORIAL/ESPECIALIDADE ENGENHARIA DE SOFTWARE)

Tradicionalmente, as organizações têm duas alternativas quando precisam de um novo sistema de informação: construí-lo usando seu time de desenvolvedores ou comprá-lo de um fornecedor externo. O desenvolvimento Low Code (LC) e No Code (NC) tem se despontado como uma alternativa, pois

a) pode proporcionar soluções próximas aos requisitos de negócios, podendo ser implementado rapidamente, embora custe muito mais do que os sistemas desenvolvidos internamente.
b) utiliza ferramentas cujas interfaces tornam a criação de novos aplicativos apenas uma questão de apontar e clicar ou configurar menus, podendo substituir os profissionais de TI, já que não exige nenhum nível de conhecimento técnico para dimensionar, manter, integrar e governar os sistemas.
c) expande o tipo de pessoas que podem criar aplicativos dentro de uma empresa. No entanto, há uma ressalva importante: o software LC/NC exige algum nível de envolvimento do time de TI quando se trabalha em sistemas críticos.
d) o software LC não exige nenhum nível de habilidade de programação, podendo ser usado por empresários não técnicos para melhorar sua produtividade.
e) o software NC geralmente é usado por funcionários híbridos de negócios/TI conhecidos como "citizen developers". Para as empresas, isso as ajuda a digitalizar e automatizar tarefas e processos mais rapidamente, dispensando a contratação de desenvolvedores.

**Gabarito:** c

## Questão 12
(FCC/2024/TRT/20ª REGIÃO (SE)/ANALISTA JUDICIÁRIO/ÁREA APOIO ESPECIALIZADO/ESPECIALIDADE TECNOLOGIA DA INFORMAÇÃO)

A equipe de TI de um Tribunal estava sobrecarregada com demandas de novos sistemas, além da necessidade de manutenção de aplicações legadas. Foi definida, então, uma estratégia de utilização de plataformas Low-code e No-code visando aumentar a agilidade no desenvolvimento, além de permitir que setores não técnicos desenvolvessem suas próprias ferramentas. O conjunto de aplicações adequadas para desenvolvimento utilizando estas plataformas, considerando as vantagens e limitações dessas abordagens, inclui:

a) migração de sistemas legados de mainframes para cloud, com recursos customizados de controle sobre desempenho e segurança.
b) cálculo automatizado de sentenças judiciais e sistemas voltados para análise preditiva avançada de processos trabalhistas críticos e confidenciais.
c) sistemas de controle de processos judiciais em tempo real, com lógicas precisas de automação de decisões judiciais, integração com múltiplos bancos de dados e alto desempenho em processamento de grandes volumes de dados.
d) funcionalidades para o sistema de gestão de casos judiciais, incluindo a integração com APIs governamentais, bancos de dados distribuídos e lógica de negócios customizada.
e) automação de fluxos de trabalho internos, como solicitações de férias e folgas, gestão de inventário de TI, aplicativos para coleta de dados através de questionários e dashboards para visualização de relatórios gerenciais.

**Gabarito:** e

## Questão 13
(CESPE/CEBRASPE/2023/SEFIN DE FORTALEZA—CE/ANALISTA FAZENDÁRIO MUNICIPAL/ÁREA DE CONHECIMENTO: CIÊNCIA DA COMPUTAÇÃO/INFORMÁTICA/PROCESSAMENTO DE DADOS)

Com relação à Low/No Code e robot process automation (RPA), julgue o próximo item.

Low/No Code é uma técnica automática de programação que propicia a evolução de programas de computadores que resolvem (ou aproximadamente resolvem) problemas; ela manipula soluções corretas e incorretas, encoraja inconsistências e abordagens contraditórias e não apresenta uma variabilidade dinâmica lógica.

**Gabarito:** E (Errado) - A descrição apresentada diverge das abordagens *Low-Code* e *No-Code*.

## Questão 14
(IBFC/2024/TRF/5ª REGIÃO/ANALISTA JUDICIÁRIO/ÁREA APOIO ESPECIALIZADO/ESPECIALIDADE: ANÁLISE DE SISTEMAS DE INFORMAÇÃO)

Considere a lista de aplicações abaixo.

I – Assistentes virtuais e ferramentas de chatbot.
II – App de internet banking.
III – Ferramenta RPA para automatizar um processo administrativo de back-office.
IV – App para divulgação de campanha de e-mail marketing.
V – Ferramenta para controle automatizado de carro autônomo.

As aplicações que pertencem a categorias típicas de sistemas Low-code/No-Code são as que constam APENAS em:

a) I, II e V.
b) II, III e IV.
c) III e IV.
d) I, III e IV.
e) I, IV e V.

**Gabarito:** d

## Questão 15
(FGV/2024/TCE—PA/AUDITOR DE CONTROLE EXTERNO/ÁREA DE INFORMÁTICA/ANALISTA DE SISTEMAS)

Em relação ao desenvolvimento de software utilizando plataformas low-code e no-code, analise as práticas a seguir.

I – Implementar uma governança de TI que inclua revisões de segurança e conformidade das aplicações desenvolvidas, além de políticas de controle de versão.

II – Utilizar apenas as bibliotecas e componentes internos da plataforma para evitar incompatibilidades e problemas de integração.

III – Desenvolver todas as aplicações críticas em paralelo utilizando métodos tradicionais de desenvolvimento para garantir a redundância.

Para garantir que as aplicações desenvolvidas atendam às boas práticas para segurança, escalabilidade e manutenção, é(são) correta(s) a(s) prática(s):

a) I, apenas.
b) II, apenas.
c) III, apenas.
d) I e III, apenas.
e) II e III, apenas.

**Gabarito:** a

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | E |
| 02 | C |
| 03 | E |
| 04 | a |
| 05 | c |
| 06 | e |
| 07 | E |
| 08 | c |
| 09 | E |
| 10 | C |
| 11 | c |
| 12 | e |
| 13 | E |
| 14 | d |
| 15 | a |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Júlio César Batista Leitão.*