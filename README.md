<p align="center">
  <img src="assets/fisilab/fisilab-planilha-256.png" alt="Ícone do Planilha" width="128">
</p>

<h1 align="center">Planilha · Suíte FisiLab</h1>

<p align="center">
  <b>Planilhas</b><br>
  Alternativa livre ao <b>Microsoft Excel</b>
</p>

<p align="center">
  Disponibilizado pelo <b>FisiLab — LARFIC · UFRGS</b> em parceria com o <b>CTA — Centro de
  Tecnologia Acadêmica</b>, para estudantes, professores e técnicos da UFRGS.
</p>

---

## O que faz

- **Interface conhecida:** faixa de opções (ribbon), barra de fórmulas, Caixa de Nome, abas de
  planilha, atalhos de teclado, alça de preenchimento, Formatar Células, Colar Especial,
  formatação condicional, tabelas e gráficos, como em uma planilha de escritório comum.
- **Compatível com XLSX:** o formato nativo é o `.xlsx`; estilos, temas, fórmulas (inclusive
  matrizes dinâmicas), tabelas, validação, comentários, hiperlinks, gráficos, imagens,
  minigráficos, tabelas dinâmicas e configurações de impressão são preservados. Também lê e grava
  CSV e TSV, abre pastas de trabalho `.xls` (Excel 97-2003) com valores, fórmulas e formatos de
  número, e importa os dados de arquivos XLSB e ODS.
- **Motor de cálculo completo:** grafo de dependências com recálculo incremental e matrizes
  dinâmicas, mais de 500 funções de planilha, além de LET, LAMBDA, MAP, REDUCE, SCAN, BYROW,
  BYCOL e MAKEARRAY, referências estruturadas a tabelas e a linguagem completa de formatos de
  número.
- **Análise de dados:** classificação e AutoFiltro, Preenchimento Relâmpago, validação de dados,
  estrutura de tópicos e subtotais, tabelas dinâmicas com lista de campos, filtros e agrupamento
  por data.
- **Gráficos e impressão:** dezessete tipos de gráfico com guia Design do Gráfico e painel de
  formatação, Visualização de Quebra de Página, configurações de impressão, exportação para PDF e
  impressão.
- **Rápido:** pastas de trabalho com cópia na escrita (desfazer quase sem custo) e uma grade
  virtualizada que só desenha o que está na tela.
- **Automatizável:** cada botão, item de menu, caixa de diálogo e gesto é um comando que pode ser
  executado por um canal de controle JSON, por um servidor **MCP** ou pela linha de comando
  (`fisilab-planilha-cli`).
- **Sem assinatura:** sem servidor de licenças e sem telemetria. A interface está disponível em
  português do Brasil (na primeira abertura) e em outros idiomas, com a paleta original do
  GridCraft e os temas **Noite** (escuro) e **Dia** (claro).

## Instalação

### Windows

Baixe o instalador `FisiLab-Planilha-Setup-<versão>.exe` no portal de downloads da
[Suíte FisiLab](https://github.com/mrcandrade/larfic/tree/main/suite-fisilab) ou na página de
[Releases do Planilha](https://github.com/mrcandrade/fisilab-planilha/releases) e execute-o.

### Compilar a partir do código

É preciso ter o [Rust](https://rustup.rs) instalado (no Windows, com as Build Tools do Visual
Studio).

```sh
cargo run --release -p gridcraft                          # aplicativo (fisilab-planilha)
cargo run --release -p gridcraft -- --sample sales        # abre um exemplo (sales, budget, grades)
cargo run --release -p gridcraft -- planilha.xlsx         # abre uma pasta de trabalho
cargo build --release -p gridcraft -p gridcraft-cli       # gera fisilab-planilha e fisilab-planilha-cli em target/release
```

Os pacotes Rust mantêm os nomes do projeto original (`gridcraft`, `gridcraft-cli`); os executáveis
gerados se chamam `fisilab-planilha` e `fisilab-planilha-cli`.

## Créditos

O Planilha é baseado no [GridCraft](https://github.com/storytold/gridcraft), criado pelo
ArtCraft Team e pelos contribuidores do GridCraft. Todo o trabalho da planilha, dos formatos de
arquivo e das ferramentas é deles; o FisiLab alterou o nome, a identidade visual, o tema de cores,
a tela de abertura, os links e o instalador (veja [MODIFICACOES.md](MODIFICACOES.md)).

O código é distribuído sob a licença MIT ou Apache 2.0, à escolha de quem o usa
([LICENSE-MIT](LICENSE-MIT), [LICENSE-APACHE](LICENSE-APACHE)). Consulte também
[NOTICE](NOTICE), [ATTRIBUTION.md](ATTRIBUTION.md) e o README original em
[README.upstream.md](README.upstream.md).

Os nomes e marcas do projeto original pertencem aos seus titulares; esta versão não é afiliada nem
endossada por eles.

## Manifesto

Conhecimento produzido em uma universidade pública deve circular livremente, e as ferramentas que
usamos para ensinar, pesquisar e criar também: leia o
[Manifesto pelas tecnologias livres](https://github.com/mrcandrade/larfic/blob/main/suite-fisilab/MANIFESTO.md).

---

<p align="center">
  <a href="https://www.ufrgs.br"><img src="assets/fisilab/ufrgs-logo.gif" alt="UFRGS" height="48"></a>
  &nbsp;&nbsp;&nbsp;
  <a href="https://cta.if.ufrgs.br"><img src="assets/fisilab/cta-logo.webp" alt="CTA — Centro de Tecnologia Acadêmica" height="48"></a>
  &nbsp;&nbsp;&nbsp;
  <img src="assets/fisilab/larfic-logo.png" alt="FisiLab — LARFIC" height="48">
</p>

<p align="center"><sub>FisiLab — LARFIC · UFRGS, em parceria com o CTA — Centro de Tecnologia Acadêmica.</sub></p>
