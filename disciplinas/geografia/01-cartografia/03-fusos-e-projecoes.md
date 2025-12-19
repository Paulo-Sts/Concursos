# Fusos Horários e Projeções Cartográficas

## Fusos horários
- Sistema criado em 1883 (Conferência de Roma) para padronização do horário mundial
- Meridiano de Greenwich (0°) adotado como referência em 1884
- A cada 15° de longitude → 1 hora de diferença
- A cada 1° de longitude → 4 minutos de diferença
- Horas adiantadas a leste de Greenwich
- Horas atrasadas a oeste de Greenwich

#### Cálculo de fusos horários

##### Hemisférios diferentes (Leste/Oeste)
1. Somar os valores das longitudes
2. Dividir por 15 para obter a diferença em horas
3. Se deslocamento para leste → somar horas
4. Se deslocamento para oeste → subtrair horas

##### Hemisférios iguais (Leste/Leste ou Oeste/Oeste)
1. Subtrair os valores das longitudes
2. Dividir por 15 para obter a diferença em horas
3. Se deslocamento para leste → somar horas
4. Se deslocamento para oeste → subtrair horas

##### Hora fracionada
- Multiplicar o resto da divisão por 4 (cada 1° = 4 minutos)

##### Tempo de transporte
- Acrescentar o tempo de viagem ao resultado final

#### Fusos horários do Brasil

| FUSO        | MERIDIANO | ABRANGÊNCIA                                                                                 |
|-------------|-----------|---------------------------------------------------------------------------------------------|
| 1º (2h GMT) | 30° W     | Ilhas oceânicas                                                                             |
| 2º (3h GMT) | 45° W     | DF, GO, TO, AP, MA, PI, CE, RN, PB, PE, AL, SE, BA, MG, ES, RJ, SP, PR, SC, RN, leste do PA |
| 3º (4h GMT) | 60° W     | Quase todo AM, oeste do PA, RR, RO, MT, MS                                                  |
| 4º (5h GMT) | 75° W     | Sudoeste do AM, AC                                                                          |

#### Linha internacional de data (LID)
- Localizada em 180° de longitude
- Ao cruzar de oeste para leste → adiciona-se 1 dia
- Ao cruzar de leste para oeste → subtrai-se 1 dia
- Exceção: áreas entre 172,5°L e 172,5°O têm mesma hora mas dias diferentes

## Projeções cartográficas
- Representação da superfície terrestre em um plano
- Todas as projeções apresentam deformações

> ### Classificação das projeções

#### Cilíndricas
- Projeção sobre cilindro envolvente
- Ângulos de 90° entre paralelos e meridianos
- Exemplo: Mapa-mundi
- Maiores deformações nas extremidades

#### Cônicas
- Projeção sobre cone
- Ideal para latitudes médias
- Linhas médias com tamanho real

#### Azimutais (planas)
- Projeção sobre plano tangente
- Ideal para regiões polares
- Polo no centro com tamanho real

> ### Tipos de projeções cilíndricas

#### Conforme (Mercator)
- Valoriza as formas
- Distorce proporções e distâncias

#### Equivalente (Peters)
- Valoriza as proporções
- Distorce formas e distâncias

#### Equidistante
- Valoriza as distâncias

> ### Outras projeções
- Robinson: pseudo-cilíndrica, afilática
- Mollweide: formato oval
- Lambert: projeção cônica
- Anamorfose: distorção para valorizar características específicas (ex: população, PIB)