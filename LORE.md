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

## ⚡ Fase 5: Animação em Loop (O Truque Final)

Para dar vida ao nosso LEGO, adicionamos movimento. O desafio era fazer o padrão de estrelas "andar" para a direita sem quebras visíveis.

**A Técnica: O "Treadmill" (Esteira)**
1. Criamos um grupo `<g>` com duas cópias do padrão lado a lado (uma em `x=0` e outra em `x=-100`).
2. Animamos esse grupo para se mover de `0` até `100`.
3. Como o padrão se repete perfeitamente a cada 100px, o reset da animação é imperceptível.

**O Código (CSS):**
```xml
<style>
  @keyframes treadmill {
    from { transform: translateX(0); }
    to { transform: translateX(100px); }
  }
  .star-group {
    animation: treadmill 3s linear infinite;
  }
</style>
<g class="star-group">
  <use href="#pattern" x="0" />
  <use href="#pattern" x="-100" />
</g>
```
> [!NOTE]
> Usamos animação via **CSS (`<style>`)** em vez de SMIL (`<animateTransform>`) porque o GitHub tem maior compatibilidade com CSS dentro de SVGs renderizados via tag `<img>`.

---

## 🛠️ Fase 6: A Resiliência do SMIL (Atributo `x`)

Descobrimos que tanto a animação de grupo (`<g>`) quanto o CSS (`<style>`) podem ser instáveis no GitHub devido ao proxy **Camo**. A forma mais robusta de animar é atacar diretamente o atributo `x` dos elementos.

**O Truque de Compatibilidade:**
Em vez de mover um contêiner, animamos o valor de `x` de cada cópia do padrão individualmente. Isso usa o SMIL mais básico possível, que raramente é bloqueado.

**O Código Final (Ultra-Compatível):**
```xml
<use href="#star-pattern" x="0">
  <animate attributeName="x" from="0" to="100" dur="3s" repeatCount="indefinite" />
</use>
<use href="#star-pattern" x="-100">
  <animate attributeName="x" from="-100" to="0" dur="3s" repeatCount="indefinite" />
</use>
```

---

## 🏆 Resultado Final
Ao combinar **Zero Whitespace** + **Full Bleed SVGs** + **align="top"** + **Attribute-based SMIL**, conseguimos uma interface que é ao mesmo tempo modular, clicável e animada de forma resiliente no GitHub.

---
*Documentado por Antigravity (IA).*
---

### Fase 7: O Pivot para "Peças Únicas" (Profile Card)
Ao tentar reproduzir layouts complexos de texto e imagem (como o Profile Card), descobrimos que o método de pequenos quadradinhos individuais é extremamente instável devido ao comportamento "inline" do GitHub.
- **Solução:** Para componentes de texto, usamos um SVG único que encapsula todo o layout interno (imagem, nome, bio). Isso garante fidelidade de 100% e elimina fendas.
- **LEGO Tower:** Snapamos o grid de apps diretamente abaixo desse card usando a técnica de zero-whitespace, criando uma estrutura vertical coesa.

### Fase 8: Herança Visual e Transparência
Descobrimos que ícones com cantos arredondados precisam de um fundo sólido (branco) dentro do próprio SVG se forem usados em grids que não permitem transparência perfeita sem artefatos.
- **Aprimoramento:** Adicionado `<rect fill="white">` em todos os ícones para garantir integração total com o fundo do GitHub e as `white_tiles`.
### Phase 10: O Triunfo do Fatiamento (LEGO Slices)
Para componentes que precisam ser "rodeados" por outros blocos menores sem o uso de tabelas (que inserem padding indesejado no GitHub):
- **A Solução:** Fatiar o componente grande (ex: 400x300) em tiras horizontais que coincidam com a altura do grid (ex: 3 tiras de 100px de altura).
- **Vantagem:** Essas tiras se comportam como "super-blocos" que permitem que o Markdown envolva o componente com blocos menores (os quadradinhos de estrela) de forma fluida e sem quebras.
