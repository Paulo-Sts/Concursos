# Conceitos de Internet e Intranet 2

## 1. Modos de Acesso por Cabo
- A internet é definida como a conexão entre várias redes, representando a rede mundial de computadores.
- Existem diversas formas de realizar essa conexão, utilizando meios físicos (wired) ou sem fio (wireless).

### 1.1 Conexão Discada
- Método onde o usuário liga para um provedor de internet utilizando modems discados que ocupam integralmente a linha telefônica.
- O modem atua como um modulador de sinal para estabelecer a conexão via linha telefônica física.
- Vantagens e desvantagens:
  - Manutenção extremamente barata para a época;
  - Possibilidade de uso de placas internas no computador;
  - Ocupação total da linha telefônica, impedindo chamadas de áudio;
  - Presença de ruídos (chiados) e alta instabilidade na conexão.

### 1.2 Linha Digital Assimétrica
- Tecnologia conhecida como ADSL que permite separar o áudio da frequência de dados.
- Possibilita a utilização simultânea da internet e da linha telefônica fixa sem interrupções.
- Garante uma conexão mais rápida em relação ao modelo discado e disponibilidade durante 24 horas por dia.

### 1.3 Modem por Cabo
- Utiliza redes de transmissão de televisão a cabo convencionais (Community Antenna Television) para a transmissão de dados.
- Faz uso da porção de banda que não é utilizada pelo sinal da TV para alcançar velocidades que variam de 70 kbps a 1 gbps.
- Em estruturas industriais, a velocidade de transmissão de dados pode ultrapassar a marca de um gigabit por segundo.

> [!TIP] DICAS: 
> - A sigla modem significa modulador de sinal, sendo o dispositivo responsável por traduzir os sinais para possibilitar o enlace entre as pontas.

## 2. Conexões sem Fio
- Conexões do tipo wireless são utilizadas em locais onde a instalação de cabos físicos é impossibilitada.

### 2.1 Acesso via Satélite
- Método que pode ser oferecido em qualquer parte do planeta, sendo ideal para comunidades afastadas ou áreas rurais.
- A comunicação ocorre por meio de uma triangulação entre o cliente, o satélite em órbita e o servidor do provedor.
- Caracteriza-se por ser um tipo de internet de custo elevado devido à complexidade da estrutura necessária.

### 2.2 Distribuição por Rádio
- Consiste na distribuição do sinal captado por um link dedicado através de antenas e pontos de presença (POPs) espalhados pela cidade.
- Forma uma malha de conexão ou rede de usuários que redistribui o sinal de forma ampla.

### 2.3 Energia Elétrica
- Tecnologia denominada PLC (Power Line Communication) que utiliza a rede de energia elétrica mundial para transmissão.
- Utiliza pulsos de comunicação através do cabo de cobre da rede elétrica para possibilitar o funcionamento da internet.

> [!CAUTION] OBSERVAÇÃO: 
> - O roteador é o dispositivo encarregado de criar uma rota específica entre dois pontos, sendo capaz de desconsiderar pontos de falha na rede.

## 3. Redes Privadas e Corporativas
- O acesso a recursos digitais pode ser classificado de acordo com a privacidade e a organização que gerencia a rede.

### 3.1 Características da Intranet
- Rede corporativa privada cujo acesso e gerenciamento são realizados por uma organização específica.
- Utiliza a pilha de protocolos TCP/IP, sendo o TCP (Transmission Control Protocol) e o IP (Internet Protocol) os mais importantes.
- Para o acesso remoto ou fora do ambiente físico da empresa, utilizam-se softwares específicos como a VPN (Virtual Private Network).
- VPN ⟶ rede virtual que estabelece uma conexão direta e segura entre dois pontos, evitando interceptações no caminho.

### 3.2 Função da Extranet
- Funciona como uma extensão da intranet, ampliando o acesso que anteriormente era restrito ao ambiente interno.
- Permite que usuários externos autorizados, como parceiros de negócios, fornecedores e clientes, acessem recursos específicos da organização.
- Diferente da internet, a extranet mantém o caráter de uso restrito e controlado por permissões.

## 4. Divisões da Rede Mundial
- A internet pode ser classificada em partes distintas de acordo com a visibilidade e indexação do seu conteúdo.

### 4.1 Surface Web e Deep Web
- Surface web: corresponde à parte da internet que pode ser facilmente encontrada e indexada por mecanismos de busca como o Google.
- Deep web: parte não indexável da rede que oculta informações para proteger a privacidade do usuário e dados governamentais.
- Dark web: área específica e restrita dentro da deep web frequentemente utilizada para a inserção de conteúdos ilegais e anonimato.

> [!TIP] DICAS: 
> - Qualquer componente conectado e configurado em uma rede de comunicação, como celulares, tablets ou impressoras, é designado pelo termo hosts.

## 5. Tabela Comparativa de Acessos
| TIPO DE ACESSO | MEIO DE TRANSMISSÃO | CARACTERÍSTICA DE USO |
|---|---|---|
| Discada | Linha telefônica física | Ocupa a linha com velocidade de 56 kbps |
| Adsl | Linha digital assimétrica | Separa o áudio dos dados para uso simultâneo |
| Cable modem | Cabo de tv por assinatura | Compartilha o meio com sinais de televisão |
| Satélite | Ondas de rádio e satélite | Triangulação de sinal para áreas remotas |
| Energia (plc) | Rede de energia elétrica | Utiliza pulsos em cabos de cobre existentes |

> [!CAUTION] OBSERVAÇÃO: 
> - O termo backbone refere-se à espinha dorsal da internet, composta por uma estrutura global de roteadores que permitem a conexão entre países.
> - Os endereços IP reservados para redes internas na intranet não podem ser iguais aos endereços IP utilizados na internet pública.