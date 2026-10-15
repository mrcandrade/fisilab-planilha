# Modificações feitas pelo FisiLab

O **Planilha** é uma versão modificada do [GridCraft](https://github.com/storytold/gridcraft)
(ArtCraft Team e contribuidores, MIT OR Apache-2.0), disponibilizada pelo FisiLab — LARFIC/UFRGS
em parceria com o CTA — Centro de Tecnologia Acadêmica como parte da Suíte FisiLab. Este arquivo
lista o que foi alterado em relação ao GridCraft 0.7.0 e por quê.

## O que mudou

### Nome e marca
- O nome visível do programa passou de "GridCraft" para **Planilha**: título da janela, nome
  do aplicativo, caixa "Sobre o Planilha", botão da guia Automatizar, mensagens de erro e de
  status, textos do canal de agentes/MCP, ajuda e versão da linha de comando, metadados gravados
  (produtor do PDF, `Application` do XLSX, `refreshedBy` das tabelas dinâmicas, `INFO("osversion")`,
  título do relatório do Solver, nome de usuário padrão) e os catálogos de tradução (chaves e
  valores atualizados juntos).
- Onde "Planilha" sozinho se confundiria com a palavra comum (metadados gravados nos arquivos,
  mensagens de erro do tipo "… can't open", títulos e descrições do servidor MCP), o programa é
  chamado de **FisiLab Planilha**. Título da janela, menus e caixa Sobre continuam "Planilha".
- **Motivo:** o NOTICE do GridCraft diz que o nome, a logomarca e os logotipos da ArtCraft são
  marcas registradas que não estão cobertas pela licença livre. Por isso a pasta `docs/brand/`
  (logotipos e marca nominativa da ArtCraft) foi apagada, e a interface não exibe mais nenhuma
  marca da ArtCraft. O crédito em texto ao GridCraft e ao ArtCraft Team foi mantido (e ampliado).
- Novo ícone do aplicativo em `assets/fisilab/` (janela, barra de tarefas e recurso do `.exe`).

### Executáveis e identificadores
- Os executáveis passaram a se chamar `fisilab-planilha(.exe)` e `fisilab-planilha-cli(.exe)`
  (seções `[[bin]]`); os pacotes Rust continuam `gridcraft` e `gridcraft-cli`.
- O app id passou de `ai.storyteller.gridcraft` para `br.ufrgs.fisilab.planilha`, e a pasta
  de configurações (preferências e logs) passou a ser `%APPDATA%\FisiLab Planilha` (Windows),
  `~/Library/Application Support/FisiLab Planilha` (macOS) e `~/.config/fisilab-planilha` (Linux), para
  não se misturar com uma instalação do GridCraft.
- Recursos do Windows (`apps/gridcraft/build.rs`): ícone, ProductName, FileDescription,
  CompanyName, LegalCopyright, OriginalFilename e InternalName do Planilha.
- O filtro de log padrão inclui o alvo `fisilab_planilha` (o binário passou a se chamar
  `fisilab-planilha`, e o Rust usa `fisilab_planilha` como alvo dos logs).

### Identidade visual da Suíte FisiLab
- Novo crate `crates/fisilab-brand` (comum a toda a suíte): tela de abertura com a logo do CTA e
  a janela "Sobre a Suíte FisiLab".
- Paleta original do GridCraft, sem alterações. Os temas original claro e escuro aparecem como
  **Noite** (escuro) e **Dia** (claro), primeiros da lista (Exibir ▸ Tema, Arquivo ▸ Opções e menu
  do macOS), seguidos de "Sistema". O tema padrão é o do GridCraft (claro, ou o do sistema na
  primeira abertura). O comando `view.theme` também aceita `noite`/`dia` (e `night`/`day`).
- Português do Brasil na primeira abertura (definido no aplicativo desktop; a biblioteca mantém o
  padrão original).
- Tela de abertura animada com a logo do CTA ao iniciar o programa.
- Item "Sobre a Suíte FisiLab…" na guia Automatizar (ao lado de "Sobre o Planilha"), na caixa
  Sobre e no menu Ajuda do macOS.

### Links
- Os links "GridCraft on getartcraft.com" e "Join the ArtCraft Discord" (caixa Sobre, menu Ajuda do
  macOS, instalador e metadados do Linux) foram trocados por: "Site da Suíte FisiLab",
  "Manifesto pelas tecnologias livres", "Projeto original (GridCraft)" e "Reportar um problema"
  (`https://github.com/mrcandrade/fisilab-planilha/issues`).
- O GridCraft não tem verificação de atualização, telemetria nem envio de relatórios de falha;
  nada disso precisou ser desligado.

### Idioma
- Numa instalação nova o idioma da interface é o **português do Brasil** (antes seguia o idioma do
  sistema). A escolha feita pelo usuário continua sendo salva e respeitada.

### Empacotamento e repositório
- `packaging/windows/gridcraft.wxs` e `package.ps1`: nomes, executáveis, ícone, textos em
  português, novo UpgradeCode e ProgIds `FisiLab.Planilha.*` (o instalador oficial da suíte é
  feito com Inno Setup pelo FisiLab). O MSI instala em `Program Files\Suite FisiLab\Planilha`,
  grava suas chaves em `HKLM\Software\FisiLab\Planilha` e se registra em
  `RegisteredApplications` como `FisiLab.Planilha`.
- A pasta `.github/` (CI, releases e financiamento do projeto original) foi apagada, para que esses
  fluxos não rodem contra este fork.
- `README.md` novo, em português; o README original está em `README.upstream.md`. `NOTICE` ganhou
  um cabeçalho do Planilha, com o texto original logo abaixo.

## O que não mudou
- O motor de planilha, os formatos de arquivo (`.xlsx`, `.xls`, `.csv`, …, inclusive o formato
  JSON interno), os comandos, os ids de comando, o protocolo de controle e o servidor MCP (que
  continua se identificando como `gridcraft` para os clientes).
- Os nomes dos crates e módulos Rust, as variáveis de ambiente (`GRIDCRAFT_*`), os comentários do
  código e a documentação técnica em `docs/` (histórico do projeto original).
- As licenças (`LICENSE-MIT`, `LICENSE-APACHE`) e o `ATTRIBUTION.md` do projeto original.
- O aplicativo web (`apps/gridcraft-web`) só teve o nome visível trocado.

## Segurança e privacidade
- O salvamento automático (que sobrescreve o `.xlsx` aberto, sem cópia de segurança) já vem
  desativado em uma instalação nova (`GridState::default`); só é ativado se o usuário ligar a opção
  em Arquivo › Opções › Salvar ou o botão "Salvamento Automático" da barra de título. A opção não é
  gravada entre sessões, então o aplicativo sempre abre com ele desligado. Foi apenas documentado no
  código e coberto por um teste (`autosave_is_off_by_default_and_can_be_toggled`).
