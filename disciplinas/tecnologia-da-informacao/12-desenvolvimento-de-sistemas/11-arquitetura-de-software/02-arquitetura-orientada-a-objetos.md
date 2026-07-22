# Arquitetura Orientada à Objetos

## 1. Conceitos Fundamentais
- Surgiu em 1970 e se popularizou em 1980.
- Utiliza princípios de programação orientada a objetos.
- Enfatiza a interação entre objetos.
- Código é estruturado em torno de entidades do mundo real.
- Comumente usado em linguagens como Java e C#.

### 1.1 Paradigma Orientado a Objetos
- Paradigmas de programação são um conjunto de técnicas utilizadas para formar a estrutura de um sistema.
- O principal paradigma usado nessa arquitetura é o orientado a objetos.
- Quando se afirma que o código é modelado em volta de entidades do mundo real, significa que criamos classes que simulam coisas que realmente existem.
- Exemplo: uma classe "Livro" simula uma entidade do mundo real, que seria um livro de verdade.
- Ao criar um objeto a partir dessa classe definida, ele passa a existir no programa, no sistema.
- É comumente usado em linguagens como Java (linguagem orientada a objetos) e C# (linguagem multiparadigma, incluindo o paradigma orientado a objetos).

### 1.2 Vantagens da Arquitetura Orientada a Objetos
- Mapeamento natural para problemas do mundo real: simula entidades que existem e traz essas entidades para dentro do código.
- Modularidade: cada módulo, nesse caso, é um objeto.
- Manutenibilidade: adicionar uma funcionalidade nova ou alterar uma já existente é mais fácil, porque os objetos funcionam de forma independente.
- Escalabilidade: facilita a extensão do código com novas funcionalidades.

> [!CAUTION] OBSERVAÇÃO: 
> - Ao contrário da arquitetura monolítica, em que todos os elementos eram interdependentes, na arquitetura orientada a objetos, cada objeto funciona de forma independente.

## 2. Classes

### 2.1 Definição
- Classes são um conjunto de instruções para construir objetos.
- Podem ser pensadas como um formulário vazio: define o tipo de dado que vai existir nos objetos, os atributos e os métodos, mas as informações estão vazias.

### 2.2 Estrutura de uma Classe
- Define tipos de dados.
- Define atributos (características).
- Define métodos (comportamentos/ações).

### 2.3 Exemplo de Classe
- Classe: Livro.
- Atributos: título, autor(a), ano de publicação.
- Métodos: emprestar e devolver.

## 3. Objetos

### 3.1 Definição
- Objetos são instâncias de classes, representando a versão real do que a classe definiu.
- Enquanto a classe define o que pode ser, o objeto é a concretização dessa definição, existindo com dados reais no sistema.

### 3.2 Exemplo de Objeto
- Objeto da classe Livro.
- Atributos:
  - Título: Jogos Vorazes.
  - Autora: Suzanne Collins.
  - Ano de Publicação: 2008.
- Métodos: emprestar e devolver.

## 4. Encapsulamento

### 4.1 Definição
- Esconde os dados internos do objeto (atributos privados).
- Os dados só podem ser acessados por meio de métodos controlados (métodos públicos).
- Permite que informações sensíveis não estejam acessíveis diretamente no código.
- Para acessar esses dados, são criados métodos públicos que recuperam as informações de maneira segura, sem expô-las diretamente.
- Esses métodos servem como intermediários entre os dados privados e o restante do sistema, protegendo a integridade e a segurança das informações.

### 4.2 Atributos Privados
- Não podem ser acessados fora da classe definida.
- Exemplo: ao criar uma classe "Pessoa", é possível definir atributos como nome, CPF, e-mail e senha. Destes, o CPF e a senha podem ser definidos como atributos privados, ou seja, não estarão acessíveis diretamente por outras partes do código.

### 4.3 Construtores
- Usados para inicializar os atributos do novo objeto com valores específicos.
- O construtor recebe os valores necessários para os atributos e os atribui ao objeto no momento de sua criação.
- Exemplo: ao criar um objeto a partir da classe "Pessoa", o construtor pode receber parâmetros como nome, CPF, e-mail e senha, inicializando os atributos do objeto com esses valores.

### 4.4 Métodos Públicos
- *Getters*: permitem a leitura dos atributos privados.
- *Setters*: permitem modificar os valores de atributos privados.
- Métodos: simulam ações que podem ser realizadas.

> [!TIP] DICAS: 
> - Encapsular = esconder os dados por questões de segurança e para facilitar a manipulação das informações.

## 5. Abstração

### 5.1 Definição
- Esconde a complexidade de um sistema de software.
- Permite a criação de modelos simples de entidades complexas do mundo real.
- Permite que a pessoa programadora se concentre em interações de nível mais alto, sem preocupação com detalhes.
- Permite a criação de modelos simples para representar entidades complexas do mundo real, definindo classes que encapsulam a lógica e os dados necessários para a operação do sistema, mas ocultam os detalhes de implementação que não são necessários para o uso cotidiano dessas classes.

### 5.2 Exemplo Prático
- Classe Abstrata ItemBiblioteca.
  - Atributos protegidos: título, autor, anoDePublicação.
  - Métodos Abstratos: emprestar(), devolver().
- Classe Livro (extende ItemBiblioteca).
  - Implementação específica para emprestar um livro: imprimir "Livro emprestado: " + título.
  - Implementação específica para devolver um livro: imprimir "Livro devolvido: " + título.
- Classe Revista (extende ItemBiblioteca).
  - Atributos privados: edição.
  - Implementação específica para emprestar uma revista: imprimir "Revista emprestada: Edição " + edição.
  - Implementação específica para devolver uma revista: imprimir "Revista devolvida: Edição " + edição.

> [!TIP] DICAS: 
> - A abstração permite que diferentes tipos de itens de biblioteca sejam manipulados de maneira consistente, utilizando a mesma interface, mas com a flexibilidade de cada tipo de item ter suas próprias particularidades.

## 6. Herança

### 6.1 Definição
- Permite que uma classe herde atributos e métodos de outras classes.
- Permite a reutilização do código.
- Estabelece uma relação hierárquica entre classes.

### 6.2 Exemplo Prático
- Classe base "Animal".
  - Atributos: nome, idade.
  - Métodos: mover, emitirSom.
- Classe "Cão" (extende Animal).
  - Atributos: raça.
  - Métodos: latir (sobrescreve emitirSom).

### 6.3 Herança Simples
- Subclasse herda apenas da superclasse (classe pai).
- Exemplo: Cão ⟶ Animal (herda apenas de Animal).

### 6.4 Herança Múltipla
- Classe derivada herda atributos de mais de uma classe base.
- Exemplo:
  - Classe Terrestre: método caminhar.
  - Classe Aquático: método nadar.
  - Classe Anfíbio (extende Terrestre, Aquático): herda caminhar e nadar.

> [!CAUTION] OBSERVAÇÃO: 
> - A herança múltipla pode introduzir desafios, como o problema do diamante, em que uma subclasse herda os mesmos métodos de várias classes base, causando possíveis ambiguidades.

### 6.5 Comparação entre os Tipos de Herança

| TIPO DE HERANÇA | CARACTERÍSTICA | EXEMPLO |
|-----------------|----------------|---------|
| Herança simples | Subclasse herda de uma única classe base | Cão herda de Animal |
| Herança múltipla | Subclasse herda de mais de uma classe base | Anfíbio herda de Terrestre e Aquático |

> [!TIP] DICAS: 
> - Os quatro pilares da arquitetura orientada a objetos são: encapsulamento, abstração, herança e polimorfismo. 