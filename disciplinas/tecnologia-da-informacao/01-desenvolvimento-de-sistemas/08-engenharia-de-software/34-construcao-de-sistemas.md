# Engenharia de Software - Construção de Sistemas

## 1. Build e Construção de Sistemas
- A construção de sistemas é o processo de criar um sistema executável completo (build), compilando e ligando componentes, bibliotecas externas, arquivos de configuração e outras informações.
- O processo de building liga os componentes, bibliotecas e arquivos de configuração, e coloca o software em operação, resultando em uma release.
- Ferramentas de construção e de controle de versão devem ser integradas, pois o build utiliza versões específicas dos componentes armazenados no repositório gerenciado pelo sistema de versão.
- O build envolve reunir uma grande quantidade de informações sobre o software e seu ambiente operacional, por isso é recomendado o uso de ferramentas automatizadas.
- Exemplo: o processo de building pega todos os processos e os compila para colocar o software em produção. Ferramentas famosas também precisam passar por testes; caso falhem, o software não pode subir para produção.

> [!CAUTION] OBSERVAÇÃO: 
> - A construção é feita para se chegar à release. O executável final não é necessariamente um arquivo .exe, pois o programa pode rodar por linguagem de script, não sendo mais obrigatório compilar todas as informações em um único arquivo executável.

## 2. Funcionalidades das Ferramentas de Construção
As ferramentas para integração e construção de sistemas podem incluir algumas ou todas as seguintes funcionalidades:

### 2.1 Geração do Script de Construção
- O sistema deve analisar o programa, identificar componentes dependentes e gerar automaticamente um script de construção (arquivo de configuração).
- Também deve permitir a criação manual e a edição desses scripts.

### 2.2 Integração com o Sistema de Controle de Versão
- O sistema deve fazer check-out das versões necessárias dos componentes armazenados no sistema de controle de versão, obtendo o código-fonte para gerar a release.

### 2.3 Recompilação Mínima
- O sistema deve analisar qual código-fonte precisa ser recompilado e realizar apenas as compilações necessárias.

### 2.4 Criação do Sistema Executável
- O sistema deve ligar os arquivos objetos compilados entre si e a outros arquivos (bibliotecas, configurações) para criar um sistema executável.
- O executável é o conjunto de todas as informações necessárias para o software rodar.

### 2.5 Automação dos Testes
- Alguns sistemas de construção podem executar testes automatizados (ex.: JUnit) para verificar se o build não foi quebrado pelas mudanças.

### 2.6 Emissão de Relatórios
- O sistema deve fornecer relatórios sobre o sucesso ou falha da construção e dos testes executados.

### 2.7 Geração da Documentação
- O sistema pode gerar notas de lançamento sobre o build e páginas de ajuda do sistema.

> [!TIP] DICAS: 
> - É possível compilar os três últimos passos (testes, relatórios e documentação) para colocar em produção apenas se o programa passar pelos testes.
> - As funcionalidades 5, 6 e 7 são frequentemente integradas ao pipeline de integração contínua.

## 3. Integração Contínua
- Métodos ágeis recomendam a construção frequente do sistema, com testes automatizados para descobrir problemas rapidamente.
- Construções frequentes são parte do processo de integração contínua.
- A integração contínua envolve a reconstrução frequente da mainline após pequenas mudanças no código-fonte.

### 3.1 Etapas da Integração Contínua
- Extrair o sistema mainline do sistema de gerenciamento de versões para a área de trabalho particular do desenvolvedor.
- Construir o sistema e executar testes automatizados. Se falhar, o build está quebrado; o responsável pelo último check-in deve reparar o problema.
- Fazer as mudanças nos componentes do sistema.
- Construir o sistema na área de trabalho particular e executar novamente os testes. Se falharem, continuar a edição.
- Uma vez aprovado, devolver o sistema ao servidor de construção, mas sem efetivar o commit como novo baseline.
- Construir o sistema no servidor de construção e rodar os testes. Se houver alterações de outros desenvolvedores, puxar as atualizações e ajustar os componentes que falharam.
- Se o sistema passar nos testes, confirmar as alterações como novo baseline no mainline.

### 3.2 Ferramentas de Apoio
- Ferramentas como Jenkins, TravisCI, Hudson e CruiseControl são usadas para apoiar a integração contínua.
- Essas ferramentas podem ser configuradas para construir o sistema assim que o desenvolvedor concluir uma atualização no repositório.
- Jenkins é um servidor de integração contínua open-source (Java), podendo rodar standalone ou como aplicação web. Vantagens: builds periódicos, testes automatizados, análise de código, identificação precoce de erros, fácil configuração, comunidade ativa e integração com outras ferramentas via plugins.

### 3.3 Vantagens da Integração Contínua
- Permite a descoberta e o conserto rápidos de problemas causados por interações entre diferentes desenvolvedores.
- O sistema mais recente no mainline é sempre o sistema funcional definitivo, mantendo uma baseline sempre rodando.

> [!CAUTION] OBSERVAÇÃO: 
> - Na prática, a integração contínua pura nem sempre é aplicável como na teoria.

## 4. Desafios da Integração Contínua
A integração contínua nem sempre é possível. Os principais desafios são:

### 4.1 Sistema Muito Grande
- Pode levar muito tempo para construir e testar o sistema, especialmente se houver integração com outros sistemas.
- Construções várias vezes ao dia tornam-se impraticáveis.

### 4.2 Plataformas Diferentes (Desenvolvimento vs. Destino)
- Pode não ser possível executar os testes na área de trabalho particular do desenvolvedor devido a diferenças de hardware, sistema operacional ou software instalado.
- O conceito de containers surgiu para facilitar e reduzir esse problema.
- Nesses casos, a integração contínua costuma ser impossível, sendo necessário realizar adaptações no final do ciclo.

### 4.3 Alternativa: Construção Diária
- Quando a integração contínua não é viável, utiliza-se um sistema de construção diária:
  1. A organização define um horário de entrega (ex.: 14h) para novos componentes. Os desenvolvedores entregam suas versões até esse horário, mesmo que incompletas, desde que proporcionem funcionalidade básica testável.
  2. Uma nova versão do sistema é construída com base nesses componentes.
  3. O sistema é entregue à equipe de testes, que executa um conjunto predefinido de testes.
  4. Defeitos descobertos são documentados e devolvidos aos desenvolvedores para correção em versões subsequentes.

> [!TIP] DICAS: 
> - Na prática, trabalha-se com janelas de decoy devido à múltipla colaboração, o que inviabiliza a integração contínua em muitos cenários.

## 5. Releases
- Os lançamentos (releases) do sistema incluem código executável, arquivos de dados, arquivos de configuração e documentação.
- O gerenciamento de lançamento envolve decisões sobre datas, preparação das informações para distribuição e documentação de cada release.
- Existem dois tipos principais:
  - Lançamentos principais (major releases): oferecem nova funcionalidade significativa.
  - Lançamentos secundários (minor releases): consertam defeitos e solucionam problemas relatados por clientes.
- Exemplo: macOS 10.9.2 – onde 10 é o sistema, 9 é o lançamento principal e 2 é o lançamento secundário.
- O gerenciamento de release é acompanhado por esses números de versão.

> [!CAUTION] OBSERVAÇÃO: 
> - O processo de release está relacionado a testes alfa e beta, e a numeração ajuda a rastrear a evolução do software.