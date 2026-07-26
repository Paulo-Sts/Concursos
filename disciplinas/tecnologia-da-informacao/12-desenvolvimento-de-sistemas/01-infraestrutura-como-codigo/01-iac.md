# Infraestrutura como Código (IaC) – Introdução e Conceitos

## 1. Definição e Conceitos-Chave

### 1.1 O que é IaC
- Infraestrutura como Código (IaC) é o gerenciamento e provisionamento da infraestrutura por meio de códigos legíveis por máquinas (arquivos de configuração, scripts), em vez de processos manuais e interativos.
- O objetivo é substituir a intervenção manual na configuração de servidores, redes e sistemas, passando a usar código para automatizar todo o ciclo de vida da infraestrutura.

### 1.2 Conceitos-Chave Associados

| CONCEITO | DESCRIÇÃO |
|----------|-----------|
| Automatização | Eliminação de processos manuais repetitivos. |
| Escalabilidade | Capacidade de provisionar e gerenciar recursos em larga escala de forma programática. |
| Consistência (Coesão) | Garantia de que a infraestrutura será provisionada de forma idêntica em todos os ambientes (desenvolvimento, teste, produção). |
| Provisionamento | Processo de criação e configuração inicial da infraestrutura. |
| Gerenciamento de Configuração | Processo de manutenção da infraestrutura no estado desejado após o provisionamento inicial, aplicando atualizações e correções. |

## 2. Provisionamento e Gerenciamento

### 2.1 Tipos de Provisionamento

| TIPO | DESCRIÇÃO |
|------|-----------|
| Servidores | Configuração de hardware físico ou virtual, instalação de SO e aplicações. |
| Nuvem | Criação da infraestrutura subjacente no ambiente de nuvem (redes, serviços). |
| Usuários | Gerenciamento de identidades e concessão de permissões a serviços. |
| Redes | Configuração de roteadores, switches, firewalls e alocação de IPs. |
| Serviços | Configuração de serviços de TI para usuários finais. |

### 2.2 Gerenciamento de Configuração
- É o processo de definir e manter a configuração desejada da infraestrutura.
- Exemplos de tarefas: corrigir erros, aplicar patches de segurança, atualizar versões de software, modificar conteúdos.
- Ferramentas populares: Ansible, Puppet, Chef.

## 3. Vantagens da IaC

| VANTAGEM | DESCRIÇÃO |
|----------|-----------|
| Aumento da velocidade | Implantações mais rápidas. |
| Redução de erros | Minimização de erros humanos. |
| Consistência | Garantida pela idempotência. |
| Redução de custos | Diminuição de custos operacionais. |
| Prevenção de desvios | Prevenção de configuration drift. |

## 4. Infraestrutura Imutável vs. Mutável

### 4.1 Infraestrutura Imutável
- Conceito: uma vez provisionada, a infraestrutura não pode ser alterada.
- Processo de Atualização: para aplicar uma mudança, a versão antiga é eliminada e substituída por uma nova versão com a configuração desejada.
- Vantagem: alta confiabilidade e estabilidade, pois o estado é sempre conhecido e pode ser facilmente recriado.

### 4.2 Infraestrutura Mutável
- Conceito: a infraestrutura pode ser alterada após provisionada.
- Processo de Atualização: as mudanças são aplicadas diretamente no recurso existente, modificando-o e atualizando-o.
- Desvantagem: a mutabilidade pode prejudicar a consistência e dificultar o versionamento.

### 4.3 Comparativo

| ASPECTO | IMUTÁVEL | MUTÁVEL |
|---------|----------|---------|
| Alteração após provisionamento | Não permite | Permite |
| Processo de atualização | Elimina e substitui | Modifica diretamente o recurso existente |
| Vantagem | Alta confiabilidade e estabilidade | Flexibilidade |
| Desvantagem | Requer recriação para mudanças | Pode gerar desvios de configuração |

### 4.4 Aplicação em IaC
- Muitas implantações de IaC são projetadas para serem imutáveis, pois este modelo garante maior confiabilidade e facilita a reversão de versões.

## 5. Abordagens de IaC: Imperativa vs. Declarativa

### 5.1 Abordagem Imperativa
- Definição: define os comandos específicos (o "COMO") que devem ser executados passo a passo para alcançar o estado desejado.
- Característica: é como um script de procedimentos. Pode ser mais fácil de entender para administradores tradicionais, mas gera mais trabalho para gerenciar a escalabilidade.

### 5.2 Abordagem Declarativa
- Definição: define o estado final desejado do sistema (o "O QUÊ"), e a ferramenta de IaC se encarrega de descobrir como alcançá-lo.
- Característica: foca no resultado, não nos passos. Requer um administrador mais qualificado para gerenciá-la, mas é mais adequada para infraestruturas complexas e em larga escala.

### 5.3 Comparativo

| ASPECTO | IMPERATIVA | DECLARATIVA |
|---------|------------|-------------|
| Foco | No processo (o "COMO") | No resultado (o "O QUÊ") |
| Funcionamento | Define comandos específicos passo a passo | Define o estado final desejado |
| Complexidade | Mais fácil para administradores tradicionais | Requer administrador mais qualificado |
| Escalabilidade | Mais trabalhosa para gerenciar | Mais adequada para infraestruturas complexas |

## 6. Versionamento da Infraestrutura
- Definição: aplicar sistemas de controle de versão (como Git) aos arquivos de código da infraestrutura.
- Benefícios:
  - Permitir a reversão para versões anteriores em caso de problemas;
  - Facilitar a correção de erros de forma controlada;
  - Manter um histórico detalhado de todas as mudanças.