# 💾 Segurança da Informação – Procedimentos de Backup

## 🧩 O que é backup?
- **Cópia de segurança** de dados importantes.
- Protege contra:
  - Falhas de hardware
  - Ataques cibernéticos
  - Corrupção ou perda de dados
- Pode ser feito em:
  - HD, SSD, fita, pendrive
  - Servidores (storages)
  - Nuvem

> ### 🧱 Tipos de backup

#### Backup completo (normal/total)
- Cópia de **todos os arquivos selecionados.**
- Marca os arquivos como copiados (atributo de arquivamento).
- **Base para outros backups** (incremental, diferencial).
- Mais lento para gravar, mas **rápido para restaurar.**

#### Backup de cópia
- Copia todos os arquivos selecionados.
- **Não desmarca o atributo de arquivamento.**
- Usado em **situações emergenciais**, fora da rotina.

#### Backup incremental
- Cópia apenas de **arquivos novos ou modificados** desde o último backup completo ou incremental.
- **Desmarca o atributo de arquivamento.**
- Mais rápido para fazer, mas **mais lento para restaurar** (exige todos os incrementais + o completo).

#### Backup diferencial
- Cópia de arquivos modificados desde o último backup completo.
- **Não desmarca o atributo de arquivamento.**
- Ocupa mais espaço que o incremental, mas **restauração é mais rápida** (usa apenas o último completo + o último diferencial).

#### Backup diário
- Cópia dos arquivos criados/modificados **no dia** ou em período definido.
- **Não desmarca atributo.**
- Não deve ser confundido com incremental/diferencial.

#### Backup espelhado (mirroring)
- **Sincronização em tempo real** com os dados de origem.
- Alteração em um lado afeta imediatamente o outro.
- **Não é proteção contra perda acidental ou vírus.**

> ### 🌐 Formas de backup por local

| TIPO    | LOCAL                           | CARACTERÍSTICAS                                             |
|---------|---------------------------------|-------------------------------------------------------------|
| Local   | Mesmo lugar dos dados originais | Rápido, mas **menos seguro**                                |
| Externo | Lugar físico diferente          | Mais seguro, precisa mover mídia                            |
| Remoto  | Feito via rede (online)         | Usa internet, está em outro servidor                        |
| Nuvem   | Armazenado em serviço de nuvem  | **Mais moderno**, automatizado, sem precisar de dispositivo |

#### 🔥 Backup online vs. offline
- **Online (quente):** sistema está em funcionamento (on-the-fly)
- **Offline (frio):** sistema parado para executar o backup

> ### ♻️ Restauração de backups

| TIPO        | COMO RESTAURAR                                      |
|-------------|-----------------------------------------------------|
| Completo    | Um único arquivo → restauração mais rápida          |
| Incremental | Backup completo + **todos os incrementais**         |
| Diferencial | Backup completo + **último diferencial apenas**     |
| Parcial     | Apenas arquivos específicos                         |
| Total       | Toda a base (completa + outros backups necessários) |

> ### ✅ Boas práticas de backup
- Fazer backups frequentes e automáticos.
- **Usar mais de um tipo** de armazenamento.
- Proteger os backups com criptografia e autenticação.
- Testar a restauração regularmente.
- Utilizar verificação em duas etapas em serviços de nuvem.
- Não copiar dados desnecessários.
- Usar storages ou sistemas confiáveis.


