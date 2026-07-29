# Conceitos de Internet e Intranet 

## 1. Conceitos Fundamentais e Pré-requisitos
- Para compreender internet, intranet e extranet, é necessário ter conhecimentos prévios sobre:
  - Conceitos de redes de computadores e comunicação de dados;
  - Categorias de redes (classificações por extensão geográfica);
  - Modelo TCP/IP e modelo OSI (protocolos de comunicação);
- Internet, intranet e extranet são formas de categorizar uma rede de computadores conforme a restrição, privacidade e segurança de acesso aos recursos.

### 1.1 Importante Distinção
- As categorias PAN, LAN, MAN e WAN referem-se à extensão geográfica da rede (alcance físico), e não a questões de privacidade, segurança ou restrição de acesso;
- Internet, intranet e extranet referem-se ao nível de restrição e privacidade dos recursos, podendo estar em qualquer extensão geográfica.

> [!CAUTION] OBSERVAÇÃO: 
> - Nem sempre a internet será uma WAN e a intranet será uma LAN. Isso é uma pegadinha comum em provas, pois a internet pode ser acessada via redes locais (LAN) e uma intranet pode conectar diferentes sedes em locais distantes (WAN).

## 2. Internet
- Trata-se da rede mundial de computadores, formada pela conexão entre várias redes ao redor do mundo;
- Características principais:
  - Possui alta capacidade de redundância e resiliência, podendo sobreviver a situações extremas (ex.: guerra atômica) devido à hiperconectividade e ao grande número de roteadores interligados por diferentes formas de conexão;
  - É uma rede pública e gratuita. O que é pago são os serviços dos provedores de acesso (utilização de infraestrutura, equipamentos e planos de conexão), mas a internet em si é livre e sem custo direto.

### 2.1 Divisão do Conteúdo da Internet
- Surface web: parte indexada da web, acessível por mecanismos de busca. Corresponde a 20% do conteúdo disponível;
- Deep web (também chamada de deepnet, web invisível, undertnet, web obscura ou web oculta): parte não indexada pelos mecanismos de busca, correspondendo a 80% do conteúdo disponível;
  - Foi originalmente criada por governos (EUA e Canadá) para proteger dados sigilosos e garantir um espaço seguro para informações não públicas;
  - Com o tempo, criminosos passaram a utilizar uma área específica da deep web, chamada de dark web, para publicar conteúdos ilícitos, aproveitando a característica de não indexação e anonimato.

### 2.2 Exemplo de Aplicação
- O acesso a sites comuns (ex.: portais de notícias, redes sociais, mecanismos de busca) ocorre na surface web;
- Sistemas internos de governos, bases de dados acadêmicas restritas e fóruns privados podem estar na deep web;
- A dark web é acessada por navegadores específicos (ex.: Tor) e contém tanto conteúdos legítimos (ex.: denúncias anônimas) quanto ilegais.

## 3. Intranet
- Rede de computadores privada que utiliza a mesma suíte de protocolos da internet (TCP/IP), mas é de uso exclusivo e restrito a um determinado grupo, organização ou localidade;
- Exemplos de uso: rede interna de uma empresa, sistema de uma escola, portal de colaboradores de uma instituição;
- O acesso é permitido apenas a usuários autorizados, como funcionários, colaboradores internos ou membros da organização.

### 3.1 Diferença entre Intranet e LAN
- Intranet não é sinônimo de LAN;
- Uma intranet pode abranger diferentes sedes de uma mesma empresa localizadas em cidades, estados ou até países distintos, sendo interligadas por conexões de longa distância (WAN ou MAN);
- Portanto, intranet está relacionada à restrição de acesso (rede privada), enquanto LAN está relacionada à extensão geográfica local.

> [!CAUTION] OBSERVAÇÃO: 
> - Não confunda intranet com LAN em provas. A banca costuma explorar essa diferença como pegadinha, afirmando que intranet é sempre uma LAN, o que é incorreto.

### 3.2 Exemplo de Aplicação
- Uma empresa com matriz em São Paulo e filiais no Rio de Janeiro e em Nova Iorque pode ter uma intranet que conecta todas as unidades, permitindo acesso a sistemas internos, independentemente da distância geográfica entre elas.

## 4. Extranet
- Trata-se de uma extensão da intranet que permite o acesso controlado a determinados recursos por usuários externos à organização;
- Não significa que a intranet se torna pública; apenas áreas específicas e recursos selecionados são liberados para acesso externo;
- O objetivo é possibilitar a colaboração com parceiros, clientes, fornecedores ou outras partes interessadas.

### 4.1 Características Principais
- A extranet conecta usuários da intranet à internet para viabilizar o acesso externo;
- Mantém a segurança e o controle de acesso, permitindo apenas que pessoas autorizadas (ex.: clientes cadastrados, parceiros comerciais) visualizem ou interajam com determinados conteúdos;
- É comumente utilizada para portais de clientes, sistemas de compras, áreas restritas para fornecedores e plataformas de ensino.

### 4.2 Exemplo de Aplicação
- O portal do Gran Concursos é acessado por colaboradores internos (intranet) e por alunos/clientes externos (extranet), que têm acesso a videoaulas, materiais e simulados, enquanto áreas administrativas permanecem restritas aos funcionários da empresa.

> [!TIP] DICAS: 
> - Memorize: Internet é pública; intranet é privada e interna; extranet é uma "área VIP" da intranet para convidados externos;
> - Atenção à pegadinha: internet não é sinônimo de WAN, e intranet não é sinônimo de LAN. As bancas adoram confundir classificação por extensão (PAN, LAN, MAN, WAN) com classificação por restrição de acesso (internet, intranet, extranet).