# Organização e Gerenciamento de Arquivos, Pastas e Programas  

## Gerenciadores de arquivos  
- Utilitários que permitem acesso, manipulação e organização de arquivos/pastas.  
- Principais gerenciadores:  
  - **Windows:** Explorador de Arquivos (antigo Windows Explorer)  
  - **Linux:** Konqueror, Dolphin, Nautilus  
  - **macOS:** Finder  

## Estrutura hierárquica de pastas  
- Raiz:  
  - **Windows:** `C:\`  
  - **Linux:** `/`  
- Regras:  
  - Não pode haver arquivos/subpastas com nomes iguais no mesmo diretório.  
  - **Caracteres proibidos no Windows:** `" * ? : < > / | \`  
- Diferenças Windows/Linux:  
  - **Case sensitivity:** Linux diferencia maiúsculas/minúsculas; Windows não.  
  - **Barras:** Windows usa `\`; Linux usa `/`.  

## Operações com arquivos/pastas  

### Copiar/mover/atalhos  
- **Mesma unidade (C:\):**  
  - Arrastar sem tecla → **Move**  
  - Arrastar + **CTRL** → **Copia**  
  - Arrastar + **ALT** ou **CTRL+SHIFT** → **Cria atalho**  
- **Unidades diferentes (C:\ → D:\):**  
  - Arrastar sem tecla → **Copia**  
  - Arrastar + **SHIFT** → **Move**  

### Exclusão de arquivos  
- **Enviar para lixeira:**  
  1. Arrastar para lixeira  
  2. Botão direito → Excluir  
  3. Tecla `DELETE` ou `CTRL+D`  
- **Exclusão permanente (3 casos):**  
  1. Arquivos em pen drives  
  2. Arquivos em rede  
  3. Lixeira cheia  
  **Atalho:** `SHIFT + DELETE`  

## Propriedades de arquivos/pastas  
- **Acessar:** Botão direito → **Propriedades**  
- **Informações exibidas:**  
  - Nome, extensão, tamanho  
  - Datas (criação, modificação, último acesso)  
  - Atributos ("Somente leitura", "Oculto")  

## Extensões de arquivos  

| TIPO        | EXTENSÕES                       |  
|-------------|---------------------------------|  
| Documentos  | .docx, .xlsx, .pptx, .pdf, .txt |  
| Imagens     | .jpg, .png, .gif                |  
| Vídeos      | .mp4, .avi, .wmv                |  
| Compactados | .zip, .rar, .7z                 |  
| Executáveis | .exe (Windows), .sh (Linux)     |  

## Compactação de arquivos  
- **Objetivo:** Reduzir tamanho sem perda de dados.  
- **Formatos:** .zip (Windows nativo), .rar, .7z  
- **Observações:**  
  - Arquivos de texto compactam melhor que imagens/vídeos.  
  - **≠ Criptografia:** Compactação não protege dados.  