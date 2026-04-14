# LEGO SVG README Experiment 🧱

Este repositório testa se é possível criar um layout de **LEGO** no GitHub usando múltiplos SVGs individuais colados sem espaços, mantendo cada um clicável.

## O Teste (Sem Tabela)

Nesta versão, as imagens são colocadas lado a lado sem nenhum espaço entre os links no Markdown.

<div align="center">
<a href="https://github.com/red"><img src="assets/red_1x1.svg" width="100" height="100" align="top" alt="Red"></a><a href="https://github.com/blue"><img src="assets/blue_1x1.svg" width="100" height="100" align="top" alt="Blue"></a><a href="https://github.com/blue"><img src="assets/blue_1x1.svg" width="100" height="100" align="top" alt="Blue"></a><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" height="100" align="top" alt="White"></a><br><a href="https://github.com/green"><img src="assets/green_1x1.svg" width="100" height="100" align="top" alt="Green"></a><a href="https://github.com/yellow"><img src="assets/yellow_1x1.svg" width="100" height="100" align="top" alt="Yellow"></a><a href="https://github.com/yellow"><img src="assets/yellow_1x1.svg" width="100" height="100" align="top" alt="Yellow"></a><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" height="100" align="top" alt="White"></a><br><a href="https://github.com/green"><img src="assets/green_1x1.svg" width="100" height="100" align="top" alt="Green"></a><a href="https://github.com/yellow"><img src="assets/yellow_1x1.svg" width="100" height="100" align="top" alt="Yellow"></a><a href="https://github.com/yellow"><img src="assets/yellow_1x1.svg" width="100" height="100" align="top" alt="Yellow"></a><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" height="100" align="top" alt="White"></a><br><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" height="100" align="top" alt="White"></a><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" height="100" align="top" alt="White"></a><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" height="100" align="top" alt="White"></a><a href="https://github.com/red"><img src="assets/red_1x1.svg" width="100" height="100" align="top" alt="Red"></a>
</div>

## Teste de Conexão (Tiling)

Abaixo, quatro blocos iguais de estrelas são colocados lado a lado para mostrar como os desenhos nas bordas se conectam perfeitamente.

<div align="center">
<a href="#"><img src="assets/star_brick.svg" width="100" height="100" align="top"></a><a href="#"><img src="assets/star_brick.svg" width="100" height="100" align="top"></a><a href="#"><img src="assets/star_brick.svg" width="100" height="100" align="top"></a><a href="#"><img src="assets/star_brick.svg" width="100" height="100" align="top"></a>
</div>

---

### Como funciona?
1. **Zero Whitespace**: Os links `<a>` estão colados um no outro no código Markdown.
2. **Full Bleed SVGs**: Os arquivos removem qualquer borda interna, preenchendo os 100x100 pixels completamente.
3. **Pedaços 1x1**: Para garantir alinhamento perfeito sem tabelas, peças maiores (como a 2x2 amarela) são formadas por múltiplos blocos 1x1.
4. **Attribute Animation**: Usamos SMIL no atributo `x` para animações em loop resilientes ao cache do GitHub.

---

📖 **Quer saber como chegamos aqui?** Confira a [LORE.md](./LORE.md) para ver todo o processo de desenvolvimento e os desafios superados.
