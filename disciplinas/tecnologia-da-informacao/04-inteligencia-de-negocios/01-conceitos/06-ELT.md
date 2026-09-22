#  ELT

## 1. ELT (Extract, Load, Transform)
- O ELT é um fluxo de transformação de dados que surgiu como alternativa ao ETL.
- Diferentemente do ETL, no ELT a carga ocorre antes da transformação.
- As etapas do ELT são:
  - Extração:
    - Identificação das fontes de dados;
    - Conexão e acesso a dados.
  - Carga:
    - Carregamento inicial no Data Lake;
    - Estruturação dos dados.
  - Transformação dos dados:
    - Preparação e transformação dos dados;
    - Uso de recursos nativos do ambiente de destino (ex.: processamento dentro do próprio Data Lake ou banco de dados).

## 2. ELT X ETL: Problemas e Benefícios do ELT
- O ELT apresenta desafios e vantagens em relação ao ETL.

### 2.1 Problemas do ELT
- Pipelines com menos maturidade.
- Menos profissionais habilitados no mercado.
- Menos segurança no processo de transformação.
- Análises mais demoradas e menos estáveis.

### 2.2 Benefícios do ELT
- Foco em dados semiestruturados e não estruturados.
- Foco em grandes bases de dados.
- Engenheiros de dados atuam apenas na extração e carga, deixando a transformação para outros profissionais.
- Os dados sempre estão disponíveis para consulta.
- Mais adaptado a data lakes.
- Reduz o tempo de carga dos dados.
- Baixo custo de manutenção do repositório de dados.
- Transformação ocorre no ambiente de destino, aproveitando seus recursos nativos.
- Transformação é mais rápida.
- Transformação é feita por especialistas do negócio (analistas).
- Permite a passagem de dados não estruturados para a análise.
- Esquema gravado no momento da análise (esquema de leitura - schema-on-read).

> [!TIP] DICAS: 
> - O ELT é o processo preferencial quando se trabalha com Data Lakes, pois os dados são carregados em sua forma bruta e transformados apenas quando necessário.
> - O fato de a transformação ser executada por especialistas do negócio agiliza o processo de análise, pois eles conhecem a regra de negócio.

> [!CAUTION] OBSERVAÇÃO: 
> - Em ELT, os dados são carregados antes da transformação, o que é o oposto do ETL (transforma antes de carregar).
> - A transformação no ELT é mais rápida porque ocorre no próprio ambiente de destino (onde os dados já estão armazenados).