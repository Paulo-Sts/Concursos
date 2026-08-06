# Arquitetura Orientada a Objetos

## 1. Fundamentos da Arquitetura
- Surgiu na década de 1970 e alcançou popularidade nos anos 1980.
- Baseia-se em princípios fundamentais da programação orientada a objetos, como classes, objetos, encapsulamento, abstração, herança e polimorfismo.
- Foca na interação entre objetos e na estruturação do código em torno de entidades que simulam elementos do mundo real.
- Linguagens de programação comumente associadas a essa arquitetura incluem Java, C++ e C#.
- Diferencia-se da arquitetura monolítica pois seus objetos funcionam de forma independente, enquanto na monolítica todos os elementos são interdependentes.

### 1.1 Vantagens da Orientação a Objetos
- Mapeamento natural para problemas e entidades da realidade;
- Modularidade, pois cada objeto funciona como um módulo independente;
- Facilidade de manutenção e manutenibilidade do sistema;
- Escalabilidade, permitindo a extensão do código com novas funcionalidades de forma simplificada.

## 2. Classes e Objetos
- Componentes fundamentais que definem a estrutura e a execução do sistema orientado a objetos.

### 2.1 Conceito de Classes
- Funcionam como um conjunto de instruções ou moldes para a construção de objetos.
- Atuam de maneira análoga a um formulário vazio, definindo tipos de dados, atributos e métodos que os objetos possuirão.
- Exemplo: a classe Livro estabelece a necessidade de título e autor, mas não contém dados de um livro específico em sua definição inicial.

### 2.2 Conceito de Objetos
- Representam instâncias de classes, funcionando como a versão real e materializada do que foi definido no molde.
- Enquanto a classe estabelece o que um elemento pode ser, o objeto efetivamente é, existindo com dados concretos no sistema.
- Exemplo: um objeto da classe Livro teria atributos preenchidos como Título: Jogos Vorazes e Autora: Suzanne Collins.

## 3. Mecanismos de Controle e Acesso
- Estratégias utilizadas para garantir a segurança, integridade e organização dos dados dentro dos objetos.

### 3.1 Encapsulamento
- Técnica que consiste em esconder dados internos e atributos privados por questões de segurança e facilitação da manipulação.
- Protege a integridade das informações sensíveis, garantindo que não sejam acessadas ou alteradas diretamente por outras partes do código.
- Reduz a possibilidade de alterações acidentais e acessos não autorizados em sistemas complexos.

### 3.2 Atributos e Métodos de Acesso
- Atributos privados ⟶ dados definidos dentro de uma classe que não podem ser acessados diretamente de fora dela;
- Construtores ⟶ métodos especiais usados para inicializar os atributos de um novo objeto com valores específicos no momento de sua criação;
- Getters ⟶ métodos públicos conhecidos como métodos de leitura que permitem acessar os valores de atributos privados;
- Setters ⟶ métodos públicos de modificação que permitem alterar os valores de atributos privados de maneira controlada;
- Métodos ⟶ funções que simulam ações que podem ser realizadas pelo objeto, como emprestar ou devolver no caso de um livro.

## 4. Pilares de Reuso e Complexidade
- Conceitos que permitem a criação de sistemas flexíveis e de fácil evolução.

### 4.1 Abstração
- Visa esconder a complexidade técnica do software para que a pessoa programadora foque em interações de alto nível.
- Permite a criação de modelos simplificados para representar entidades complexas do mundo real.
- Oculta detalhes de implementação que não são necessários para o uso cotidiano das classes no sistema.

### 4.2 Herança
- Pilar que permite que uma classe herde atributos e métodos de outra, promovendo a reutilização eficiente de código.
- Estabelece uma relação hierárquica entre classes base (superclasses) e classes derivadas (subclasses).
- Exemplo: uma classe Animal pode servir de base para as classes Cachorro e Gato, que herdarão características comuns como nome e idade.

### 4.3 Tipos de Herança
- Herança simples ⟶ ocorre quando uma subclasse herda características de apenas uma única classe pai ou superclasse;
- Herança múltipla ⟶ permite que uma classe derivada herde atributos e métodos de mais de uma classe base simultaneamente.

| CONCEITO | FUNÇÃO NO SISTEMA |
|---|---|
| CLASSES | Conjunto de instruções ou moldes para construção |
| OBJETOS | Instâncias reais com dados concretos |
| ENCAPSULAMENTO | Esconder dados internos por segurança |
| ABSTRAÇÃO | Reduzir complexidade ocultando detalhes técnicos |
| HERANÇA | Reutilização de código através de hierarquia |

> [!TIP] DICAS: 
> - Pense na classe como a planta de uma casa e no objeto como a casa pronta e mobiliada.
> - O encapsulamento é como a carcaça de um motor: você usa os botões (métodos públicos) sem precisar tocar nas engrenagens internas (atributos privados).

> [!CAUTION] OBSERVAÇÃO: 
> - Em provas de concurso, lembre-se que encapsular não serve apenas para segurança, mas também para facilitar a manutenção das informações.
> - A herança múltipla pode introduzir o problema do diamante, causando ambiguidades quando métodos iguais são herdados de diferentes classes base.
> - O design de software pode ser visto como produto (abstração do mundo real) ou como processo (orientado a objetivos).