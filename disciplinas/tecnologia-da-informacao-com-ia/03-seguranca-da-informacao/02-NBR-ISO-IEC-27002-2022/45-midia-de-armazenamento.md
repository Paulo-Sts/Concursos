# ISO/IEC 27002:2022 - Controles Físicos VI

## 1. Mídia de Armazenamento

### 1.1 Controle
- As mídias de armazenamento devem ser gerenciadas por seu ciclo de vida de aquisição, uso, transporte e descarte, de acordo com o esquema de classificação e com os requisitos de manuseio da organização.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade; Integridade; Disponibilidade | Proteger | Segurança física; Gestão de ativos | Proteção |

### 1.2 Propósito
- Assegurar a divulgação, modificação, remoção ou destruição de informações apenas de forma autorizada sobre as mídias de armazenamento.
- O ciclo de vida da mídia abrange desde a aquisição, uso e transporte até o descarte.
- Inclui-se a eliminação definitiva dos dados contidos na mídia, garantindo que não haja mais possibilidade de utilização.
- Devem ser observadas as legislações ambientais pertinentes para o descarte adequado das mídias.
- Cada mídia deve conter dados classificados conforme o sistema de classificação definido pela organização.
- Qualquer procedimento de divulgação, modificação, remoção ou destruição deve ocorrer apenas mediante autorização prévia.

> [!TIP] DICAS:
> - O controle é classificado como preventivo, atuando nas propriedades de confidencialidade, integridade e disponibilidade.
> - O propósito principal é garantir que todas as ações sobre as mídias sejam autorizadas.

## 2 Orientação para Mídia de Armazenamento Removível
- Devem ser consideradas as seguintes diretrizes para o gerenciamento de mídias de armazenamento removíveis:
  a) Estabelecer uma política específica sobre o gerenciamento de mídia de armazenamento removível e comunicar essa política a qualquer pessoa que use ou manuseie esse tipo de mídia;
  b) Quando necessário e possível, exigir autorização para que os meios de armazenamento sejam removidos da organização e manter um registro dessas remoções, a fim de manter uma trilha de auditoria;
  c) Armazenar todas as mídias de armazenamento em um ambiente seguro e protegido de acordo com a classificação de suas informações e protegê-las contra ameaças ambientais (como calor, umidade, campo eletrônico ou envelhecimento), de acordo com as especificações dos fabricantes;
  d) Usar técnicas criptográficas para proteger informações nas mídias de armazenamento removíveis, se a confidencialidade ou a integridade das informações forem considerações importantes;
  e) Mitigar o risco de degradação de mídia de armazenamento, enquanto as informações armazenadas ainda forem necessárias, transferindo os dados para novas mídias antes que se tornem ilegíveis;
  f) Armazenar múltiplas cópias de informações de grande valor, em mídias de armazenamento separadas, para reduzir ainda mais o risco de dano ou perda de informações coincidentes;
  g) Considerar o registro das mídias de armazenamento removível para limitar a chance de perda de informações;
  h) Somente habilitar as portas de mídia de armazenamento removíveis (por exemplo, slots de cartão SD e portas USB) se houver uma razão organizacional para seu uso;
  i) Monitorar a transferência de informações para mídia de armazenamento removível, onde houver a necessidade de usar tais meios de armazenamento;
  j) Informações podem ser vulneráveis a acesso não autorizado, uso indevido ou alteração indevida durante o transporte físico, por exemplo, ao enviar mídia de armazenamento pelos serviços postais ou por mensageiros.

> [!TIP] DICAS:
> - A remoção de mídias da organização exige autorização formal e registro para trilha de auditoria (item b).
> - Criptografia deve ser usada quando confidencialidade ou integridade forem relevantes (item d).
> - Múltiplas cópias de informações de grande valor devem ser armazenadas em mídias separadas (item f).

> [!CAUTION] OBSERVAÇÃO:
> - Considera-se inadequado armazenar uma cópia de segurança no mesmo local físico do original, pois isso não configura um backup efetivo.
> - A probabilidade de ocorrência de um problema que afete ambas as mídias no mesmo local é elevada.
> - Os backups devem ser mantidos em local geograficamente distante para garantir a preservação das informações.
> - Neste controle, a mídia inclui documentos em papel.
> - Ao transferir a mídia de armazenamento físico, aplicar as medidas de segurança de 5.14.

## 3 Orientação para Reutilização ou Descarte Seguro
- Os procedimentos para a reutilização ou descarte seguro de mídia de armazenamento devem ser estabelecidos para minimizar o risco de vazamento de informações confidenciais a pessoas não autorizadas.
- Os procedimentos de reutilização ou descarte seguro devem ser proporcionais à sensibilidade das informações contidas.

> [!CAUTION] OBSERVAÇÃO:
> - O nível de segurança aplicado a uma mídia deve ser proporcional à sensibilidade do seu conteúdo.
> - Informações classificadas como de alto sigilo demandam medidas de proteção mais rigorosas.
> - Conteúdos de conhecimento público ou com sigilo ostensivo não requerem o mesmo nível de custódia.
> - É necessário dosar e aplicar as medidas de segurança de acordo com a criticidade da informação.

### 3.1 Itens a serem considerados
- a) Se as mídias de armazenamento contendo informações confidenciais precisarem ser reutilizadas dentro da organização, excluir os dados com segurança ou formatar a mídia antes de reutilizá-la (ver 8.10);
- b) Descartar de forma segura a mídia de armazenamento contendo informações confidenciais, quando não forem mais necessárias (por exemplo, destruindo, triturando ou excluindo o conteúdo com segurança);
- c) Ter procedimentos implementados para identificar os itens que podem exigir descarte seguro;
- d) Muitas organizações oferecem serviços de coleta e descarte para mídia de armazenamento;
- e) Registrar o descarte de itens sensíveis, a fim de manter uma trilha de auditoria;
- f) Ao acumular mídia de armazenamento para descarte, considerar o efeito de agregação, que pode fazer com que uma grande quantidade de informações não sensíveis se torne sensível.

> [!CAUTION] OBSERVAÇÃO:
> - Convém tomar o devido cuidado na seleção de um fornecedor externo apropriado com controles e experiência adequados.
> - Um processo de avaliação de risco deve ser realizado em dispositivos danificados contendo dados sensíveis, para determinar se convém que os itens sejam fisicamente destruídos em vez de enviados para reparo ou descartados (ver 7.14).

> [!TIP] DICAS:
> - A reutilização exige exclusão segura ou formatação prévia.
> - O descarte deve ser seguro e proporcional à sensibilidade da informação.
> - Registro do descarte é obrigatório para manter trilha de auditoria.
> - O efeito de agregação pode tornar informações não sensíveis em sensíveis quando acumuladas.

## 4. Outras Informações
- Quando as informações confidenciais na mídia de armazenamento não forem criptografadas, considerar proteção física adicional na mídia de armazenamento.

> [!CAUTION] OBSERVAÇÃO:
> - Recomenda-se a utilização de criptografia na mídia de backup, uma vez que essa tecnologia se encontra amplamente disponível nos dispositivos atuais.
> - Conforme orienta a norma, deve-se considerar a implementação de proteção física adicional para essas mídias, pois essa medida compensa a ausência de proteção lógica.