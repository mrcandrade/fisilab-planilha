# Janela do DMG (macOS)

Dois arquivos prontos, copiados por `package.sh` para dentro da imagem; nada aqui é gerado durante a compilação.

| Arquivo | O que é |
|---|---|
| `background.tiff` | Fundo da janela do Finder (HiDPI, 1x e 2x). Vai para `.background/background.tiff`. |
| `dmg-layout.DS_Store` | Ajustes de visualização do Finder (tamanho da janela, posição dos ícones, fundo). Vai para `.DS_Store`. |

Ambos vêm de `suite-fisilab/scripts/gerar_mac.py`, no repositório
[mrcandrade/larfic](https://github.com/mrcandrade/larfic). Para alterá-los, gere-os de novo lá.

Nomes que o layout espera (não mude sem gerar de novo):

- nome do volume: `Planilha` (sem versão);
- aplicativo: `Planilha.app`;
- atalho para a pasta de programas: `Aplicativos`.
