# REST

## 1. Conceito de REST
- Representational State Transfer é definido como um estilo arquitetural para sistemas de informação distribuídos.
- Permite projetar aplicativos web fracamente acoplados e otimizados para o ambiente da internet.
- Representa uma maneira distinta de utilizar o protocolo HTTP, oferecendo uma perspectiva inovadora sobre como as requisições podem ser realizadas.
- Diferente de padrões rígidos, o REST é uma forma de pensar sobre a estruturação de web services utilizando recursos nomeados.

> [!CAUTION] OBSERVAÇÃO: 
> - O REST não é um padrão ou uma arquitetura propriamente dita, mas sim um estilo arquitetônico que define restrições para o design de sistemas.

## 2. Identificação de Recursos e Métodos
- Qualquer informação disponível no sistema é considerada um recurso.
- Os recursos são identificados por um Localizador Uniforme de Recursos (URL) ou Identificador Uniforme de Recursos (URI).
- As URLs utilizam substantivos para identificar os recursos, enquanto os métodos HTTP atuam como verbos que definem as ações.

### 2.1 Métodos HTTP
- GET ⟶ obtém o estado atual do recurso identificado para fins de busca;
- PUT ⟶ realiza a atualização de um recurso já existente no sistema;
- POST ⟶ utilizado para a criação de um novo recurso;
- DELETE ⟶ promove a eliminação do recurso identificado no sistema.

## 3. Princípios do REST
- Interface uniforme ⟶ simplifica o desenvolvimento e promove a uniformidade das APIs;
- Recursos com múltiplas representações ⟶ permite que um mesmo conteúdo seja visualizado sob diferentes perspectivas;
- Hipermídia como máquina de estado ⟶ utilizado para gerenciar o estado da aplicação;
- Não armazenamento de estado (stateless) ⟶ as interações ocorrem de maneira independente sem que o sistema mantenha o estado da conexão.

> [!CAUTION] OBSERVAÇÃO: 
> - A característica stateless é um dos fundamentos mais abordados em provas, pois garante que as comunicações sejam independentes e escaláveis.

## 4. Formatos de Representação de Recursos
- Não existe um padrão obrigatório para a representação das informações trocadas, visto tratar-se de um estilo arquitetural.
- A escolha do formato contribui para a flexibilidade e eficiência na implementação de serviços web.

| FORMATO | CARACTERÍSTICA TÉCNICA |
|---|---|
| JSON | Baseado em texto, simples e eficiente no consumo de banda |
| XML | Formato estruturado utilizado em abordagens tradicionais |
| RSS/Atom | Utilizados especificamente para a publicação de feeds |

> [!TIP] DICAS: 
> - O JSON tem ganhado destaque como substituto do XML por apresentar maior simplicidade estrutural e rapidez nas requisições.

## 5. Semântica de Recursos REST
- Os recursos são entidades bem definidas com endereços e identificadores próprios dentro do sistema.
- Para a criação de um web service com semântica adequada, utilizam-se três pilares fundamentais.

### 5.1 Pilares da Semântica
- Mime Type ⟶ componente que serve para alterar as representações de um mesmo conteúdo;
- URL ⟶ endereço único utilizado para identificar cada recurso individualmente;
- Métodos HTTP ⟶ mecanismos responsáveis por provocar as alterações nos recursos identificados.

## 6. Comparativo entre REST e SOAP
- O REST é reconhecido por sua velocidade e eficiência, superando o SOAP especialmente em redes de alta latência.
- Enquanto o SOAP é limitado ao formato XML, o REST suporta múltiplos formatos como JSON, XML e texto simples.
- O REST exige menos largura de banda e recursos por possuir menor overhead de comunicação.

| CRITÉRIO | ABORDAGEM REST | ABORDAGEM SOAP |
|---|---|---|
| Natureza | Estilo arquitetural | Protocolo de comunicação |
| Formato de dados | Múltiplos formatos (JSON, XML, etc.) | Estritamente XML |
| Segurança | Suporta HTTPS e criptografia | Utiliza a especificação WS-Security |
| Performance | Alta performance e baixa latência | Mais complexo e com maior overhead |

> [!CAUTION] OBSERVAÇÃO: 
> - O REST não é restrito exclusivamente ao protocolo HTTP, embora seja amplamente utilizado com ele.
> - Diferente do que algumas questões sugerem, o REST oferece suporte à criptografia através do uso de HTTPS.