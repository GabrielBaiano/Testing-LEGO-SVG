# LEGO SVG README Experiment 🧱

Este repositório é um teste para verificar se é possível criar um layout tipo **LEGO** no GitHub usando múltiplos SVGs individuais que se encaixam, mantendo cada um clicável.

## O Teste

Cada "peça" abaixo é um arquivo SVG individual na pasta `assets/`. Elas foram organizadas em uma tabela para formar um bloco coeso.

<div align="center">

<table border="0" cellpadding="0" cellspacing="0">
  <tr>
    <td><a href="https://github.com/red"><img src="assets/red_1x1.svg" width="100" alt="Red 1x1"></a></td>
    <td colspan="2"><a href="https://github.com/blue"><img src="assets/blue_2x1.svg" width="200" height="100" alt="Blue 2x1"></a></td>
    <td><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" alt="White Filler"></a></td>
  </tr>
  <tr>
    <td rowspan="2"><a href="https://github.com/green"><img src="assets/green_1x2.svg" width="100" height="200" alt="Green 1x2"></a></td>
    <td colspan="2" rowspan="2"><a href="https://github.com/yellow"><img src="assets/yellow_2x2.svg" width="200" height="200" alt="Yellow 2x2"></a></td>
    <td><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" alt="White Filler"></a></td>
  </tr>
  <tr>
    <td><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" alt="White Filler"></a></td>
  </tr>
  <tr>
    <td><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" alt="White Filler"></a></td>
    <td><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" alt="White Filler"></a></td>
    <td><a href="https://github.com/white"><img src="assets/white_1x1.svg" width="100" alt="White Filler"></a></td>
    <td><a href="https://github.com/red"><img src="assets/red_1x1.svg" width="100" alt="Red 1x1"></a></td>
  </tr>
</table>

</div>

> [!TIP]
> Em muitos ambientes de Markdown (como GitHub), tabelas HTML sem bordas são a melhor forma de criar layouts complexos mantendo a interatividade individual de cada imagem.

---

### Como funciona?
1. **Peças Modulares**: Cada SVG tem um tamanho fixo (ex: 100x100 para 1x1).
2. **Preenchimento**: Quadrados brancos (`white_1x1.svg`) são usados para completar o retângulo e manter a estrutura visual.
3. **Clique Individual**: Cada `<img>` está envolto em um `<a>`, permitindo links diferentes para cada peça.
