# Engenharia de Software - Requisitos 5

## 1. Validação de Requisitos
- É o processo de verificar se os requisitos especificados estão corretos e completos em relação ao que o usuário realmente deseja.
- Diferentes tipos de verificação devem ser efetuados durante este processo.
- O usuário deve dar a chancela final, comprovando que o requisito é realmente o objeto pensado.

> [!CAUTION] OBSERVAÇÃO: 
> - O processo da Engenharia de Requisitos é composto por atividades, mas cada uma das atividades pode ser entendida como um processo em si.

### 1.1 Verificações de Validade
- Um usuário pode pensar que é necessário um sistema para executar determinadas funções.
- Porém, uma análise mais aprofundada pode identificar funções adicionais ou diferentes das inicialmente pensadas.
- Os sistemas possuem diversos stakeholders com diferentes necessidades.
- Qualquer conjunto de requisitos é inevitavelmente um compromisso da comunidade de stakeholders.

### 1.2 Verificações de Consistência
- Os requisitos no documento não devem entrar em conflito.
- Não deve haver restrições contraditórias ou descrições diferentes para a mesma função do sistema.
- Exemplo: Se um requisito define que o sistema deve ter um botão "Salvar" em vermelho e outro requisito define que todos os botões de ação devem ser azuis, há uma inconsistência.

> [!TIP] DICAS: 
> - As verificações de consistência podem ser feitas por meio de revisão por pares (uma pessoa lê o texto de outra em busca de inconsistências) ou por meio de prototipação (para obter maior clareza).

### 1.3 Verificações de Completude
- O documento de requisitos deve incluir todos os requisitos que definem as funções e as restrições pretendidas pelo usuário.
- Exemplo: Se for fixado que o sistema deve gerar um relatório ao final do mês, o relatório deverá ser gerado ao final de TODO mês.

### 1.4 Verificações de Realismo
- Usando o conhecimento das tecnologias existentes, os requisitos devem ser verificados para assegurar que realmente podem ser implementados.
- Devem considerar o orçamento e o cronograma para o desenvolvimento do sistema.
- Exemplo: Um requisito que exige que o sistema funcione 24x7 (24 horas por dia, 7 dias por semana) foge da realidade, pois há a necessidade de realização de manutenção.

> [!CAUTION] OBSERVAÇÃO: 
> - Os requisitos não funcionais às vezes fogem da realidade.

### 1.5 Verificabilidade
- Para reduzir o potencial de conflito entre o cliente e o contratante, os requisitos devem ser passíveis de verificação.
- Significa que deve ser possível escrever um conjunto de testes que demonstrem que o sistema entregue atende a cada requisito especificado.

### 1.6 Adaptabilidade
- É a capacidade de um requisito sofrer alterações sem produzir efeitos em outros requisitos.
- Requisitos complexos podem afetar outros requisitos, indicando baixa adaptabilidade.

> [!CAUTION] OBSERVAÇÃO: 
> - A verificabilidade consiste na realização de um conjunto de testes dos requisitos.

## 2. Técnicas de Validação

### 2.1 Revisões de Requisitos
- Os requisitos são analisados sistematicamente por uma equipe de revisores.
- O objetivo é verificar erros e inconsistências.

### 2.2 Prototipação
- Um modelo executável do sistema é demonstrado para os usuários finais e clientes.
- Os usuários podem experimentar o modelo para verificar se ele atende a suas reais necessidades.

### 2.3 Geração de Casos de Teste
- Os requisitos devem ser testáveis.
- Se os testes forem concebidos como parte do processo de validação, isso frequentemente revela problemas de requisitos.
- Se é difícil ou impossível projetar um teste, significa que os requisitos serão difíceis de serem implementados e devem ser reconsiderados.

> [!TIP] DICAS: 
> - As principais técnicas de validação de requisitos são: Revisão de requisitos, Prototipação e Geração de casos de teste.
> - A Prototipação é uma técnica que pode ser utilizada tanto para descobrir quanto para validar requisitos.

## 3. Verificação versus Validação
- A verificação busca demonstrar que o sistema atende à sua especificação.
- A validação busca demonstrar que o sistema atende às necessidades do cliente.
- Ambos os processos envolvem a busca de erros na especificação ou de projeto.

> [!CAUTION] OBSERVAÇÃO: 
> - Para proceder a validação de requisitos, é necessário que se procure os erros na especificação.
> - Nos testes de software, por exemplo, são realizados os testes de defeito (testes para encontrar defeitos).