# A Lore do LEGO SVG 🧱

Este arquivo documenta a jornada técnica e os desafios superados para transformar o README do GitHub em uma interface modular de blocos.

---

## 🚀 Fase 1: O Conceito de Tabela (O Erro)

Nossa primeira ideia foi usar tabelas HTML padrão. Parecia lógico para alinhar blocos.

**O Código:**
```html
<table>
  <tr>
    <td><img src="red.svg"></td>
    <td><img src="blue.svg"></td>
  </tr>
</table>
```

**O Resultado Visual:**
- O GitHub adiciona **paddings** automáticos dentro de cada célula (`<td>`).
- Aparecem **bordas cinzas** indesejadas dependendo do tema.
- **Veredito:** Ficava parecendo uma planilha Excel, não um LEGO. As peças não se tocavam.

---

## 📐 Fase 2: O Alinhamento Inline (O Quase)

Tentamos colocar as peças uma ao lado da outra, removendo a tabela.

**O Código (Com erro de whitespace):**
```markdown
<a href="#"><img src="red.svg"></a>
<a href="#"><img src="blue.svg"></a>
```

**O Problema do Whitespace:**
O Markdown interpreta a quebra de linha entre os links como um espaço vazio. Isso criava um gap vertical entre as peças.

**A Solução Horizontal:**
Colar as tags no código:
```markdown
<a href="#"><img src="red.svg"></a><a href="#"><img src="blue.svg"></a>
```
*Isso resolveu o alinhamento de lado, mas as linhas ainda tinham fendas pretas entre elas.*

---

## 🎨 Fase 3: O Mistério do Gap Vertical (A Solução)

Mesmo colando as imagens horizontalmente, existia um espaço de ~4px entre a Row 1 e a Row 2. Isso acontece porque imagens são elementos `inline` e o navegador reserva espaço para a "cauda" das letras (como p, q, y).

**O Código Com Erro:**
```html
<a href="#"><img src="brick.svg" width="100"></a><br>
<a href="#"><img src="brick.svg" width="100"></a>
```

**A Solução: `align="top"`**
Ao usar o atributo `align="top"`, forçamos a imagem a ignorar a linha de base do texto e se alinhar perfeitamente ao topo da linha.

**O Código Final:**
```html
<a href="#"><img src="red.svg" width="100" align="top"></a><br>
<a href="#"><img src="blue.svg" width="100" align="top"></a>
```

---

## 🧱 Fase 4: Full Bleed SVG

Para que o LEGO funcione, a peça não pode ter margens internas (padding) dentro do próprio arquivo SVG.

**Errado (SVG com margem):**
```xml
<rect x="5" y="5" width="90" height="90" ... /> <!-- Deixa 5px de gap -->
```

**Correto (Full Bleed):**
```xml
<rect x="0" y="0" width="100" height="100" ... /> <!-- Preenchimento total -->
```

---

## 🏆 Resultado Final
Ao combinar **Zero Whitespace** + **Full Bleed SVGs** + **align="top"**, conseguimos um bloco onde cada peça é individual e clicável, mas visualmente parecem uma única estrutura.

---
*Documentado por Antigravity (IA).*
