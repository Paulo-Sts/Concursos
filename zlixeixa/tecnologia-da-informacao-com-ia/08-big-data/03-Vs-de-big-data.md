# Vs de Big Data

## 1. Conceitos Fundamentais do Big Data
- Big Data é caracterizado por um conjunto de atributos conhecidos como "Vs", que definem suas principais dimensões e desafios.
- A definição inicial do conceito era baseada em três Vs essenciais: Volume, Variedade e Velocidade.
- Com a evolução da área, novos Vs foram incorporados para ampliar a definição, chegando a modelos com 5Vs, 6Vs ou até 7Vs.
- A compreensão desses atributos é fundamental para projetos de Big Data, pois orienta a gestão e análise de grandes volumes de dados.

## 2. Os 3 Vs Iniciais do Big Data
- Para que uma base de dados seja considerada Big Data, é necessário atender a três premissas essenciais.

### 2.1 Volume
- Refere-se à quantidade massiva de dados gerados e armazenados.
- Os dados podem chegar a terabytes, petabytes ou exabytes.
- Exemplos:
  - Registros de transações financeiras globais.
  - Dados de sensores em fábricas.
  - Uploads de usuários para o YouTube, que em 2016 exigiam 1 petabyte de nova capacidade de armazenamento por dia.
  - Facebook armazenando cerca de 250 bilhões de imagens, exigindo exabytes de armazenamento em 2018.

### 2.2 Velocidade
- Refere-se ao ritmo com que os dados são criados, transmitidos e processados.
- Em muitos casos, o valor da informação depende de ser processada rapidamente, pois se for extemporânea, já não terá utilidade.
- Os sistemas de Big Data precisam lidar com dados que chegam sob a forma de fluxos em tempo real.
- Exemplos:
  - Processamento de dados de bolsa de valores em milissegundos.
  - Monitoramento de tráfego em tempo real (Waze, Google Maps).
  - Processamento de dados de dispositivos IoT (câmeras, sensores).
  - Facebook processa mais de 900 milhões de fotos carregadas por dia.
  - Alibaba processou 470 milhões de registros de eventos por segundo durante um período de pico.

### 2.3 Variedade
- Refere-se à diversidade de formatos, origens e tipos de dados.
- Classificação dos dados:
  - Estruturados: tabelas e bancos SQL (formato tabular).
  - Semiestruturados: XML, JSON, logs (possuem organização própria, mas não em formato de tabela).
  - Não estruturados: imagens, vídeos, áudios, textos livres (não seguem uma organização predefinida).
- Exemplos:
  - Postagens em redes sociais (incluem imagens e vídeos).
  - Registros de vendas.
  - Fotos de satélite.
  - WhatsApp (armazena mensagens de texto, figurinhas, áudios, imagens e vídeos).

> [!CAUTION] OBSERVAÇÃO:
> - Aproximadamente 80% a 90% dos dados gerados atualmente são não estruturados ou semiestruturados.
> - Os bancos de dados relacionais tradicionais foram projetados para dados estruturados; o Big Data precisa gerenciar e processar todos os tipos de dados perfeitamente.

## 3. Ampliação do Conceito: 5Vs
- Além dos três Vs iniciais, acrescentam-se dois atributos essenciais.

### 3.1 Veracidade
- Refere-se à confiabilidade, segurança e qualidade dos dados.
- Envolve a precisão e integridade das informações, evitando erros, dados incompletos, inconsistentes ou fontes não verificadas.
- Desafios:
  - Dados incompletos ou inconsistentes.
  - Fontes não verificadas.
  - Dados confusos, ruidosos e propensos a erros que comprometem sua confiabilidade.
- Exemplos:
  - Fake news em redes sociais.
  - Erros de digitação em cadastros.
  - Dados com anomalias ou corrompidos.

> [!TIP] DICAS:
> - A veracidade está diretamente associada à confiabilidade e à qualidade dos dados, influenciando a precisão dos resultados obtidos a partir deles.
> - Dados sem veracidade não podem ser considerados Big Data, pois carecem de qualidade e segurança.
> - O ruído nos dados (informações incorretas, inconsistentes ou mal coletadas) é um problema clássico tratado pela veracidade.

### 3.2 Valor
- Refere-se à capacidade de extrair insights úteis que apoiem a tomada de decisão.
- Sem valor, Big Data é apenas armazenamento caro.
- Está ligado à utilidade e relevância dos dados para gerar benefícios e vantagem competitiva para a organização.
- Exemplos:
  - Análise de padrões de consumo para campanhas de marketing.
  - Previsão de demanda para reduzir estoques.
  - Transformar dados em resultados práticos com impacto real em decisões estratégicas.

> [!TIP] DICAS:
> - O valor está ligado à capacidade de extrair utilidade prática dos dados, agregando significado e benefícios à organização.
> - Não basta armazenar dados; é preciso transformá-los em insights acionáveis.

## 4. Expansão Adicional: Variabilidade e Visualização
- Algumas abordagens expandem o conceito para incluir 7Vs, sendo este último explorado em questões de bancas examinadoras como o Cebraspe.

### 4.1 Variabilidade
- Refere-se ao grau de instabilidade, flutuação ou mudança de significado dos dados ao longo do tempo.
- Mesmo dados provenientes da mesma fonte podem variar de comportamento ou contexto, exigindo ajustes na análise.
- Desafios:
  - Dados que apresentam picos sazonais (ex.: aumento de vendas no Natal).
  - Mudança na forma de coleta ou no padrão de geração dos dados.
  - Mudança de contexto que modifica o significado dos indicadores.
- Exemplos práticos:
  - Fraudes em cartão de crédito: sistemas de detecção precisam ser retreinados, pois os fraudadores mudam de estratégia.
  - Picos sazonais: aumento de vendas em períodos como o Natal exige adaptação dos modelos.
  - Mudança na fonte de dados: alterações na coleta podem inviabilizar pipelines existentes.
  - Análise de sentimentos: gírias ou expressões regionais podem confundir a interpretação automática.
  - Indicadores econômicos: o contexto pode alterar o significado dos dados, exigindo nova interpretação.

### 4.2 Visualização
- Refere-se à capacidade de transformar grandes volumes e diversidade de dados em representações gráficas claras e interpretáveis.
- Facilita a compreensão, descoberta de padrões e apoio à tomada de decisão.
- Não basta apenas armazenar e extrair os dados; é preciso apresentá-los de uma forma que as pessoas consigam entendê-los.
- Ferramentas:
  - Power BI.
  - Tableau.
  - Kibana (Elastic Search Stack).
  - Grafana.
- Exemplos:
  - Dashboards em tempo real para monitorar desempenho de vendas.
  - Mapas de calor para identificar regiões com maior incidência de crimes.
  - Séries temporais para acompanhar variação de indicadores econômicos.

> [!CAUTION] OBSERVAÇÃO:
> - A inclusão de Variabilidade e Visualização como Vs adicionais pode ser considerada para uma compreensão mais completa do tema.
> - O modelo mais comum utiliza cinco Vs (Volume, Velocidade, Variedade, Veracidade e Valor), mas existem outros, como os sete Vs, que expandem essa definição.
> - Volume: característica mais comum do Big Data.
> - Velocidade: talvez seja a característica mais negligenciada do Big Data.
> - Variedade: responsável por impor desafios contextuais adicionais para armazenamento, tratamento e análise.
> - Veracidade: tratada como o quarto V pela IBM.
> - Valor: o diferencial está na capacidade de transformar dados em insights aplicáveis.
> - Variabilidade: dados podem variar de comportamento ou contexto, exigindo ajustes na análise.
> - Visualização: facilita a compreensão e a descoberta de padrões.

## 6. Principais Desafios do Big Data
- O Big Data apresenta desafios significativos que vão além do simples armazenamento de grandes volumes de informações.

### 6.1 Desafios Relacionados à Implantação
- Velocidade de geração e processamento: os dados são gerados rapidamente e precisam ser processados quase em tempo real.
- Segurança e privacidade: é necessário adotar políticas e técnicas robustas para garantir a integridade e a confiabilidade dos dados.
- Especialização profissional: o processo demanda especialistas para manipulação, análise e interpretação dos dados.

> [!CAUTION] OBSERVAÇÃO:
> - A adoção do Big Data não implica na dispensa de profissionais de tecnologia da informação.
> - Não há impossibilidade de adotar medidas robustas para tratar a segurança e privacidade; trata-se de um desafio que requer políticas e técnicas adequadas.

### 6.2 Desafios Relacionados aos Dados
- Dados não estruturados: a predominância (aproximadamente 80%) de dados não estruturados exige soluções tecnológicas capazes de lidar com diferentes formatos simultaneamente.
- Limpeza de dados: dados sujos (com erros, ruídos, inconsistências, desinformações deliberadas) custam bilhões de dólares por ano; os sistemas de Big Data precisam limpar os dados e manter sua proveniência para justificar sua confiabilidade.
- Variedade de fontes: os dados vêm de muitas fontes, cada uma com estruturas distintas e níveis de confiabilidade variados.

### 6.3 Complexidade do Big Data
- O desafio do Big Data não se restringe ao tamanho dos arquivos ou à quantidade de sistemas de armazenamento disponíveis.
- A complexidade está no conjunto de fatores que envolvem o volume massivo de dados, a velocidade com que são gerados e processados e a variedade de formatos e fontes.
- Esses elementos exigem soluções tecnológicas avançadas para viabilizar a coleta, o tratamento e a análise de informações em grande escala.

> [!TIP] DICAS:
> - A análise de Big Data permite identificar padrões, extrair insights estratégicos e apoiar diferentes áreas, como marketing, saúde, finanças e segurança pública.
> - O uso de Machine Learning não elimina a necessidade de intervenção humana, já que a responsabilidade pelas decisões permanece sempre com as pessoas.