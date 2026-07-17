# Anotações

# Low-Code e No-Code

## 1.1 Contexto e Definições

- Os processos **low-code** e **no-code** surgem como alternativa à **programação tradicional**, que exige conhecimento aprofundado de linguagens de programação.
- Ambas as abordagens visam:
  - Acelerar a transformação digital.
  - Reduzir o *backlog* de TI.
  - Democratizar o desenvolvimento de soluções.

### 1.1.1 Programação Tradicional
- Desenvolvimento utilizando linguagens formais (Java, C, Python, C#, JavaScript etc.) por meio de escrita manual de código-fonte estruturado.
- O desenvolvedor deve: conhecer sintaxe; entender estruturas de controle, lógica e algoritmos; modelar arquiteturas; gerenciar bancos de dados, integrações, segurança e testes.

**Vantagens:**
- Permite criar sistemas personalizados sem limitações (processo artesanal).
- Sistemas otimizados para alto desempenho e grande volume de usuários.
- Lógica de negócio, segurança e fluxo totalmente definidos pelo programador.
- Possibilidade de usar bibliotecas, *frameworks*, APIs e serviços diversos.
- Ideal para aplicações críticas (bancárias, segurança pública, saúde).

**Desvantagens:**
- Exige conhecimento técnico aprofundado e experiência.
- Projetos complexos demandam mais tempo de análise, codificação, testes e manutenção.
- Envolve times técnicos especializados e custos com infraestrutura.
- Áreas de negócio ficam limitadas à disponibilidade do setor técnico.
- Alterações em requisitos exigem reprogramação e novos ciclos de testes.

## 1.2 Low-Code

### 1.2.1 Conceito
- Abordagem de desenvolvimento que permite criar aplicações por meio de **interfaces visuais e ferramentas gráficas**, reduzindo significativamente a necessidade de codificação manual.
- Permite e exige **trechos de código** para personalizações mais avançadas.
- O que é construído visualmente (*drag-and-drop*) é traduzido automaticamente em código-fonte (Java, C#, JavaScript, HTML, SQL, XML ou JSON).

### 1.2.2 Público-alvo
- Programadores.
- Analistas técnicos com algum conhecimento de código.
- Times mistos (TI + negócio).

### 1.2.3 Características
- Interface visual (*drag-and-drop*) com blocos para construção de telas, fluxos e formulários.
- Suporte a scripts e códigos personalizados para regras de negócio, segurança e integrações complexas.
- Fácil conexão com bancos de dados, ERPs e APIs.
- Componentes reutilizáveis (*widgets*, fluxos, *templates*).
- *Deploy* simplificado (automatização em nuvem ou servidores internos).
- Governança de TI (versionamento, autenticação, segurança, permissões, rastreabilidade).
- Alta capacidade de customização (dentro das limitações da plataforma).

### 1.2.4 Funcionamento
1. **Modelagem visual:** usuário monta a aplicação com blocos visuais.
2. **Camada de metadados:** cada ação é registrada como metadado estruturado (XML ou JSON).
3. **Motor de renderização (*engine*):** converte metadados em código executável.
4. **Compilação/interpretação automática:** gera código *front-end* (HTML/CSS/JS), *back-end* (Java, C#, Node.js) e *queries* de banco de dados (SQL, LINQ).

### 1.2.5 Vantagens
- Acelera o desenvolvimento (ideal para transformação digital e MVPs).
- Permite customização com código para regras complexas.
- Reduz dependência total de programadores – especialistas de negócio podem colaborar.
- Facilita integração com sistemas existentes (conectores prontos ou APIs personalizadas).
- Escalável para ambientes corporativos (arquitetura em nuvem).

### 1.2.6 Desvantagens
- Limitações de customização total – plataforma pode não permitir alterar componentes de base.
- ***Lock-in* de fornecedor** – dependência da plataforma e licenças.
- Exige conhecimento técnico mínimo para integrações com sistemas externos.
- **Riscos de segurança:** aplicativos podem apresentar vulnerabilidades por implementação inadequada, limitações da plataforma ou ataques à própria plataforma.
- Difícil migração para desenvolvimento tradicional – projeto pode precisar ser refeito do zero.
- Escalabilidade pode ter limites.
- Vulnerabilidades podem baixar o nível de segurança.

## 1.3 No-Code

### 1.3.1 Conceito
- Abordagem ainda mais acessível que o *low-code*.
- **Não exige nenhum conhecimento prévio de programação.**
- Funciona no sistema de "clique e arraste" (*drag-and-drop*).
- O usuário deve se adaptar às **regras e limitações da plataforma**, utilizando módulos pré-construídos.
- Customização mínima – o produto é feito para criação dentro das estruturas definidas pela plataforma.

### 1.3.2 Público-alvo
- Usuários de negócio.
- Pessoas sem conhecimento técnico em programação.

### 1.3.3 Características
- Interface 100% visual.
- Sem necessidade de escrita de código.
- Utilização de módulos e *templates* prontos.
- Customização limitada às opções oferecidas pela plataforma.

## 1.4 Comparativo Geral

| ASPECTO | PROGRAMAÇÃO TRADICIONAL | LOW-CODE | NO-CODE |
|---------|------------------------|----------|---------|
| **Conhecimento necessário** | Alto (programação) | Baixo (algum código) | Nenhum |
| **Customização** | Total | Alta (dentro dos limites) | Mínima |
| **Velocidade de desenvolvimento** | Lenta | Rápida | Muito rápida |
| **Público-alvo** | Desenvolvedores | Programadores/analistas | Usuários de negócio |
| **Controle sobre o código** | Total | Parcial | Nenhum |
| **Ideal para** | Sistemas críticos | MVPs, transformação digital | Aplicações simples |

## 1.5 Segurança em Plataformas Low-Code

- A segurança **não depende exclusivamente** das práticas de desenvolvimento do usuário – também depende das condições oferecidas pela plataforma.
- A **integração com sistemas existentes pode introduzir vulnerabilidades específicas**.
- Plataformas *low-code* **não possuem segurança nativa que elimina todos os riscos**.
- A segurança **não é a mesma** em todas as plataformas – depende da plataforma utilizada e da aplicação criada.
- *Low-code* **pode ser utilizado** para desenvolver aplicações que exigem alta segurança, mas não é recomendado em determinados casos críticos.

> [!CAUTION] OBSERVAÇÃO
> **Sistemas hipercríticos** (bancários, de segurança, de saúde) ainda exigem programação tradicional, pois necessitam de flexibilidade e controle total.

---

# Questões de Fixação

## Questão 01
(CESPE/CEBRASPE/2022/BNB/ANALISTA DE SISTEMAS/DESENVOLVIMENTO DE SISTEMAS)

Com relação aos conceitos de sistemas operacionais, julgue o seguinte item.

Low-code foi criado para desenvolver interfaces que funcionassem sem alfabetização em nenhum idioma e, principalmente, sem alfabetização em inglês.

**Gabarito:** E (Errado) - Low-code foi criado para desenvolvimento por usuários com **baixo conhecimento de programação**, não para eliminar a alfabetização.

## Questão 02
(CESPE/CEBRASPE/2024/ANVISA/ESPECIALISTA EM REGULAÇÃO E VIGILÂNCIA SANITÁRIA/ÁREA 4)

Em relação ao desenvolvimento e à sustentação de software e ao gerenciamento de produtos de software, julgue o item a seguir.

A principal diferença entre as plataformas de desenvolvimento low-code e no-code é o conhecimento de codificação do usuário.

**Gabarito:** C (Correto)

## Questão 03
(IBFC/2024/TRF/5ª REGIÃO/ANALISTA JUDICIÁRIO/ÁREA APOIO ESPECIALIZADO/ESPECIALIDADE: ANÁLISE DE SISTEMAS DE INFORMAÇÃO)

Assinale a alternativa correta que apresenta a principal vantagem das plataformas Low-Code no desenvolvimento de aplicações corporativas.

a) Eliminar a necessidade de testes de script em todos os processos.
b) Garantir que apenas desenvolvedores altamente qualificados possam criar aplicações eficientes.
c) Permitir o desenvolvimento de soluções digitais com o mínimo de codificação, utilizando ferramentas visuais de arrastar e soltar.
d) Exigir que todo o código seja escrito manualmente para garantir maior controle sobre o produto final.

**Gabarito:** c

## Questão 04
(IBFC/2024/TRF/5ª REGIÃO/ANALISTA JUDICIÁRIO/ÁREA APOIO ESPECIALIZADO/ESPECIALIDADE: ANÁLISE DE SISTEMAS DE INFORMAÇÃO)

Assinale a alternativa que apresenta de que forma as plataformas Low-Code contribuem para a inovação nas organizações, especialmente no contexto de desenvolvimento ágil.

a) Ao centralizar todo o desenvolvimento em equipes especializadas, limitando a participação de outros departamentos.
b) Ao permitir que especialistas de negócios sem habilidades avançadas em codificação desenvolvam rapidamente aplicações funcionais, acelerando o ciclo de inovação.
c) Ao reduzir a necessidade de interação entre equipes de TI e de negócios, tornando o processo mais segmentado e eficiente.
d) Ao garantir que todas as aplicações desenvolvidas sigam o mesmo ciclo de vida, independentemente da complexidade dos requisitos.

**Gabarito:** b

## Questão 05
(FCC/2025/TRT/15ª REGIÃO (SP)/TÉCNICO JUDICIÁRIO/ÁREA APOIO ESPECIALIZADO/ESPECIALIDADE TECNOLOGIA DA INFORMAÇÃO)

Ao ser questionado sobre a segurança em plataformas low-code, uma Técnica de um Tribunal Regional do Trabalho respondeu, corretamente que

a) a segurança em low-code depende exclusivamente das práticas de desenvolvimento do usuário.
b) a integração com sistemas existentes pode introduzir vulnerabilidades específicas.
c) plataformas low-code possuem segurança nativa que elimina todos os riscos de segurança.
d) todas as plataformas low-code garantem a mesma qualidade de segurança.
e) low-code não pode ser utilizado para desenvolver aplicações que exigem alta segurança.

**Gabarito:** b

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | E |
| 02 | C |
| 03 | c |
| 04 | b |
| 05 | b |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Júlio César Batista Leitão.*