# Engenharia de Software - Gerenciamento de Configuração

## 1. Visão Geral
- O gerenciamento de configuração é uma disciplina essencial tanto para projetos individuais, para evitar o esquecimento de alterações, quanto para projetos em equipe.
- Em equipes, especialmente as distribuídas, vários desenvolvedores trabalham simultaneamente no mesmo sistema, tornando o gerenciamento de configuração indispensável.
- O sistema de gerenciamento de configuração fornece acesso ao sistema em desenvolvimento e gerencia as alterações feitas no código por todos os membros da equipe.

### 1.1 Atividades
- O gerenciamento de configuração é composto por quatro atividades principais:

#### 1.1.1 Controle de Versão
- Mantém o controle das várias versões dos componentes do sistema.
- Garante que as mudanças feitas por diferentes desenvolvedores não interfiram umas com as outras.

#### 1.1.2 Construção de Sistema
- Processo de reunir componentes, dados e bibliotecas do programa.
- Envolve compilar e ligar esses elementos para criar um sistema executável.

#### 1.1.3 Gerenciamento de Mudanças
- Mantém o controle das solicitações de mudança de clientes e desenvolvedores no software já entregue.
- Elabora os custos e o impacto de fazer essas mudanças.
- Decide se e quando as alterações devem ser implementadas.

#### 1.1.4 Gerenciamento de Lançamentos (Releases)
- Envolve a preparação do software para lançamento externo.
- Acompanha as versões do sistema que foram lançadas para uso do cliente.

## 2. Desenvolvimento Ágil
- O desenvolvimento ágil, com mudanças múltiplas ao dia, é impossível sem ferramentas de gerenciamento de configuração.
- As versões definitivas dos componentes são mantidas em um repositório compartilhado.
- Os desenvolvedores copiam esses componentes para suas áreas de trabalho particulares para modificá-los.

## 3. Terminologia
| TERMO | EXPLICAÇÃO |
|---|---|
| Área de trabalho | Uma área particular onde o software pode ser modificado sem afetar outros desenvolvedores. |
| Baseline | Uma coleção controlada de versões de componentes que compõem um sistema. As versões não podem ser alteradas, e a baseline sempre pode ser recriada. |
| Codeline | Um conjunto de versões de um componente de software e outros itens de configuração dos quais ele depende. |
| Construção de sistema | Criação de uma versão executável do sistema por meio de compilação e ligação das versões corretas dos componentes e bibliotecas. |
| Controle de configuração (versão) | Processo de registrar e manter versões de sistemas e componentes, gerenciando mudanças e identificando/armazenando todas as versões ao longo da vida útil. |
| Fusão (merging) | Criação de uma nova versão de um componente a partir da fusão de versões separadas em diferentes codelines. |
| Item de configuração (ICS) | Qualquer item associado a um projeto de software (projeto, código, dados de teste, etc.) submetido ao controle de configuração, com identificador único. |
| Lançamento | Uma versão de um sistema liberada para uso dos clientes ou outros usuários. |
| Mainline | Uma sequência de baselines que representam diferentes versões de um sistema. |
| Ramificação (branching) | Criação de uma nova codeline a partir de uma versão de uma codeline existente, permitindo desenvolvimento independente. |
| Repositório | Banco de dados compartilhado com versões de componentes e metainformações sobre mudanças. |
| Versão | Uma instância de um item de configuração que difere de outras, com um identificador único. |

> [!TIP] DICAS:
> - Os itens de configuração sempre devem ter um identificador único e são essenciais para rastrear qualquer artefato do projeto.
> - O "Controle de Configuração" é frequentemente usado como sinônimo de "Controle de Versão" em alguns contextos de prova.

## 4. Codelines e Baselines
- Uma codeline é uma sequência de versões do código-fonte, onde versões posteriores derivam de anteriores.
- As codelines normalmente se aplicam a componentes individuais do sistema.
- Uma baseline é uma definição de um sistema específico, especificando as versões dos componentes, bibliotecas, arquivos de configuração e outras informações.
- A mainline é uma sequência de versões do sistema desenvolvida a partir de uma baseline original.

### 4.1 Importância das Baselines
- As baselines são cruciais porque permitem recriar uma versão específica de um sistema.
- Exemplo: Uma linha de produtos pode ser instanciada para criar versões específicas para cada cliente.
- Exemplo: É preciso recriar a versão entregue a um cliente para corrigir defeitos relatados.

### 4.2 Estratégia Comum de Versionamento
- É comum a criação de uma baseline "develop" e uma baseline "master".
- O trabalho de desenvolvimento é realizado na baseline "develop".
- Em determinado momento, os componentes estáveis são passados para a baseline "master".

> [!CAUTION] OBSERVAÇÃO:
> - Muitos desenvolvedores têm problemas para voltar a versões anteriores do software por não saberem usar corretamente os conceitos de codelines e baselines. Isso é um erro comum na prática e pode ser cobrado em provas.