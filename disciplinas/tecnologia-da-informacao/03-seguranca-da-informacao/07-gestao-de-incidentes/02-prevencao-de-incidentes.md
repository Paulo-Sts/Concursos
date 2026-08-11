# Prevenção de Acidentes

## 1. Políticas e Procedimentos de Segurança
- A primeira estratégia para prevenir incidentes é o estabelecimento de procedimentos e políticas de segurança da informação.
- O processo de definição de normas está presente em três níveis dentro do órgão:
  - Estratégico: compreende as grandes metas e objetivos estratégicos da segurança da informação, culminando em uma política de segurança da informação;
  - Tático: trata-se de políticas complementares (normas), como metas para a segurança da informação;
  - Operacional: diz respeito aos procedimentos operacionais.
- Políticas bem-definidas previnem acidentes de segurança, pois as instruções são responsáveis por definir o processo.
- A política de segurança está no alto nível da pirâmide, seguida pelas normas e, por fim, pelos procedimentos operacionais.
- A política de segurança não tem o mesmo nível de detalhamento dos procedimentos.

### 1.1 Hierarquia das Normas de Segurança
- Política de segurança: alto nível estratégico, define diretrizes gerais.
- Normas: nível tático, estabelecem metas e regras complementares.
- Procedimentos operacionais: nível operacional, detalham a execução prática das atividades.

## 2. Controle de Acesso
- O controle de acesso pode ser realizado em diferentes níveis:
  - Controle físico: utilização de identificação biométrica para acessar áreas restritas;
  - Controle de software: login e senha;
  - Controle de dados/informações: bases de dados acessíveis apenas por pessoas específicas.
- De maneira geral, controle de acesso é uma forma de prevenção de incidentes de segurança da informação.

### 2.1 Princípio do Privilégio Mínimo
- As políticas de controle de acesso devem ser fechadas: somente os acessos especificamente autorizados são permitidos.
- Garante que os usuários tenham apenas o acesso de que realmente precisam.
- É a política mais utilizada para controle de acesso.
- A Lei de Acesso à Informação tem lógica inversa: todo arquivo é público, exceto os definidos como restritos.

## 3. Firewall e Segurança de Rede
- O firewall (literalmente "parede de fogo") evita que pacotes indesejados, com conteúdo malicioso, ultrapassem a barreira entre a rede externa (internet) e a rede interna.
- Filtros de pacotes tradicionais são considerados firewall porque podem executar uma política de filtragem com base na combinação de endereços e números de porta.
- Examinam cada datagrama e determinam, a partir de regras específicas, se ele deve passar ou ficar.

> [!TIP] DICAS:
> - O firewall atua como barreira entre a rede interna e externa, bloqueando pacotes maliciosos.

## 4. Softwares de Segurança (Antivírus)
- O antivírus é uma prática efetiva de prevenção, mas não protege contra botnets.
- O antivírus atua contra malwares em geral.
- Impede que o computador se torne um "zumbi" em uma botnet, impedindo a instalação do vírus na rede.

> [!CAUTION] OBSERVAÇÃO:
> - O antivírus não impede que "zumbis" de fora ataquem a rede; ele apenas previne a infecção local.

## 5. Intrusion Prevention System (IPS)
- O IPS (Sistema de Prevenção de Intrusões) pode estar localizado na linha de frente, entre a internet e o firewall, ou após o firewall.
- É um sistema pró-ativo, ou seja, atua diretamente no elemento invasor, não apenas emite um alerta.
- Pode trabalhar por meio de assinatura de arquivos ou por análise de comportamento da rede.

## 6. Intrusion Detection System (IDS)
- O IDS (Sistema de Detecção de Intrusões) apenas emite um alerta a respeito do invasor, não atua na resolução do problema.
- Normalmente, localiza-se antes do firewall.
- Pode ser usado para detectar varreduras de porta e de pilha TCP, além de ataques de DoS, de inundação de largura de banda, de worms e de vírus.
- Pode trabalhar por meio de assinatura de arquivos ou por análise de comportamento da rede.

### 6.1 Comparação entre IPS e IDS
| CARACTERÍSTICA | IPS | IDS |
|----------------|-----|-----|
| Função principal | Previne e bloqueia ataques | Detecta e alerta sobre ataques |
| Ação | Proativa (age diretamente) | Reativa (apenas emite alerta) |
| Localização típica | Entre a internet e o firewall ou após o firewall | Antes do firewall |
| Tipo de atuação | Atua sobre o invasor | Não atua, apenas informa |

## 7. User and Entity Behavior Analytics (UEBA)
- O UEBA é uma estratégia de prevenção de incidentes que usa aprendizado de máquina (machine learning).
- Os dados de rede coletados passam pelo machine learning, que classifica os comportamentos suspeitos.

## 8. Análise de Tráfego de Rede
- Faz a captura de pacotes de internet que estão trafegando pela rede.
- Lista informações sobre os pacotes em busca de comportamentos anômalos.

## 9. Análise de Logs
- Normalmente, trata-se de uma análise automatizada.

## 10. Replicação e Backup de Dados
- Replicação de dados é a solução utilizada quando há bancos de dados da organização distribuídos pelo mundo.
- Em vez de fazer um backup tradicional, faz-se a replicação do arquivo em três nós distintos.
- Se um nó cair, ainda há outros dois contendo o arquivo.

## 11. Controle de Spam
- O spam traz consigo arquivos maliciosos.
- O controle de spam é uma forma de prevenir incidentes.
- Pode ser realizado através de listas:
  - Blacklist (lista negra): remetentes não confiáveis;
  - Whitelist (lista branca): remetentes confiáveis.

### 11.1 Comparação entre Blacklist e Whitelist
| BLACKLIST | WHITELIST |
|-----------|-----------|
| Bloqueia remetentes não confiáveis | Permite acesso apenas de remetentes cadastrados |
| Processo mais simples e comum | Processo mais custoso |
| Impede a entrada de executáveis não cadastrados | Lista de e-mails, domínios ou IP previamente aprovados |
| Normalmente não submetidos aos filtros | Normalmente não submetidos aos filtros |

> [!CAUTION] OBSERVAÇÃO:
> - A implantação de whitelist é um processo mais custoso que a blacklist.
> - Com a implementação do whitelisting, impossibilita-se a entrada de qualquer executável que não esteja cadastrado.

## 12. Honeypot
- O honeypot (literalmente "pote de mel") atua atraindo pacotes malignos que tenham conseguido passar pelo firewall e chegar à rede interna.
- Trata-se de uma vulnerabilidade conhecida, incluída no sistema para atrair invasores.
- Permite coletar informações sobre o invasor e eliminá-lo antes que ele atinja o sistema de fato.
- Pode ser utilizado para atingir os objetivos de:
  - Atrair um atacante potencial;
  - Afastá-lo de sistemas críticos;
  - Incentivar o atacante a ficar no sistema por tempo suficiente para que haja resposta dos administradores;
  - Coletar informações sobre a atividade do atacante (foram projetados para esse fim).

> [!TIP] DICAS:
> - Honeypots atraem atacantes, afastam de sistemas críticos e permitem análise das atividades dos invasores.

## 13. Gerenciamento de Privilégios Administrativos
- O princípio do privilégio mínimo norteia o gerenciamento de privilégios administrativos.
- Políticas de controle de acesso devem ser fechadas: somente os acessos especificamente autorizados são permitidos.

## 14. Atualização de Sistemas (Patches)
- Uma das formas de barrar ataques às vulnerabilidades de sistemas é aplicar rotineiramente os patches disponibilizados pelos fabricantes de software.
- Todo sistema de segurança deve ser atualizado com frequência.
- O patch de correção corrige bugs identificados ao longo do uso do sistema.
- Pode acontecer de, no momento da construção do patch, por um descuido, a pessoa adicionar alguma alteração no código que gera um problema não mapeado.
- Ao aplicar o patch de correção, a ferramenta pode deixar de funcionar, causando novos erros em outras funções.

## 15. Tratamento de Incidentes
- A detecção de um incidente de segurança computacional pode ser feita por:
  - Ferramentas automáticas (alertas e alarmes);
  - Denúncias;
  - Avaliação feita por analista de segurança.
- A detecção de incidentes não se restringe apenas a ferramentas automáticas.
- O incidente de segurança de rede não precisa ser necessariamente confirmado.
- O simples fato de observar o risco de que o incidente aconteceu ou detectar um pretenso incidente é motivo para executar o protocolo de tratamento.
- A mudança de políticas de segurança influencia a identificação da ocorrência de incidentes em redes de computadores.
- Um processo de triagem de incidentes faz uma avaliação rápida dos incidentes, inclusive para confirmá-los.

### 15.1 Resposta a Ataques de DoS (Denial of Service)
- No caso de um ataque de DoS a uma rede de computadores, é mais indicado como resposta reconfigurar o roteador para minimizar efeitos de flooding.
- A reconfiguração de roteadores é mais eficaz do que a duplicação de arquivos para investigação forense.
- O ataque de DoS muitas vezes parte de robôs.
- Para evitar esse tipo de invasão por bots, utiliza-se o CAPTCHA.