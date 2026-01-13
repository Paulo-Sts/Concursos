# Memória Primária

## 1. Definição e Hierarquia de Memórias
- A memória é um dispositivo que permite ao computador armazenar dados. A hierarquia de memórias, do mais rápido para o mais lento (e do mais caro/capacidade menor para o mais barato/capacidade maior), é:
  - Registradores
  - Memória Cache
  - Memória Principal (RAM)
  - Memória Secundária (HD, SSD, etc.)

#### Relações Importantes
- Velocidade e custo são diretamente proporcionais.
- Velocidade e capacidade são inversamente proporcionais.

## 2. Memória Primária
- São memórias que o processador pode endereçar diretamente, essenciais para o funcionamento do computador. 
- São voláteis, exceto a ROM. 
- Incluem:
  - Registradores
  - Memória Cache
  - Memória RAM
  - Memória ROM

## 3. Tipos de Memória Primária

#### 3.1 Registradores
- Memória mais rápida e cara do computador.
- Localizada dentro da CPU (processador).
- Tipos de registradores de propósito específico:
  - Program Counter (PC): Contador de Programas.
  - Instruction Register (IR): Registrador de Instrução.
  - Memory Address Register (MAR): Registrador de Endereço.
  - Memory Buffer Register (MBR): Registrador de Dados.

#### 3.2 Memória Cache
- Memória intermediária de acesso rápido entre a CPU e a RAM.
- Objetivo: obter velocidade próxima da dos registradores com custo mais baixo.
- Dividida em níveis (L1, L2, L3, L4) para atender à demanda de velocidade. L1 é a mais rápida e menor, ficando dentro do processador.

#### 3.3 Memória RAM (Random Access Memory)
- Memória de acesso aleatório, principal do computador.
- Volátil: perde dados ao ser desligada.
- Usada para armazenar arquivos e programas em processamento.
- Capacidade típica: de 2 GB a 32 GB.
- Tipos/tecnologias: SIMM, DIMM, DDR, DDR2, DDR3, DDR4, DDR5.
- Memória Virtual: quando a RAM fica sem espaço, o sistema operacional usa parte do HD ou SSD como extensão (RAM virtual).

#### 3.4 Memória ROM (Read-Only Memory)
- Memória somente de leitura, não volátil (dados não se perdem ao desligar).
- Gravada pelo fabricante, geralmente não pode ser alterada.
- Armazena o firmware (software básico do hardware).
- Tipos de ROM:
  - ROM: gravada uma vez, não regravável.
  - PROM: memória virgem, gravada uma vez pelo usuário.
  - EPROM: pode ser apagada (com luz ultravioleta) e regravada.
  - EEPROM: pode ser apagada e regravada eletricamente (origem da memória Flash).

## 4. Firmware e Programas da ROM
- Conjunto de instruções operacionais programadas diretamente no hardware. Armazenado em ROM, PROM, EPROM, EEPROM ou Flash.

#### 4.1 BIOS (Basic Input/Output System)
- Programa pré-gravado em ROM.
- Responsável pelo suporte básico ao hardware e pelo início da carga do sistema operacional (boot).
- Primeiro software executado ao ligar o computador.
- Atualmente, está sendo substituído pelo UEFI (mais moderno).

#### 4.2 POST (Power-On Self-Test)
- Sequência de testes ao hardware realizada pelo BIOS ao ligar.
- Verifica se o sistema está operacional.

#### 4.3 Setup
- Programa para alterar parâmetros de configuração do sistema.
- Os parâmetros são armazenados na memória CMOS (volátil, mas mantida por uma bateria).
- Acesso via teclas (como F2 ou Del) durante o boot.

## 5. Memória CMOS
- Memória RAM volátil especial que armazena configurações do Setup (data, hora, configurações de boot).
- Mantida por uma bateria na placa-mãe para não perder dados ao desligar.

## 6. Características-Chave
- Voláteis: Registradores, Cache, RAM, CMOS.
- Não Voláteis: ROM, PROM, EPROM, EEPROM, Flash, memória secundária (HD, SSD).
- Memória mais importante para execução de programas: RAM.
- Tecnologias DDR (DDR, DDR2, DDR3, DDR4, DDR5) referem-se à memória RAM.
- A ordem de velocidade (mais rápida para mais lenta) é: Cache da CPU > RAM > SSD (memória secundária).