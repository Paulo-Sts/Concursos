# Evolução dos Bancos de Dados

## 1. Panorama Histórico e Evolução
- A evolução dos bancos de dados passou por diferentes fases, iniciando com sistemas de arquivos.
- Antes do modelo relacional, houve os modelos hierárquico e em rede.
- Com o avanço das linguagens orientadas a objetos, surgiram modelos semânticos, onde os dados passaram a ter significado.
- A partir de objetos complexos, desenvolveu-se o banco de dados orientado a objetos.
- Com a hipermídia (internet), a inteligência artificial e a necessidade de recuperação ampla de informação, chegou-se ao conceito de banco de dados "inteligente".

### 1.1 Sistemas de Arquivos
- Pode ser entendido como um programa que armazenava arquivos ou como aplicações guardadas em sistemas de arquivos.
- Representa uma fase anterior aos modelos de banco de dados estruturados.

## 2. Modelo Hierárquico
- Os dados são estruturados em forma de árvore, com registros conectados por ligações hierárquicas.
- Cada registro é uma coleção de campos, e cada campo possui um único valor.
- Neste modelo, um registro pai pode ter vários registros filhos, mas um registro filho tem apenas um pai.
- Existe um único registro do tipo raiz, que não participa como filho em nenhum relacionamento.
- Um registro do tipo raiz pode se relacionar com inúmeros registros filhos.

> [!TIP] DICAS:
> - Modelo hierárquico é como uma árvore genealógica: cada filho tem um único pai.
> - O registro raiz é único e não possui pai.

> [!CAUTION] OBSERVAÇÃO:
> - Diferente do modelo em rede, onde um filho pode ter múltiplos pais, no hierárquico isso não é permitido.

## 3. Modelo em Rede
- É utilizado em sistemas de grande porte.
- Permite que um registro filho tenha mais de um pai (relacionamentos muitos-para-muitos), diferentemente do modelo hierárquico.
- Estrutura-se como um grafo, onde os registros podem se conectar de forma mais flexível.

> [!CAUTION] OBSERVAÇÃO:
> - A principal diferença para o modelo hierárquico é que o filho pode ter mais de um pai.

## 4. Modelo Relacional
- Representa o banco de dados como uma coleção de relações, sendo a relação similar a uma tabela.
- Aplica operações de união e interseção de conjuntos.
- Atualmente é o modelo mais utilizado por ser flexível e adequado para resolver problemas de concepção e implementação.
- Possui uma sublinguagem ampla de comunicação padronizada: o SQL.
- Exemplo de relação: Médico x Especialidade.

### Tabela Médico
| CRM_MÉDICO | NOME_MÉDICO | COD_ESPECIALIDADE |
|------------|-------------|-------------------|
| 101-1      | John        | 001               |
| 102-2      | Maria       | 001               |
| 103-3      | Josh        | 002               |

### Tabela Especialidade
| COD_ESPECIALIDADE | DESC_ESPECIALIDADE |
|-------------------|--------------------|
| 001               | Ortopedia          |
| 002               | Anestesia          |

### 4.1 Tupla
- No modelo relacional, cada linha da tabela é chamada de tupla.
- A tupla representa um tipo de objeto com seus atributos, que são persistidos no banco de dados.

> [!CAUTION] OBSERVAÇÃO:
> - Os bancos de dados relacionais modernos (Oracle, PostgreSQL, MySQL, Firebird, SQLServer) são tecnicamente considerados modelos de dados relacionais.

## 5. Modelo Orientado a Objetos (OO)
- Surgiu com a popularização das linguagens de programação orientadas a objetos e devido às limitações de armazenamento e representação semântica do modelo relacional (objetos complexos).
- No modelo OO, toda entidade do mundo real é representada por um objeto, que associa um estado (propriedades) e um comportamento (operações/métodos).
- Estrutura do objeto: propriedades + métodos.
- Permite a abstração de conceitos do mundo real, construindo classes que representam objetos, como uma classe "Cadeira" com atributos (cor, material, pernas).

### 5.1 Exemplo de Definição de Tipo
```
1. define type FUNCIONARIO
2. tuple (
3.   nome: string;
1.   cpf: string;
2.   datanasc: Data;
3.   endereco: string;
4.   sexo: char;
5.   salario: float;
6.   supervisor: FUNCIONARIO;
7.   dept: DEPARTAMENTO;
8. )
```

### 5.2 Objetos Complexos
- "Funcionário" é um tipo de objeto que pode conter outro objeto dentro de si, como "supervisor" (também do tipo Funcionário).
- "Departamento" é outro exemplo de objeto complexo.
- Essa capacidade de composição é uma característica do modelo orientado a objetos.

### 5.3 Encapsulamento
- O encapsulamento é um princípio da orientação a objetos.
- Exemplo: ao dirigir um carro, o motorista interage com métodos públicos (acelerar, frear, passar marcha) sem precisar entender os detalhes internos do motor.
- A interação ocorre por meio de troca de mensagens.

## 6. Modelo de Dados (Conceito Geral)
- Um modelo de dados é um conjunto de conceitos usados para descrever a estrutura de um banco de dados.
- A estrutura envolve tipos de dados, relacionamentos e restrições que os dados devem suportar.
- Os bancos de dados permitem abstração, ocultando detalhes de armazenamento desnecessários para a maioria dos usuários.

## 7. NoSQL
- NoSQL é um conjunto de abordagens para armazenamento que não seguem o modelo relacional tradicional.
- Permite maior escalabilidade horizontal, adicionando mais nós para direcionar consultas.
- Oferece flexibilidade para lidar com grandes volumes de dados não estruturados.
- Não requer esquemas fixos, sendo ideal para aplicações dinâmicas e distribuídas.
- Classifica-se em diferentes modelos: documentos, chave-valor, colunas e grafos.
- É amplamente utilizado em Big Data, IoT, redes sociais e aplicações em tempo real.

> [!TIP] DICAS:
> - NoSQL é a escolha para aplicações que exigem alta escalabilidade e flexibilidade de esquema.
> - A escalabilidade horizontal é um diferencial do NoSQL em relação aos modelos tradicionais.