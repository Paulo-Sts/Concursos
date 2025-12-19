# Windows 11 – Explorador de Arquivos e OneDrive

## 1. Explorador de Arquivos

#### 1.1 Estrutura e Seções Principais
- Acesso Rápido: exibe pastas e arquivos recentes.
- Este Computador: unidades de disco locais, removíveis e de rede.
- Bibliotecas: visualização virtual que agrupa arquivos de pastas diferentes em um único local.
- Rede: dispositivos e computadores compartilhados na rede.

#### 1.2 Funcionalidades
- Navegação hierárquica (pastas e subpastas).
- Barra de endereços para navegação direta.
- Botão direito em "Este Computador" oferece:
  - Gerenciamento do Computador
  - Mapear/desconectar unidade de rede
  - Propriedades do sistema
- Botão direito em unidades de disco permite:
  - Formatar
  - Ejetar (unidades removíveis)
  - Renomear
  - Abrir em nova guia/janela
  - Fixar no Acesso Rápido

#### 1.3 Bibliotecas
- Recurso de visualização virtual (não move arquivos fisicamente).
- Permite criar novas bibliotecas e incluir pastas.
- Pasta de salvamento: arquivos arrastados para a biblioteca são movidos para essa pasta.
- Excluir um arquivo da biblioteca o exclui da pasta de origem.

#### 1.4 Teclas de Atalho
- `F1`: Ajuda
- `F2`: Renomear
- `F3`, `Ctrl+E`, `Ctrl+F`: Pesquisar
- `F4`: Foca na barra de endereços
- `F5`: Atualizar
- `F11`: Tela inteira
- `Ctrl+A`: Selecionar tudo
- `Ctrl+N`: Nova janela
- `Ctrl+Shift+N`: Nova pasta
- `Ctrl+W` ou `Alt+F4`: Fechar janela

#### 1.5 Caracteres Proibidos em Nomes de Arquivos
- Aspas (`"`)
- Asterisco (`*`)
- Interrogação (`?`)
- Dois-pontos (`:`)
- Menor (`<`) e Maior (`>`)
- Barra normal (`/`), vertical (`|`) e invertida (`\`)

## 2. OneDrive

#### 2.1 Características
- Serviço de armazenamento em nuvem da Microsoft.
- Integrado nativamente ao Windows e ao Explorador de Arquivos.
- Sincronização de arquivos entre dispositivos.

#### 2.2 Status dos Arquivos no Explorador
- Disponível quando online: arquivo só está na nuvem.
- Sincronização pendente: aguardando sincronização.
- Disponível neste dispositivo: arquivo sincronizado localmente.
- Sempre disponível neste dispositivo: arquivo mantido localmente mesmo se excluído na nuvem.
- OneDrive precisa de sua atenção: erro de sincronização requer ação do usuário.

#### 2.3 Status do Serviço (Área de Notificações)
- Atualizado
- Processando alterações
- Em pausa
- Problemas de sincronização

#### 2.4 Configurações do OneDrive
- Backup automático de pastas (Área de Trabalho, Documentos, Imagens).
- Salvamento automático de fotos e capturas de tela.
- Pausa de sincronização em modo de economia de bateria ou rede limitada.
- Cofre pessoal: pasta protegida por autenticação adicional.

#### 2.5 Resolução de Conflitos
- Ocorre quando múltiplos usuários editam o mesmo arquivo.
- Opções: manter versão local, versão da nuvem ou ambas.

## 3. Utilitários de Disco

#### 3.1 Desfragmentar e Otimizar
- Reorganiza arquivos para melhor performance (HDD).
- Pouco efetivo em SSDs (reduz vida útil).
- Pode ser agendado.

#### 3.2 Limpeza de Disco
- Exclui arquivos temporários, cache, relatórios de erro.
- Libera espaço em disco.

## 4. Windows Defender Firewall
- Firewall nativo do Windows.
- Bloqueia acessos não autorizados a programas e portas.
- Regras de entrada e saída; padrão é bloquear tudo.

## 5. Conexão de Área de Trabalho Remota
- Acesso remoto a outro computador via protocolo RDP.
- Requer nome do computador e credenciais.
- Configurável em qualidade de imagem e desempenho.