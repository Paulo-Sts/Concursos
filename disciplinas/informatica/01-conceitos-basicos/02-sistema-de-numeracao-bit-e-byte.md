# Sistema de Numeração Bit e Byte

## 1. Bases Numéricas
- Os seres humanos utilizam a base decimal (0 a 9).
- Computadores operam em baixo nível com a base binária (0 e 1), pois a eletrônica representa esses valores através de pulsos elétricos (ligado/desligado).
- Outras bases utilizadas na computação: Octal (0 a 7) e Hexadecimal (0 a 9 e letras A a F).

## 2. Unidades de Medida de Informação
- Bit (Binary Digit): É a menor unidade de informação. Pode assumir apenas dois valores: 0 ou 1.
- Byte (Binary Term): É o conjunto de 8 bits. É a unidade utilizada para representar um caractere (letra, número ou símbolo).

## 3. Hierarquia de Armazenamento
- As capacidades de memória e armazenamento seguem uma progressão. Para converter entre elas, utiliza-se a base 1024 (2 elevado a 10):
  - Byte (B)
  - Kilobyte (KB) = 1.024 Bytes
  - Megabyte (MB) = 1.024 KB
  - Gigabyte (GB) = 1.024 MB
  - Terabyte (TB) = 1.024 GB
  - Petabyte (PB) = 1.024 TB
  - Exabyte (EB) = 1.024 PB

## 4. Macete para Memorização
- Uma técnica comum para lembrar a ordem das unidades (B, K, M, G, T, P, E) é a frase: "**B**urger **K**ing **M**uito **G**rande **T**enho **P**ara **E**u".

## 5. Regras de Conversão
- Para subir na escala (ex: de Byte para KB): Divide-se por 1024.
- Para descer na escala (ex: de GB para MB): Multiplica-se por 1024.
- Aproximação para cálculos rápidos: Em algumas questões, pode-se arredondar 1024 para 1000 para encontrar um valor aproximado (ex: 578.400.256 bytes é aproximadamente 551 MB quando dividido precisamente por 1024 duas vezes).

## 6. Pontos-Chave para Concursos
- Bit vs. Byte: Um Byte tem sempre 8 bits. Atenção a pegadinhas que trocam essas unidades.
- Siglas: "b" minúsculo geralmente indica bit (usado em velocidade de internet, ex: Mbps), enquanto "B" maiúsculo indica Byte (usado em tamanho de arquivos).
- Base Hexadecimal: Lembrar que após o número 9, utilizam-se letras (A=10, B=11, C=12, D=13, E=14, F=15).
- Armazenamento: Saber que um arquivo de texto ocupa poucos KB, uma foto alguns MB e um filme em alta definição alguns GB.