# A Lore do LEGO SVG 🧱

Este arquivo documenta a jornada técnica para fazer um README do GitHub parecer um brinquedo de montar.

## 📜 A Jornada

### 1. O Conceito Inicial
A ideia era usar a modularidade do SVG para criar componentes que, quando empilhados, formariam uma interface coesa, mas mantendo a capacidade de clicar em cada peça individualmente.

### 2. A Falha das Tabelas
Nossa primeira tentativa usou tabelas HTML (`<table>`). Embora as tabelas permitam `colspan` e `rowspan` (perfeito para peças 2x1 ou 2x2), o GitHub aplica paddings, bordas e estilos padrão que criavam "buracos" entre as peças. O resultado parecia um grid de dashboard, não um LEGO.

### 3. A Luta Contra o Whitespace
Decidimos remover a tabela e colocar as imagens lado a lado no Markdown. Descobrimos que qualquer espaço ou quebra de linha no código gerava um gap horizontal. Ao "colar" as tags `<a>` uma na outra, resolvemos o alinhamento lateral.

### 4. O Mistério do Gap Vertical
Mesmo coladas horizontalmente, as linhas do nosso LEGO tinham uma separação preta (o fundo do GitHub). Isso acontecia porque o navegador trata as imagens como elementos *inline*, reservando espaço abaixo delas para as "pernas" das letras (descendentes).

### 5. O Golpe Final: `align="top"`
A solução definitiva veio ao adicionar o atributo `align="top"` em cada tag `<img>`. Isso forçou o navegador a alinhar as imagens pelo topo, eliminando o espaço reservado para texto abaixo delas e colando as linhas verticalmente.

## 🛠️ Tecnologias Utilizadas
- **SVG 1.1**: Para os blocos "full-bleed" de 100x100 pixels.
- **GFM (GitHub Flavored Markdown)**: Usando comportamento de renderização de imagens inline.
- **Zero Whitespace**: Técnica de codificação para evitar gaps de renderização.

---
*Documentado por Antigravity (IA).*
