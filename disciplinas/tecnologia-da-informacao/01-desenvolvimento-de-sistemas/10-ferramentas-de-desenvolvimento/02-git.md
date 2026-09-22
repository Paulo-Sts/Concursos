# Ferramenta de Versionamento Git

## 1. Conceito e Funcionamento do Git
- Ferramenta de controle de versões utilizada para identificar, armazenar e gerenciar diferentes versões de arquivos de forma descentralizada.
- Permite a colaboração eficiente entre desenvolvedores em múltiplos repositórios distribuídos, independentemente da localização geográfica.
- O Git não gera cópias completas de cada versão, mas armazena as diferenças entre elas (deltas), o que garante economia de espaço e eficiência.
- Utiliza conceitos fundamentais como baseline e branch para o gerenciamento das versões do projeto.

### 1.1 Sistemas Centralizados versus Descentralizados
- Sistemas centralizados, como Subversion (SVN) e SourceSafe, operam com um único repositório central onde todos os desenvolvedores trabalham.
- Sistemas descentralizados ou distribuídos, como o Git, permitem que cada desenvolvedor possua uma cópia local completa do repositório.
- Essa arquitetura possibilita o trabalho independente e autônomo, sem a necessidade de conexão constante com um servidor central.

| SISTEMA | ARQUITETURA | EXEMPLOS |
|---|---|---|
| Centralizado | Repositório único central | SVN, SourceSafe, ClearCase, CVS |
| Descentralizado | Repositório local completo | Git |

## 2. Diferença entre Git e GitLab
- O Git é estritamente a ferramenta de versionamento e controle de código.
- O GitLab é uma suíte completa de ferramentas para desenvolvimento colaborativo que utiliza o Git.
- O GitLab oferece funcionalidades adicionais importantes, como a automação de pipelines e a implementação de integração contínua (CI/CD).

## 3. Comandos Básicos e Aplicações
- git clone ⟶ realiza a cópia completa de um repositório remoto para o ambiente local do desenvolvedor;
- git add ⟶ adiciona arquivos modificados ao índice de preparação (staging area); o comando git add . adiciona todas as mudanças de uma vez;
- git commit ⟶ registra e efetiva as alterações no repositório local, geralmente acompanhado de uma mensagem explicativa (-m);
- git push ⟶ envia as alterações registradas no repositório local para o repositório remoto;
- git pull ⟶ atualiza o repositório local com as mudanças mais recentes vindas do repositório remoto.

## 4. Gerenciamento de Ramificações e Fusões
- Branch ⟶ ramificação ou desdobramento do projeto que permite modificar o código sem afetar a versão principal.
- Merge ⟶ comando que realiza a fusão ou integração de diferentes versões ou ramos de código.
- git rebase ⟶ comando avançado utilizado para reorganizar commits, exigindo cautela na sua execução.

## 5. Gestão de Configuração e Qualidade
- O Git é uma ferramenta essencial na gestão de configuração de software, abrangendo o controle, a automação e o versionamento.
- O controle de versões é um dos pilares para a manutenção da integridade e eficiência do produto final.
- A prática do versionamento está diretamente ligada à garantia de qualidade de software (GQE).

> [!TIP] DICAS: 
> - Pratique os comandos em ambiente local através do terminal de linha de comando para consolidar o aprendizado prático exigido em provas.
> - Sempre realize um commit das suas alterações locais antes de executar o comando git pull para evitar conflitos desnecessários.

> [!CAUTION] OBSERVAÇÃO: 
> - A terminologia branch é frequentemente associada a metáforas de árvores, com raízes (root) e ramos.
> - Fique atento à sigla GQE em provas, que significa Garantia de Qualidade de Software (Software Quality Assurance - SQA em inglês).
> - O Git pode ser utilizado para versionar não apenas código-fonte, mas também documentos e arquivos de configuração.