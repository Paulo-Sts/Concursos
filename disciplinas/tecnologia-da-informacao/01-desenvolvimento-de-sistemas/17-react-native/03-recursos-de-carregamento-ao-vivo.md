# Recursos de Recarregamento e Componente Image

## 1. Recursos de Recarregamento ao Vivo (Hot, Live e Fast Refresh)

### 1.1 Definição
- Ferramentas de Desenvolvimento: permitem que os desenvolvedores visualizem as mudanças no código em tempo real, sem a necessidade de recompilar toda a aplicação manualmente.
- Objetivo: acelerar o ciclo de desenvolvimento e facilitar a identificação de erros.

### 1.2 Comparativo Detalhado: Hot Reloading vs. Live Reloading

| CARACTERÍSTICA | HOT RELOADING | LIVE RELOADING |
|----------------|---------------|----------------|
| Definição | Atualiza componentes específicos em tempo real, injetando as novas versões sem recarregar todo o aplicativo. | Recarrega a aplicação inteira sempre que um arquivo é salvo. |
| Estado da Aplicação | Mantém o estado atual dos componentes. (Ex: dados preenchidos em um formulário ou valor de um contador são preservados). | Reinicia/Perde o estado da aplicação a cada recarga. (Ex: contador volta a 0). |
| Velocidade | Rápido, pois recompila e substitui apenas os módulos modificados. | Mais lento, devido ao reboot completo da aplicação. |
| Uso Ideal | Ajustes finos na UI e lógica de um componente específico (ex: ajustar texto, cores ou estilos de um botão). | Alterações estruturais que envolvem múltiplos arquivos, configurações fundamentais ou adição de novas bibliotecas. |
| Acionamento | Manual (via menu de desenvolvimento ou atalhos de teclado). | Automático (ao salvar o arquivo). |

### 1.3 Fast Refresh (A Evolução)
- Definição: funcionalidade moderna que combina as melhores características do Hot Reloading e Live Reloading, resolvendo inconsistências dos métodos anteriores.
- Introdução: integrado por padrão no React Native a partir da versão 0.61 (2019).
- Característica Principal: automático (acionado ao salvar) e Preserva o Estado (mantém o estado dos componentes sempre que possível).
- Mecanismo: recarrega completamente um componente apenas quando sua estrutura é modificada de forma que não seja possível preservar o estado; caso contrário, apenas aplica a atualização rápida.

> [!TIP] DICA:
> - Hot Reloading: manual, preserva o estado.
> - Live Reloading: automático, perde o estado.
> - Fast Refresh: automático, preserva o estado (evolução, padrão desde 0.61).

## 2. Componente `<Image>`

### 2.1 Função e Sintaxe Básica
- Função: componente fundamental para exibir imagens (ícones, fotos, gráficos) no React Native.
- Propriedade Principal: `source` (Fonte).
- Tipos de Fonte Suportadas:
  1. Imagem de Rede (Remota): utiliza um objeto com a propriedade `uri`;
  2. Imagem Local (Estática): utiliza a função `require()` com o caminho relativo do arquivo.

| TIPO DE IMAGEM | SINTAXE | OBSERVAÇÃO |
|----------------|---------|------------|
| Rede (Remota) | `<Image source={{ uri: 'https://...' }} />` | Requer a definição de `width` e `height` no estilo. |
| Local (Estática) | `<Image source={require('./caminho/icon.png')} />` | O caminho é resolvido em tempo de compilação. |

### 2.2 Propriedade `resizeMode` (Redimensionamento)
- Função: controla como a imagem será ajustada ao espaço delimitado pelo componente (`style={{width: ..., height: ...}}`).

| VALOR | COMPORTAMENTO |
|-------|---------------|
| `cover` | Redimensiona para cobrir todo o espaço, mantendo a proporção. Pode cortar partes da imagem se necessário. |
| `contain` | Ajusta a imagem inteiramente dentro do espaço disponível, garantindo visibilidade total (sem cortes). Podem sobrar espaços vazios (bordas). |
| `stretch` | Estica a imagem para preencher completamente o espaço, distorcendo a proporção original. |
| `center` | Centraliza a imagem no espaço disponível sem redimensionar (mantém tamanho original). |
| `repeat` | Repete a imagem como um mosaico para cobrir o espaço. |

> [!TIP] DICA:
> - `cover` mantém a proporção, mas pode cortar a imagem.
> - `contain` mantém a proporção e mostra a imagem inteira, mas pode gerar espaços vazios.
> - `stretch` preenche tudo, mas distorce a imagem.