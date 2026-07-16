# Anotações

# NIST Cybersecurity Framework (CSF) 2.0

## 1.1 Conceito Geral do CSF

- O **NIST Cybersecurity Framework (CSF) 2.0** fornece orientações para gerenciar riscos de cibersegurança.
- É aplicável a **organizações de qualquer tamanho ou setor** – não se restringe a empresas de determinado porte ou segmento específico.
- O CSF auxilia as organizações a: **entender**, **avaliar**, **priorizar** e **comunicar** seus esforços de cibersegurança.

> ### 1.1.1 Atenção para Concursos
> **Atenção/Exceção:** As bancas podem elaborar questões restringindo a aplicabilidade do CSF a apenas algumas organizações de determinado tamanho ou setor específico.
> **O CSF é aplicável a organizações de qualquer tamanho ou setor!**

## 1.2 Componentes do CSF

O CSF é composto por três elementos principais:

| COMPONENTE | DESCRIÇÃO |
|------------|-----------|
| **CSF Core** (Núcleo) | Taxonomia de resultados de cibersegurança de alto nível |
| **CSF Profiles** (Perfis) | Mecanismos para descrever a postura de cibersegurança **atual** e **desejada** |
| **CSF Tiers** (Níveis) | Caracterizam o rigor das práticas de governança e gestão de risco de cibersegurança |

## 1.3 Funções do CSF Core

São **6 funções** do núcleo (*Core*), que se subdividem em categorias e subcategorias:

| FUNÇÃO | PORTUGUÊS | INGLÊS | DESCRIÇÃO SINTÉTICA |
|--------|-----------|--------|---------------------|
| **1** | Governar | ***Govern*** | Estratégia, políticas e gestão de risco |
| **2** | Identificar | ***Identify*** | Entendimento dos riscos e ativos atuais |
| **3** | Proteger | ***Protect*** | Salvaguardas para gerenciar riscos |
| **4** | Detectar | ***Detect*** | Identificação e análise de ataques |
| **5** | Responder | ***Respond*** | Ações em resposta a incidentes |
| **6** | Recuperar | ***Recover*** | Restauração de ativos e operações |

> [!TIP] DICAS
> - É importante saber os nomes das funções tanto em **português** quanto em **inglês**, pois as bancas podem fazer referência em ambos os idiomas.
> - Ordem das funções: **G**overnar → **I**dentificar → **P**roteger → **D**etectar → **R**esponder → **R**ecuperar (G-I-P-D-R-R)

## 1.4 Detalhamento das Funções

### 1.4.1 Governar (GV / ***Govern***)

- Estratégia, expectativas e políticas de gestão de risco de cibersegurança são **estabelecidas, comunicadas e monitoradas**.
- É uma função de **alto nível hierárquico** – a alta direção é responsável por essa função.
- **Subcategorias:**
  - Compreensão do contexto organizacional;
  - Estabelecimento de estratégia de segurança cibernética e gestão de risco da cadeia de suprimentos;
  - Funções, responsabilidades e autoridades;
  - Política;
  - Supervisão estratégica de cibersegurança.

> ### 1.4.2 Governar - Responsabilidade da Alta Direção
> **Atenção/Exceção:** A função **Governar** é de responsabilidade da **alta direção**, por envolver estratégia, políticas e supervisão estratégica de cibersegurança.

### 1.4.3 Identificar (ID / ***Identify***)

- Compreensão dos **riscos atuais** de cibersegurança.
- Está intrinsecamente ligada ao **conhecimento dos ativos organizacionais** (tudo o que apresenta valor para a organização).
- **Subcategorias:**
  - Compreensão dos ativos da organização: dados, hardware, software, sistemas, instalações, serviços, pessoas, fornecedores e riscos relacionados;
  - Priorização dos esforços consistentes com a estratégia de gestão de risco e necessidades da missão identificadas em **Governar**.

### 1.4.4 Proteger (PR / ***Protect***)

- **Salvaguardas** para gerenciar os riscos.
- Uma vez identificados e priorizados os ativos e riscos, esta função apoia a capacidade de proteger esses ativos para **prevenir ou reduzir** a probabilidade e o impacto de eventos adversos de cibersegurança.
- **Subcategorias:**
  - Gestão de identidade, autenticação e controle de acesso;
  - Conscientização e treinamento;
  - Segurança de dados;
  - Segurança da plataforma;
  - Resiliência da infraestrutura tecnológica.

> [!CAUTION] OBSERVAÇÃO
> **A gestão de identidade, autenticação, controle de acesso, segurança de dados e resiliência da infraestrutura tecnológica** são resultados abrangidos pela função **PROTEGER (PR)**, e NÃO pela função IDENTIFICAR (ID).

### 1.4.5 Detectar (DE / ***Detect***)

- **Identificação e análise** de ataques e compromissos de cibersegurança.
- Permite a descoberta e análise oportuna de:
  - **Anomalias** (ex.: acesso ao sistema fora do expediente);
  - **Indicadores de comprometimento**;
  - Outros eventos potencialmente adversos que podem indicar que ataques e incidentes estão ocorrendo.

### 1.4.6 Responder (RS / ***Respond***)

- **Ações tomadas em resposta** a incidentes de cibersegurança detectados na função anterior.
- Apoia a capacidade de **conter os efeitos** de incidentes de cibersegurança.

### 1.4.7 Recuperar (RC / ***Recover***)

- **Restauração de ativos e operações** afetados por incidentes de cibersegurança.

> [!TIP] DICAS
> - A função que trata da **restauração** é **Recuperar** (RC / *Recover*).
> - A função que trata da **resposta** a incidentes é **Responder** (RS / *Respond*).
> - **Não confundir:** Responder (ações durante o incidente) x Recuperar (restauração após o incidente).

## 1.5 Tabela Resumo das Funções

| FUNÇÃO (PT) | FUNÇÃO (EN) | PALAVRA-CHAVE | O QUE FAZ? |
|-------------|-------------|---------------|------------|
| Governar | ***Govern*** | Estratégia | Estabelece políticas e supervisiona |
| Identificar | ***Identify*** | Ativos/riscos | Compreende riscos e ativos atuais |
| Proteger | ***Protect*** | Salvaguardas | Protege ativos e mantém resiliência |
| Detectar | ***Detect*** | Anomalias | Encontra e analisa ataques |
| Responder | ***Respond*** | Contenção | Toma ações durante incidentes |
| Recuperar | ***Recover*** | Restauração | Restaura operações após incidentes |

---

# Questões de Fixação

## Questão 01
Qual das seguintes funções do CSF trata da restauração de operações após um incidente?

a) Governar.
b) Proteger.
c) Recuperar.
d) Responder.
e) Identificar.

**Gabarito:** c

## Questão 02
(CNJ/CESPE/CEBRASPE/TÉCNICO JUDICIÁRIO/ÁREA APOIO ESPECIALIZADO/PROGRAMAÇÃO DE SISTEMAS/2024)

Conforme a versão mais recente do NIST Cybersecurity Framework, a função core IDENTIFY (ID) abrange resultados como gestão de identidade, autenticação, controle de acesso, segurança de dados e resiliência da infraestrutura tecnológica.

**Gabarito:** E (Errado) - Estes resultados são abrangidos pela função **PROTECT (PR)**, não pela função IDENTIFY (ID).

---

# Gabarito Oficial

| QUESTÃO | GABARITO |
|---------|----------|
| 01 | c |
| 02 | E |

---

*Este material foi elaborado pela equipe pedagógica do Gran Concursos, de acordo com a aula preparada e ministrada pelo professor Josis Alves.*