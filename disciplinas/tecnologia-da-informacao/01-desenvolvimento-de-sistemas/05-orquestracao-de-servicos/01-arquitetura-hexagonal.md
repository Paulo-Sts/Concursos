# Arquitetura Hexagonal

## 1. Introdução e Propósito
- Criada em 2005 por Alistair Cockburn.
- Também denominada Arquitetura de Portas e Adaptadores.
- Objetivo central ⟶ isolar o núcleo da aplicação de todas as dependências externas.
- Baseia-se em três pilares fundamentais: núcleo da aplicação, portas e adaptadores.

## 2. Núcleo da Aplicação
- Representa o coração do sistema, onde reside toda a lógica de negócios.
- Caracteriza-se pela independência total de bancos de dados, APIs e interfaces de usuário.
- Permite a realização de testes e manutenção sem interferência da infraestrutura.
- Possibilita o reuso em variados contextos, como aplicações web ou aplicativos móveis.

### 2.1 Componentes do Núcleo
- Classes de domínio: representam conceitos de negócio, como pedido ou cliente, encapsulando dados e lógica.
- Responsabilidade das classes: manter o estado e a integridade do conceito que representam.
- Serviços de domínio: classes destinadas a lógicas complexas ou que coordenam ações entre múltiplas classes de domínio.
- Regras de negócios e lógica: métodos operacionais que garantem a conformidade das ações com as normas do negócio.

## 3. Portas
- Atuam como interfaces que definem o protocolo de comunicação entre o núcleo e o ambiente externo.
- Garantem que o núcleo interaja com tecnologias distintas sem conhecer seus detalhes técnicos.

### 3.1 Classificação das Portas
- Portas primárias (inbound ports): interfaces que possibilitam a entrada de dados e comandos para o núcleo.
- Exemplo ⟶ operações de realizar pedido ou calcular preço em sistemas de vendas.
- Portas secundárias (outbound ports): interfaces que permitem ao núcleo enviar informações ou solicitar serviços externos.
- Exemplo ⟶ ações de salvar pedido ou realizar consultas em sistemas de estoque.

## 4. Adaptadores
- Estabelecem a conexão física entre o núcleo e as tecnologias externas como bancos de dados ou interfaces.
- Realizam a tradução técnica das mensagens que entram e saem do núcleo.
- Proporcionam flexibilidade ao sistema, permitindo a troca de tecnologias apenas com a alteração do adaptador correspondente.

### 4.1 Classificação dos Adaptadores
- Adaptadores primários (inbound adapters): vinculam a interface de usuário ao núcleo da aplicação.
- Exemplo ⟶ controladores HTTP que transformam requisições web em chamadas de métodos internos.
- Adaptadores secundários (outbound adapters): vinculam o núcleo a sistemas de suporte como bancos de dados ou serviços externos.
- Exemplo ⟶ implementação de repositórios que efetuam a gravação em bases SQL.

> [!TIP] DICAS: 
> - As classes de domínio devem ser totalmente independentes de classes de infraestrutura e sistemas externos.
> - O núcleo da aplicação nunca deve ser responsável pelo armazenamento físico dos dados ou pela tecnologia usada para esse fim.

> [!CAUTION] OBSERVAÇÃO: 
> - As principais vantagens da arquitetura hexagonal cobradas em provas são:
>   - Elevada manutenibilidade;
>   - Facilidade de realização de testes;
>   - Tolerância em relação a mudanças e variações tecnológicas.