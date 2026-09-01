# Engenharia de Software - Sistema de Controle de Versão

## 1. Conceitos Fundamentais
- Os sistemas de controle de versão identificam, armazenam e controlam o acesso às diferentes versões dos componentes de software.
- O VCS existe para que as pessoas possam trabalhar sem problemas de perder a versão.

### 1.1 Tipos de Sistemas de Controle de Versão Modernos

#### 1.1.1 Sistemas Centralizados
- Um único repositório mestre mantém todas as versões dos componentes.
- Exemplo amplamente utilizado: Subversion (SVN).

#### 1.1.2 Sistemas Distribuídos
- Existem várias versões do repositório de componentes ao mesmo tempo.
- Exemplo amplamente utilizado: Git.

> [!TIP] DICAS: 
> - O SVN (centralizado) e o Git (distribuído) são os sistemas mais cobrados em concursos.
> - Decore as operações básicas de cada um: checkout (SVN) e clone (Git) para obter cópias; commit e push (Git) para enviar alterações.

> [!CAUTION] OBSERVAÇÃO: 
> - Ambos os sistemas fornecem funcionalidades comparáveis, mas as implementam de maneiras diferentes.

## 2. Características Principais dos VCS

### 2.1 Identificação de Versão e Lançamento
- As versões gerenciadas recebem identificadores únicos quando são submetidas ao sistema.
- Os identificadores permitem gerenciar diferentes versões sem alterar o nome do componente.
- As versões podem receber atributos que ajudam a identificar cada versão de maneira única.

### 2.2 Registro do Histórico de Mudanças
- O sistema mantém registros das mudanças feitas para criar versões novas a partir de versões anteriores.
- Em alguns sistemas, as mudanças podem ser usadas para selecionar uma determinada versão.
- Envolve marcar os componentes com palavras-chave que descrevem as mudanças.
- As palavras-chave podem ser usadas para selecionar componentes a serem incluídos em uma baseline.

### 2.3 Desenvolvimento Independente
- Diferentes desenvolvedores podem trabalhar simultaneamente no mesmo componente.
- O VCS controla os componentes em que se fez check-out para edição.
- Assegura que as mudanças feitas por diferentes desenvolvedores não interfiram umas nas outras.

### 2.4 Apoio de Projeto
- Permite o desenvolvimento de vários projetos que compartilham componentes.
- É possível fazer check-in e check-out de todos os arquivos associados a um projeto de uma só vez.

### 2.5 Gerenciamento de Armazenamento
- Em vez de manter cópias separadas de todas as versões, o sistema usa mecanismos eficientes.
- Não mantém cópias duplicadas de arquivos idênticos.
- Quando há apenas pequenas diferenças entre os arquivos, o sistema pode armazenar essas diferenças (deltas).
- Uma versão específica pode ser recriada automaticamente aplicando as diferenças a uma versão mestre.

> [!CAUTION] OBSERVAÇÃO: 
> - O código-fonte é basicamente texto, portanto não ocupa tanto espaço de armazenamento.

## 3. Funcionamento do Check-In e Check-Out em Repositório Centralizado

### 3.1 Conceitos Básicos
- O repositório do projeto mantém a versão "mestre" de todos os componentes.
- A versão mestre é utilizada para criar as baselines para a construção do sistema.
- Área de trabalho particular: onde os desenvolvedores trabalham nas cópias dos componentes.

### 3.2 Fluxo de Trabalho
- Ao modificar componentes, os desenvolvedores copiam (fazem check-out) os componentes do repositório para sua área de trabalho.
- Trabalham nessas cópias localmente.
- Após concluírem as alterações, os componentes modificados são devolvidos (faz-se check-in) para o repositório.

> [!CAUTION] OBSERVAÇÃO: 
> - É importante evitar situações em que as mudanças interfiram umas nas outras, ou seja, evitar que as mudanças feitas por um desenvolvedor sobrescrevam as de outro.

## 4. Clonagem do Repositório no Modelo Distribuído

### 4.1 Conceito de Clone
- Um repositório "mestre" é criado em um servidor, mantendo o código produzido pela equipe.
- Em vez de fazer check-out, o desenvolvedor cria um clone do repositório do projeto.
- O clone é baixado e instalado no computador do desenvolvedor.
- Os desenvolvedores trabalham nos arquivos necessários e mantêm as novas versões em seu repositório particular.

### 4.2 Fluxo de Trabalho no Git
- Os desenvolvedores fazem commit das alterações para atualizar seu repositório privado.
- Depois, podem enviar (push) as alterações para o repositório do projeto.
- Ou podem informar ao gerente de integração que as versões modificadas estão disponíveis.
- O gerente pode então puxar (pull) esses arquivos para o repositório do projeto.

> [!CAUTION] OBSERVAÇÃO: 
> - Normalmente, quando se tem uma cópia do repositório na máquina, e alguém faz um push no repositório mestre, é necessário fazer um pull para que seu próprio repositório local seja atualizado. Se não souber como fazer isso, forçar pode gerar problemas.

## 5. Vantagens do Modelo Distribuído

### 5.1 Mecanismo de Backup
- Se o repositório estiver corrompido, o trabalho pode continuar.
- O repositório do projeto pode ser restaurado a partir de cópias locais.

### 5.2 Trabalho Off-Line
- Permite que os desenvolvedores façam commit das alterações mesmo sem conexão de rede.

### 5.3 Apoio ao Projeto Padronizado
- Os desenvolvedores podem compilar e testar todo o sistema em suas máquinas locais.
- Permite testar as alterações antes de enviá-las ao repositório central.

## 6. Ramificação (Branch) e Fusão (Merge)

### 6.1 Conceito de Ramificação
- Uma consequência do desenvolvimento independente é que os codelines podem se ramificar.
- Em vez de uma sequência linear de versões, podem existir várias sequências independentes.
- Isso é normal no desenvolvimento, pois diferentes desenvolvedores trabalham em versões diferentes do código-fonte.

### 6.2 Recomendações sobre Branches
- É recomendável que uma nova ramificação (branch) seja criada para que as alterações não afetem acidentalmente um sistema que está funcionando.

### 6.3 Conceito de Fusão
- Em algum momento, pode ser necessário fundir (merge) ramificações de código.
- O merge cria uma versão nova do componente que inclui todas as alterações feitas.
- Exemplo: versões 2.1.2 e 2.3 são fundidas para criar a versão 2.4.

> [!CAUTION] OBSERVAÇÃO: 
> - O problema é fazer diversos branches e impedir o acesso a determinadas versões do programa.

## 7. Gerenciamento de Armazenamento Usando Deltas

### 7.1 Conceito de Delta
- Quando uma nova versão é criada, o sistema armazena um delta: uma lista de diferenças entre a nova versão e a versão mais antiga usada para criá-la.
- Os deltas geralmente são armazenados como listas de linhas alteradas.
- Aplicando os deltas automaticamente, uma versão pode ser criada a partir de outra.

### 7.2 Armazenamento da Versão Mais Recente
- Como a versão mais recente provavelmente será a mais utilizada, a maioria dos sistemas a armazena na íntegra.
- Os deltas definem como recriar versões anteriores do sistema.

> [!CAUTION] OBSERVAÇÃO: 
> - Um dos problemas com a abordagem de deltas é que pode levar muito tempo para aplicar todos os deltas. Se após fazer muitos deltas for preciso voltar a uma versão mais antiga, seria necessário desfazer tudo.

## 8. Abordagem do Git para Armazenamento

### 8.1 Compressão Padrão
- Como o armazenamento em disco é relativamente barato, o Git usa uma abordagem alternativa mais rápida.
- O Git não usa deltas, mas aplica um algoritmo de compressão padrão nos arquivos armazenados e em sua metainformação associada.
- A abordagem não armazena cópias duplicadas de arquivos.
- A recuperação de um arquivo envolve apenas sua descompactação, sem necessidade de aplicar uma cadeia de operações.

### 8.2 Packfiles
- O Git usa a noção de packfiles, em que vários arquivos menores são combinados em um único arquivo indexado.
- Isso reduz a sobrecarga associada a vários arquivos pequenos.
- Os deltas são usados dentro de packfiles para reduzir ainda mais o seu tamanho.

## 9. Comandos SVN
| COMANDO | DESCRIÇÃO |
|---|---|
| Add | Programar um novo arquivo ou diretório para inclusão no repositório |
| Checkout (co) | Criar uma cópia de trabalho local de um repositório remoto |
| Commit (ci) | Enviar (check in) as alterações locais para o repositório |
| Copy (cp) | Copiar um ou mais arquivos em uma cópia de trabalho ou no repositório |
| Delete (del, remove, rm) | Itens especificados são programados para exclusão no próximo commit |
| Diff (di) | Exibir diferenças em arquivos do diretório |
| Help (?, h) | Ajuda do Subversion e ajuda sobre subcomandos |
| Move (mv, rename, ren) | Mover arquivos ou diretórios na cópia de trabalho ou no repositório |
| Resolve | Resolver conflitos em arquivos ou diretórios da cópia de trabalho |
| Revert | Desfazer todas as edições locais ou opcionalmente de um arquivo/diretório |
| Status | Exibir o status dos arquivos e diretórios da cópia de trabalho |
| Update | Trazer mudanças do repositório para a cópia de trabalho |