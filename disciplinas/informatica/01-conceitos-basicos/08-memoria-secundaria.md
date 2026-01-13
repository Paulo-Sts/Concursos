# Memória Secundária

## 1. Definição e Características
- São memórias não voláteis (mantêm os dados mesmo sem energia).
- Também chamadas de armazenamento em massa ou memória de armazenamento permanente.
- Exemplos: HDD, SSD, SSHD, pendrive, cartão de memória, CD, DVD, Blu-ray, fita magnética.

## 2. Tipos de Memória Secundária

#### 2.1 HDD (Hard Disk Drive) – Disco Rígido Magnético
- Utiliza discos magnéticos e partes móveis (braço mecânico).
- Formatação Física: feita na fábrica; divide o disco em trilhas, setores e cilindros; isola bad blocks.
- Formatação Lógica: define o sistema de arquivos; pode ser refeita.
- Sistemas de arquivos comuns:
  - Windows: FAT16, FAT32, NTFS, exFAT.
  - Linux: Ext2, Ext3, Ext4, ReiserFS, entre outros.
- Limitação do FAT32: arquivos máximos de 4 GB; partição máxima de 8 GB (na prática, 2 TB).
- Capacidade típica: 320 GB a 8 TB.
- Interfaces de conexão: IDE/PATA (antiga), SATA (atual mais comum), SCSI, SAS, USB, eSATA.

#### 2.2 SSD (Solid State Drive) – Disco de Estado Sólido
- Sem partes móveis; usa memória flash (semelhante a pendrives).
- Mais rápido, silencioso e com menor consumo de energia que o HDD.
- Mais caro por GB.
- Interfaces:
  - SATA: mais comum, mas limita velocidade.
  - NVMe: usa soquetes PCIe; velocidade superior ao SATA.
- Vida útil: geralmente menor que a do HDD (ciclos de gravação limitados), mas mais resistente a impactos.

#### 2.3 SSHD (Solid State Hybrid Drive) – Disco Híbrido
- Combina tecnologias SSD (para velocidade) e HDD (para capacidade maior a custo menor).
- Objetivo: equilibrar desempenho e custo.

#### 2.4 Memória Flash
- Tecnologia de armazenamento não volátil e regravável.
- Usada em: SSDs, pendrives, cartões de memória (SD, Memory Stick), armazenamento interno de celulares e câmeras.
- Pendrive (Memória USB Flash Drive): usa memória flash; capacidade até 1 TB.

#### 2.5 Memória Terciária
- Memória secundária que precisa de um drive (leitor) específico para acesso.
- Exemplos: CD, DVD, Blu-ray, disquetes, fitas magnéticas.

#### 2.6 Mídias Ópticas
- CD (Compact Disc):
  - CD-ROM: somente leitura.
  - CD-R: gravável uma vez.
  - CD-RW: regravável.
  - Capacidade: 650 MB a 700 MB.
- DVD (Digital Versatile Disc):
  - Maior capacidade que o CD.
  - Capacidade: 4,7 GB (um lado) até 8,5 GB (dois lados).
- Blu-ray (BD):
  - Para vídeo de alta definição e armazenamento de alta densidade.
  - Capacidade: 25 GB (camada simples) a 50 GB (camada dupla).
- HD DVD: formato concorrente ao Blu-ray; capacidade de 15 GB a 30 GB (não se popularizou).

#### 2.7 Mídias Magnéticas Removíveis (Antigas)
- Disquete (Floppy Disk): 1,44 MB (3,5 polegadas).
- Zip Drive: 100 MB a 750 MB.
- Jaz Drive: 1 GB a 2 GB.
- Fita Magnética (DLT/DAT): usada para backup; capacidade de 20 GB a 220 TB.

## 3. Comparativo Rápido

| DISPOSITIVO     | TECNOLOGIA         | VOLÁTIL? | PARTES MÓVEIS? | VELOCIDADE  | CAPACIDADE TÍPICA |
|-----------------|--------------------|----------|----------------|-------------|-------------------|
| HDD             | Magnética          | Não      | Sim            | Mais lento  | 320 GB – 8 TB     |
| SSD             | Flash (eletrônica) | Não      | Não            | Mais rápido | 120 GB – 4 TB     |
| SSHD            | Híbrida            | Não      | Sim (parcial)  | Interm.     | 500 GB – 2 TB     |
| Pendrive/Cartão | Flash              | Não      | Não            | Rápido      | 8 GB – 1 TB       |
| CD/DVD/Blu-ray  | Óptica             | Não      | Não (no disco) | Lento       | 700 MB – 50 GB    |
| Fita Magnética  | Magnética          | Não      | Sim            | Muito lento | 20 GB – 220 TB    |

## 4. Dicas Importantes
- NVMe é a interface mais rápida para SSDs atualmente.
- SSD é considerado um dispositivo de armazenamento eletrônico (sem partes mecânicas).
- HDD é magnético e tem partes móveis.
- Unidade de disco no Windows pode ser classificada como:
  - Fixa (HD interno, SSD interno).
  - Removível (pendrive, HD externo, cartão de memória).
  - Unidade de rede (compartilhamento na rede).
- Blu-ray foi desenvolvido para vídeo de alta definição, não para substituir HDDs como armazenamento principal.
- A expansão da memória RAM melhora o desempenho na execução simultânea de programas; a memória secundária (HD/SSD) armazena os dados permanentemente.