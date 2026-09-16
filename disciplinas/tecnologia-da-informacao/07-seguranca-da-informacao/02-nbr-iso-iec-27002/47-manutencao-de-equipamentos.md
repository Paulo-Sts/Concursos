# Iso/Iec 27002:2022 - Controles Físicos VIII

## 1. Manutenção de Equipamentos 7.13
- Convém que os equipamentos sejam mantidos corretamente para assegurar a disponibilidade, integridade e confidencialidade da informação.
- O controle abrange a manutenção do equipamento como um todo, garantindo que esteja disponível e íntegro para as atividades, evitando acessos indevidos.
- Propósito: evitar perdas, danos, roubos ou comprometimento de informações e outros ativos, além de impedir a interrupção das operações por falta de manutenção.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade; Integridade; Disponibilidade | Proteger | Segurança física; Gestão de ativos | Proteção; Resiliência |

### 1.1 Diretrizes para Manutenção
- Realizar a manutenção de acordo com a frequência e especificações recomendadas pelo fornecedor.
- Implantar e monitorar um programa de manutenção próprio da organização.
- Permitir que apenas pessoal autorizado realize reparos e manutenção.
- Manter registros de todas as falhas, sejam elas suspeitas ou reais, e de toda manutenção preventiva ou corretiva.
- Implementar controles quando o equipamento for programado para manutenção, considerando se será realizada no local ou externamente.
- Fiscalizar o pessoal de manutenção durante a execução dos serviços no local.
- Autorizar e controlar rigorosamente o acesso para manutenção remota.
- Aplicar medidas de segurança para ativos que precisem ser retirados das dependências da organização para manutenção.
- Cumprir requisitos de manutenção impostos por apólices de seguro.
- Inspecionar o equipamento antes de reinseri-lo na operação para garantir que não houve adulteração.
- O conceito de equipamento inclui: instalações de processamento, UPS, baterias, geradores, sistemas de detecção de intrusão, extintores e ar-condicionado.

> [!CAUTION] OBSERVAÇÃO: 
> - A responsabilidade pela manutenção física não é do setor de TI; sua função é gerenciar e administrar o uso. Reparos em componentes eletrônicos (ex.: substituir HD) devem ser feitos exclusivamente por profissionais autorizados e preparados ⟶ suporte técnico do fornecedor.
> - Pessoal de manutenção externo deve estar condicionado a um acordo de confidencialidade adequado.

## 2. Descarte Seguro ou Reutilização de Equipamentos 7.14
- Convém verificar se itens de equipamentos que contêm mídia de armazenamento tiveram dados confidenciais e softwares licenciados removidos ou substituídos com segurança antes do descarte ou reutilização.
- Propósito: evitar o vazamento de informações por meio de equipamentos descartados ou reutilizados.

| TIPO DE CONTROLE | PROPRIEDADES DE SEGURANÇA DA INFORMAÇÃO | CONCEITOS DE SEGURANÇA CIBERNÉTICA | CAPACIDADES OPERACIONAIS | DOMÍNIOS DE SEGURANÇA |
|---|---|---|---|---|
| Preventivo | Confidencialidade | Proteger | Segurança física; Gestão de ativos | Segurança; Proteção |

### 2.1 Orientação para Descarte e Reutilização
- Verificar fisicamente se as mídias de armazenamento estão presentes no equipamento antes de processar o descarte.
- Mídias com informações confidenciais ou direitos autorais devem ser destruídas fisicamente ou ter os dados tornados irrecuperáveis por sobregravação.
- Remover rótulos e marcas que identifiquem a organização, proprietário ou sistema antes do descarte ou doação.
- Remover controles de segurança (listas de acesso) e equipamentos de vigilância ao fim de contratos de locação ou ao sair do controle da organização.
- Avaliar riscos em equipamentos danificados para decidir se devem ser destruídos fisicamente em vez de enviados para reparo.

### 2.2 Uso de Criptografia no Descarte
- A criptografia completa do disco (FDE) reduz o risco de divulgação de informações sensíveis no descarte, desde que atendidos critérios:
  - Processo de criptografia forte abrangendo todo o disco (incluindo espaço livre);
  - Chaves criptográficas longas para resistir a ataques de força bruta;
  - Chaves mantidas em sigilo e nunca armazenadas no mesmo disco.

> [!CAUTION] OBSERVAÇÃO: 
> - A exclusão simples (padrão do sistema) não é suficiente, pois permite a recuperação dos dados. É necessário formatar adequadamente ou usar técnicas como a desmagnetização ⟶ eliminação definitiva.
> - Equipamentos obsoletos podem ser doados para caridade ou outros órgãos públicos (especialmente os com menor orçamento), desde que removidos os dados e as licenças de software de uso permanente da organização.