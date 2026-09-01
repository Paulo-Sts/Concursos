# Interoperabilidade de Sistemas: SOA e Web Services

## 1. Interoperabilidade de Sistemas
- Capacidade de diferentes sistemas, organizações ou dispositivos se comunicarem e trocarem informações de forma eficiente e padronizada.
- Consiste na possibilidade de ocorrer a comunicação entre serviços sem a necessidade de unificar todas as bases de dados e estruturas.
- Utiliza o middleware como uma aplicação específica para realizar a intercomunicação entre esses sistemas diversos.
- Evolução das antigas bibliotecas de consumo para o uso atual de barramentos com entradas de solicitações baseadas no serviço desejado.

## 2. Arquitetura Orientada a Serviços
- Conhecida pela sigla SOA (Service Oriented Architecture), consiste em uma arquitetura que disponibiliza estrutura computacional para conexão de entidades, softwares e pessoas.
- Funciona como uma estratégia que proclama a criação de todos os ativos de software de uma organização via metodologia de programação orientada a serviços.
- Os serviços são tratados como componentes de software dentro de uma forma de arquitetura de sistemas distribuídos.
- Apresenta as seguintes vantagens principais para a organização:
  - Reutilização de software;
  - Aumento da produtividade;
  - Maior agilidade;
  - Melhor alinhamento com os objetivos de negócio.

## 3. Funcionamento e Camadas da Arquitetura
- O trabalho é integralmente baseado em mensagens que trafegam em uma camada de transporte específica.
- Camada de Transporte ⟶ utiliza protocolos como HTTP, SMTP e IIOP para a movimentação das mensagens.
- Camada de Mensagens ⟶ as informações são empacotadas e disponibilizadas em formatos como XML e através do protocolo SOAP.
- Definição de serviço ⟶ compreensão sobre a disponibilização de uma funcionalidade externa para ser consumida como utilidade ou vantagem.
- Exemplo: a disponibilização pela Receita Federal de acesso à base de dados para consulta de validade de CPF sem expor a segurança total da base.
- Barramento de serviços ⟶ estrutura onde o desenvolvedor ou usuário envia mensagens de solicitação e recebe o retorno no mesmo formato.

## 4. Propriedades e Orientação
- Visão lógica ⟶ permite que programas acessem bancos de dados e implementem processos de negócio sem a necessidade de acesso direto ao banco.
- Mensagens de orientação ⟶ a interação ocorre entre agentes provedores e solicitantes por meio de mensagens de requisição e resposta.
- Encapsulamento ⟶ o agente solicitante não possui a necessidade de conhecer como a implementação interna do serviço é realizada.
- Descrição de orientação ⟶ o serviço é descrito por metadados processáveis por máquina contendo apenas detalhes importantes expostos ao público.
- Granularidade ⟶ utilização de um pequeno número de operações que lidam com mensagens relativamente grandes e complexas.
- Plataforma neutra ⟶ as mensagens são enviadas em formatos padronizados independentes da plataforma ou linguagem de desenvolvimento original.

## 5. Princípios da SOA
- Padronização do contrato de serviço ⟶ definição rigorosa de quais serviços serão prestados e quais mensagens podem ser encaminhadas;
- Baixo acoplamento ⟶ capacidade de vincular componentes fortalecendo a independência para que o serviço seja utilizado em diferentes sistemas;
- Abstração do serviço ⟶ capacidade de extrair a vantagem do serviço ocultando sua lógica de implementação;
- Autonomia do serviço ⟶ capacidade técnica de o serviço funcionar de maneira independente;
- Visibilidade do serviço ⟶ necessidade de o serviço ser acessível e localizável externamente;
- Independência do controle de estado ⟶ o serviço não deve ser dependente de estar ocupado ou não para ser consumido;
- Reusabilidade ⟶ característica que permite o uso do serviço em diversos contextos, sendo pilar da engenharia orientada a reuso;
- Capacidade de composição ⟶ possibilidade de utilizar diferentes componentes e serviços para compor uma funcionalidade única.

## 6. Características Essenciais
- Acoplamento fraco;
- Reutilização;
- Interoperabilidade;
- Padronização;
- Composição.

> [!TIP] DICAS: 
> - Para memorizar os princípios da SOA, utilize o mnemônico PaBaA VIRCa: Padronização, Baixo acoplamento, Abstração, Autonomia, Visibilidade, Independência de estado, Reusabilidade e Capacidade de composição.
> - Para as características, utilize o mnemônico A Ré IntePaCo: Acoplamento fraco, Reutilização, Interoperabilidade, Padronização e Composição.

> [!CAUTION] OBSERVAÇÃO: 
> - A interoperabilidade de sistemas é um conteúdo muito cobrado em provas de diversos cargos de TI, desde gestão até infraestrutura.
> - Pegadinha de prova ⟶ a interoperabilidade não é apenas o acesso à informação, mas a capacidade de troca eficiente e padronizada entre diferentes sistemas e organizações.
> - Atenção ao acoplamento ⟶ na arquitetura SOA, os serviços devem possuir acoplamento fraco para promover independência, e não acoplamento forte.