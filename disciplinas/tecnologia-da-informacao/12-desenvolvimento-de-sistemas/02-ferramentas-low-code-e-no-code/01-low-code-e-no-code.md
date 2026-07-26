# Low-Code e No-Code

## 1. Contexto e Definições
- Os processos low-code e no-code surgem como alternativa à programação tradicional, que exige conhecimento aprofundado de linguagens de programação.
- Ambas as abordagens visam:
  - Acelerar a transformação digital;
  - Reduzir o backlog de TI;
  - Democratizar o desenvolvimento de soluções.

## 2. Programação Tradicional

### 2.1 Definição
- Desenvolvimento utilizando linguagens formais (Java, C, Python, C#, JavaScript etc.) por meio de escrita manual de código-fonte estruturado.
- O desenvolvedor deve: conhecer sintaxe; entender estruturas de controle, lógica e algoritmos; modelar arquiteturas; gerenciar bancos de dados, integrações, segurança e testes.

### 2.2 Vantagens
- Permite criar sistemas personalizados sem limitações (processo artesanal);
- Sistemas otimizados para alto desempenho e grande volume de usuários;
- Lógica de negócio, segurança e fluxo totalmente definidos pelo programador;
- Possibilidade de usar bibliotecas, frameworks, APIs e serviços diversos;
- Ideal para aplicações críticas (bancárias, segurança pública, saúde).

### 2.3 Desvantagens
- Exige conhecimento técnico aprofundado e experiência;
- Projetos complexos demandam mais tempo de análise, codificação, testes e manutenção;
- Envolve times técnicos especializados e custos com infraestrutura;
- Áreas de negócio ficam limitadas à disponibilidade do setor técnico;
- Alterações em requisitos exigem reprogramação e novos ciclos de testes.

## 3. Low-Code

### 3.1 Conceito
- Abordagem de desenvolvimento que permite criar aplicações por meio de interfaces visuais e ferramentas gráficas, reduzindo significativamente a necessidade de codificação manual.
- Permite e exige trechos de código para personalizações mais avançadas.
- O que é construído visualmente (drag-and-drop) é traduzido automaticamente em código-fonte (Java, C#, JavaScript, HTML, SQL, XML ou JSON).

### 3.2 Público-alvo
- Programadores;
- Analistas técnicos com algum conhecimento de código;
- Times mistos (TI + negócio).

### 3.3 Características
- Interface visual (drag-and-drop) com blocos para construção de telas, fluxos e formulários;
- Suporte a scripts e códigos personalizados para regras de negócio, segurança e integrações complexas;
- Fácil conexão com bancos de dados, ERPs e APIs;
- Componentes reutilizáveis (widgets, fluxos, templates);
- Deploy simplificado (automatização em nuvem ou servidores internos);
- Governança de TI (versionamento, autenticação, segurança, permissões, rastreabilidade);
- Alta capacidade de customização (dentro das limitações da plataforma).

### 3.4 Funcionamento
1. Modelagem visual: usuário monta a aplicação com blocos visuais;
2. Camada de metadados: cada ação é registrada como metadado estruturado (XML ou JSON);
3. Motor de renderização (engine): converte metadados em código executável;
4. Compilação/interpretação automática: gera código front-end (HTML/CSS/JS), back-end (Java, C#, Node.js) e queries de banco de dados (SQL, LINQ).

### 3.5 Vantagens
- Acelera o desenvolvimento (ideal para transformação digital e MVPs);
- Permite customização com código para regras complexas;
- Reduz dependência total de programadores – especialistas de negócio podem colaborar;
- Facilita integração com sistemas existentes (conectores prontos ou APIs personalizadas);
- Escalável para ambientes corporativos (arquitetura em nuvem).

### 3.6 Desvantagens
- Limitações de customização total – plataforma pode não permitir alterar componentes de base;
- Lock-in de fornecedor – dependência da plataforma e licenças;
- Exige conhecimento técnico mínimo para integrações com sistemas externos;
- Riscos de segurança: aplicativos podem apresentar vulnerabilidades por implementação inadequada, limitações da plataforma ou ataques à própria plataforma;
- Difícil migração para desenvolvimento tradicional – projeto pode precisar ser refeito do zero;
- Escalabilidade pode ter limites.

## 4. No-Code

### 4.1 Conceito
- Abordagem ainda mais acessível que o low-code.
- Não exige nenhum conhecimento prévio de programação.
- Funciona no sistema de "clique e arraste" (drag-and-drop).
- O usuário deve se adaptar às regras e limitações da plataforma, utilizando módulos pré-construídos.
- Customização mínima – o produto é feito para criação dentro das estruturas definidas pela plataforma.
- Baseado no conceito de desenvolvimento declarativo (o usuário declara o que deseja, e a plataforma gera o código).

### 4.2 Público-alvo
- Usuários de negócio;
- Pessoas sem conhecimento técnico em programação.

### 4.3 Características
- Interface 100% visual;
- Sem necessidade de escrita de código;
- Utilização de módulos e templates prontos;
- Customização limitada às opções oferecidas pela plataforma;
- Blocos de funcionalidades: comandos de lógica, fluxos, integrações e bancos de dados encapsulados em componentes prontos;
- Conectores nativos: integração com planilhas, bancos, APIs REST/SOAP, redes sociais e ferramentas como Google Workspace ou Microsoft 365.

### 4.4 Vantagens do No-Code
- Desenvolvimento extremamente ágil – aplicações criadas em minutos ou poucas horas;
- Zero conhecimento técnico necessário – ideal para usuários que não sabem programar;
- Baixo custo inicial – sem necessidade de contratar desenvolvedores;
- Autonomia do setor de negócio – libera a TI de demandas mais simples;
- Automação de tarefas repetitivas – ideal para processos simples e rotinas administrativas.

### 4.5 Desvantagens do No-Code
- Baixa flexibilidade: aplicações limitadas a blocos disponíveis na plataforma;
- Customização restrita: não permite regras de negócio complexas fora do que é suportado;
- Risco de Shadow IT: soluções paralelas sem validação técnica pela equipe de TI;
- Dependência da plataforma: forte vendor lock-in (dificuldade de migração futura);
- Dificuldade de escalabilidade: não recomendado para sistemas críticos, complexos ou com alto volume de dados;
- Vulnerabilidades da plataforma.

### 4.6 Ferramentas No-Code
- Exemplos: Bubble, Airtable, Glide, Adalo, Zapier (automações), Make (antiga Integromat).

> [!CAUTION] OBSERVAÇÃO:
> - As plataformas no-code NÃO eliminam completamente os riscos relacionados à segurança. Embora utilizem interfaces visuais e intuitivas, ainda estão sujeitas a vulnerabilidades.

## 5. Citizen Developer

### 5.1 Definição Gartner
- Colaborador que cria funcionalidades de aplicativos para uso próprio ou de terceiros.
- Utiliza ferramentas que não são explicitamente proibidas pelas áreas de TI ou pelas unidades de negócio.
- É uma persona (perfil de usuário), não um cargo formal ou função designada.
- Está vinculado a uma unidade de negócio ou área funcional que não pertence ao setor de TI.

> [!TIP] DICAS:
> - Citizen developer é um perfil de usuário, não um cargo formal.
> - Está fora do setor de TI – pertence a áreas de negócio como RH, financeiro ou jurídico.

## 6. Comparativo Detalhado – Low-Code x No-Code

| ASPECTO | LOW-CODE | NO-CODE |
|---------|----------|---------|
| Conhecimento necessário | Básico/intermediário de programação. | Nenhum. |
| Escrita de código | Permite trechos de código. | Não permite. |
| Customização | Alta (dentro dos limites). | Mínima/restrita. |
| Público-alvo | Programadores, analistas técnicos. | Usuários de negócio, citizen developers. |
| Flexibilidade | Média/alta. | Baixa. |
| Velocidade de desenvolvimento | Rápida. | Muito rápida. |
| Ideal para | MVPs, transformação digital, sistemas de média complexidade. | Automação de processos simples, prototipagem rápida. |
| Risco de Shadow IT | Médio. | Alto. |

## 7. Considerações sobre Segurança
- A segurança não depende unicamente da infraestrutura de cloud dos fornecedores.
- Aplicações desenvolvidas com essas plataformas possuem código que é executado pelo computador – a ausência de escrita manual não significa ausência de código.
- A integração com sistemas existentes pode introduzir vulnerabilidades específicas.
- Não há segurança nativa que elimina todos os riscos.

> [!TIP] DICAS:
> - A compatibilidade com diversas plataformas e dispositivos é uma VANTAGEM, não uma limitação, das plataformas low-code e no-code.
> - As abordagens low-code/no-code permitem o lançamento mais rápido de protótipos e MVPs em comparação com o desenvolvimento tradicional.

## 8. Aplicações Adequadas para Low-Code/No-Code

| APLICAÇÕES TÍPICAS | APLICAÇÕES NÃO RECOMENDADAS |
|-------------------|---------------------------|
| Assistentes virtuais e ferramentas de chatbot. | Apps de internet banking (alta segurança, complexidade e personalização). |
| Ferramentas RPA para automação de processos administrativos de back-office. | Cálculo automatizado de sentenças judiciais (sistemas críticos que demandam alto grau de customização e segurança). |
| Aplicativos para divulgação de campanhas de e-mail marketing. | Sistemas de controle de processos judiciais em tempo real com lógicas precisas de automação de decisões. |
| Automação de fluxos de trabalho internos (solicitações de férias, gestão de inventário de TI, coleta de dados por questionários, dashboards para relatórios gerenciais). | Ferramentas para controle automatizado de carro autônomo (alta complexidade). |
| — | Migração de sistemas legados de mainframes para cloud com recursos customizados de controle sobre desempenho e segurança. |

> [!CAUTION] OBSERVAÇÃO:
> - Sistemas hipercríticos (bancários, de segurança, de saúde) ainda exigem programação tradicional, pois necessitam de flexibilidade e controle total.

## 9. Boas Práticas para Low-Code/No-Code

| PRÁTICA | DESCRIÇÃO |
|---------|-----------|
| Governança de TI | Implementar governança que inclua revisões de segurança e conformidade das aplicações desenvolvidas. |
| Controle de versão | Políticas de controle de versão das aplicações desenvolvidas. |
| Avaliação crítica | Avaliar caso a caso se aplicações críticas devem ser desenvolvidas em paralelo com métodos tradicionais – não é uma prática recomendada de forma geral. |

## 10. Tabela Resumo – Low-Code x No-Code

| ASPECTO | LOW-CODE | NO-CODE |
|---------|----------|---------|
| Escrita de código | Mínima (permite personalização). | Nenhuma. |
| Conhecimento técnico | Básico. | Nenhum. |
| Customização | Alta. | Baixa. |
| Flexibilidade | Média. | Baixa. |
| Velocidade | Rápida. | Muito rápida. |
| Público-alvo | Programadores/analistas. | Citizen developers. |
| Risco de Shadow IT | Médio. | Alto. |