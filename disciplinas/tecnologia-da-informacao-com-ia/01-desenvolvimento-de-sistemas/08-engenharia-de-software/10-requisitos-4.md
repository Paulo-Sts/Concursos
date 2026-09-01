# Engenharia de Software - Requisitos 4

## Técnicas de Levantamento de Requisitos
- Existem técnicas para levantar requisitos (descoberta) e para validar requisitos.
- A prototipação pode ser usada tanto para levantar quanto para validar requisitos na espiral.

## 1. Descoberta de Requisitos
- Processo de coleta de informações sobre sistemas necessários e existentes.
- Separa os requisitos do usuário e sistema a partir dessas informações.
- A interação ocorre com os stakeholders do sistema (gerentes, reguladores externos, etc.).
- Normalmente, os sistemas possuem vários stakeholders.

### 1.1 Entrevistas
- Entrevistas formais ou informais com stakeholders.
- São parte da maioria dos processos de engenharia de requisitos.

> [!TIP] DICAS:
> - Stakeholders = partes interessadas no sistema.

### 1.2 Cenários
- As pessoas se relacionam melhor com exemplos da vida real do que com descrições abstratas.
- Técnicas de levantamento de requisitos, estudos de UX, IHC e UI tornaram os cenários extremamente evoluídos.

### 1.3 Casos de Uso
- Em sua forma mais simples, identifica os atores envolvidos em uma interação e dá nome ao tipo de interação.
- Exemplo: cadastrar aluno.

### 1.4 Etnografia
- Método de pesquisa acadêmica baseado em observação (sem interação).
- O analista faz imersão no ambiente de trabalho onde o sistema será usado.
- Observa o trabalho do dia a dia e anota as tarefas reais dos participantes.
- Ajuda a descobrir requisitos implícitos que refletem formas reais de trabalho, não processos formais definidos pela organização.

> [!CAUTION] OBSERVAÇÃO:
> - O sistema é o meio termo: não pode ser o processo formal não utilizado, nem uma bagunça sistematizada pelo usuário.

### 1.5 Prototipação
- Usada para levantar e validar requisitos.
- Requisitos são apresentados em um protótipo de interface para validação.
- O protótipo deve ser simples.
- Após a validação, um documento de requisitos deve ser criado para documentar o levantado.

### 1.6 JAD (Joint Application Development)
- Metodologia criada pela IBM.
- Usuários e analistas projetam o sistema juntos em sessões de grupo estruturadas, guiados por um líder de reunião.
- Utiliza criatividade e trabalho em equipe para definir o ponto de vista dos usuários sobre o sistema.
- Princípios básicos (exceto técnicas virtuais):
  - Dinâmica de grupo.
  - Uso de técnicas visuais.
  - Utilização de documentação padrão.
  - Manutenção do processo organizado e racional.

> [!CAUTION] OBSERVAÇÃO:
> - A técnica JAD não faz uso de técnicas virtuais, pois as sessões são guiadas e formadas pelo agrupamento de pessoas (joint = articulado; junto).

## 2. Mesclagem de Técnicas

### 2.1 Etnografia e Prototipação
- Faz-se análise etnográfica, reuniões de prestação de contas e etnografia focada.
- Gera-se prototipação do sistema e avaliação do protótipo.
- A prototipação pode ser feita pelo desenvolvimento de sistema genérico.
- A prototipação pode dar feedback nas reuniões de prestação de contas para melhorar a etnografia focada.

### 2.2 QFD (Quality Function Deployment)
- Usa observação, entrevistas com clientes, pesquisas e exame de dados históricos (relatórios de problemas) como dados brutos.
- Os dados são traduzidos em uma tabela de requisitos (tabela da voz do cliente) e revisados com o cliente.
- Enfatiza o entendimento do que é valioso para o cliente e emprega esses valores ao longo do processo de engenharia.
- Classifica os requisitos em três categorias.

#### 2.2.1 Requisitos Normais
- Refletem objetivos e metas estabelecidos durante reuniões com o cliente.
- Se presentes, o cliente fica satisfeito.
- Exemplos: tipos de displays gráficos, funções específicas, níveis de desempenho definidos.

#### 2.2.2 Requisitos Esperados
- Implícitos no produto ou sistema; tão fundamentais que o cliente não os declara explicitamente.
- A ausência causa grande insatisfação.
- Exemplos: facilidade na interação homem-máquina, confiabilidade, correção operacional global, facilidade na instalação do software.

> [!CAUTION] OBSERVAÇÃO:
> - O requisito esperado é, normalmente, um requisito não funcional, pois ninguém dirá explicitamente que deseja confiabilidade ou perfeita funcionalidade — são naturalmente esperados.

#### 2.2.3 Requisitos Fascinantes
- Vão além da expectativa dos clientes.
- São muito satisfatórios quando presentes.
- Exemplo: software de celular com recursos-padrão e capacidades não esperadas (tecla multitoque, correio de voz visual) que encantam os usuários.

### Tabela de Classificação QFD
| TIPO DE REQUISITO | CARACTERÍSTICA | EXEMPLO |
|---|---|---|
| Normais | Objetivos estabelecidos em reuniões; satisfazem quando presentes | Tipos de displays gráficos; funções específicas; níveis de desempenho |
| Esperados | Implícitos; fundamentais; não declarados; ausência causa insatisfação | Facilidade de interação; confiabilidade; correção operacional; fácil instalação |
| Fascinantes | Vão além da expectativa; muito satisfatórios quando presentes | Recursos inovadores não esperados (multitoque, correio de voz visual) |