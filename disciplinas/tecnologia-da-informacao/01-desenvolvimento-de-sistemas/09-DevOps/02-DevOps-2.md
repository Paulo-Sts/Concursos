# DevOps 2

## 1. Princípios e Pilares do DevOps
- O DevOps baseia-se em fundamentos específicos para que a cultura se desenvolva em pilares que trazem a sustentação necessária.
- Princípios fundamentais incluem a colaboração entre equipes, automação de processos produtivos e implementação contínua.
- As ações são voltadas ao cliente com foco em gerar valor e criar soluções com o final em mente de forma prospectiva.
- Diferenciação conceitual:
  - Princípios são fundamentos para evolução;
  - Pilares são elementos de sustentação da continuidade.

### 1.1 Detalhamento dos Pilares
- Comunicação osmótica e constante para tornar o fluxo de informações fluido entre as equipes.
- Colaboração obrigatória entre times de diferentes departamentos.
- Utilização de ferramentas de automação para evitar processos manuais improdutivos.
- Monitoramento e testes antecipados ao máximo possível para garantir a qualidade operacional.

## 2. Práticas de Desenvolvimento e Infraestrutura
- Integração contínua (CI) consiste na construção e teste automático de cada parte do código entregue.
- Entrega contínua (CD) foca na execução de novas checagens e disponibilização frequente do software para os clientes.
- Microsserviços utilizam pequenas funcionalidades independentes que se comunicam via interface REST para agilizar entregas.
- Infraestrutura como código (IaC) gerencia recursos por meio de arquivos de configuração e scripts em vez de acessos manuais.
- Vantagens da IaC:
  - Padronização da configuração do computador;
  - Aumento da agilidade e automação;
  - Reuso de configurações já existentes.

### 2.1 Monitoramento e Qualidade
- O monitoramento de logs auxilia na identificação precoce de problemas através de ferramentas automatizadas.
- Os eventos registrados em logs permitem identificar comportamentos que indicam falhas iminentes em servidores.
- Shift-left testing é a abordagem que antecipa a realização de testes para o início do ciclo de vida.
- O princípio de validar a qualidade antecipa a análise de características funcionais e não funcionais.

## 3. Ciclo de Vida do DevOps
- O ciclo de vida é composto por oito processos repetitivos organizados em um fluxo contínuo.
- Fases do ciclo:
  - Planejar (plan) envolvendo requisitos e regras de negócio;
  - Codificar (code) com foco em escrita de código e controle de versão;
  - Compilar (build) para validação estática e preparação de pacotes;
  - Testar (test) para mitigar falhas e garantir confiabilidade;
  - Lançar (release) como etapa de pré-implantação e ajuste;
  - Liberar (deploy) para a entrada da nova versão em produção;
  - Operar (operate) para manter o software disponível;
  - Monitorar (monitor) para verificar o estado da infraestrutura.

### Tabela de Ferramentas e Conceitos

| FERRAMENTA OU CONCEITO | FINALIDADE PRINCIPAL | EXEMPLO DE APLICAÇÃO |
|---|---|---|
| DOCKER | Programação de instâncias | Ambientes de contêineres |
| GITLAB OU OPENSHIFT | Controle de publicação | Publicação da solução na produção |
| CI/CD | Método de entrega | Integração e implantação contínuas |
| MIDDLEWARE | Interconexão de aplicações | Software para conectar sistemas diferentes |

> [!TIP] DICAS: 
> - O termo Shift-left é uma gíria técnica que significa realize isso antes para otimizar processos.
> - A estruturação baseada em contêineres Docker é um dos tópicos mais frequentes em avaliações de tecnologia.

> [!CAUTION] OBSERVAÇÃO: 
> - O ciclo de vida do DevOps não deve ser confundido com o ciclo de CI/CD que atua em uma camada de integração inferior.
> - O TDD é classificado como uma prática de desenvolvimento e não meramente uma prática de teste.