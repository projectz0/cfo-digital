# Changelog — CFO Digital

Histórico de versões do app. Cada versão é uma tag no git (`git tag`), marcando um ponto testado e funcionando — se algo quebrar depois, é pra essa marca que voltamos.

Formato: [semver](https://semver.org/lang/pt-BR/) — `MAIOR.MENOR.CORREÇÃO`. Aumenta MAIOR em mudanças grandes de arquitetura, MENOR a cada funcionalidade nova, CORREÇÃO a cada bugfix.

---

## [1.3.1] — 28/08/2026

### Adicionado
- Opção "⚠ Sem conta" no filtro de Conta — mostra despesas/receitas próprias sem conta vinculada, pra facilitar achar e completar o cadastro. Aparece sempre, independente do mês.

---

## [1.3.0] — 28/08/2026

### Modificado
- Filtro de Subcategoria na lista de lançamentos trocado por filtro de Conta (mesmo padrão do filtro de Cartão já existente) — mostra só as contas usadas no mês selecionado, filtra por conta debitada. Subcategoria era um texto livre pouco usado como filtro na prática; o campo continua existindo no formulário e na busca por texto, só perdeu o filtro dedicado na lista.

---

## [1.2.0] — 20/08/2026

### Adicionado
- Nova caixinha "Dívida de Terceiros" no formulário de despesa, ao lado de Parcelado/Recorrente — independente das duas (pode marcar junto, ex: conta recorrente paga por outra pessoa)
- Ao marcar, some o campo "Conta debitada" e aparece o campo com o nome do terceiro; meio de pagamento continua normal (cartão de crédito continua anexando a fatura)
- Menu lateral e cabeçalhos renomeados de "Terceiros" para "Dívida de Terceiros"

### Observação
- Mudança só de formulário/exibição — o dado salvo não muda, lançamentos existentes não são afetados (abrem com a caixinha pré-marcada corretamente ao editar)

---

## [1.1.0] — 20/08/2026

### Adicionado
- Ao marcar "Parcelado", o app agora pergunta se o valor digitado é o **total da compra** ou o **valor de cada parcela**, com prévia ao vivo (ex: "10x de R$100,00 = total de R$1.000,00")
- Checkboxes de Parcelado/Recorrente movidos para antes dos campos de Descrição/Valor no formulário — a decisão vem primeiro

### Corrigido
- Ambiguidade real que gerava parcelas com valor errado: o app sempre assumiu "valor = total da compra" sem deixar isso claro, então digitar o valor de cada parcela por engano gerava parcelas 10x (ou mais) menores que o esperado

### Removido
- Opção "Importar backup" do menu Ferramentas — sem validação dos dados importados, foi a porta de entrada de lançamentos não identificados investigados na v1.0.0. Função ainda existe no código, só sem entrada no menu

---

## [1.0.0] — 04/08/2026

Primeira versão marcada — ponto de partida do versionamento. Reúne tudo que foi construído e corrigido até aqui.

### Adicionado
- Central de alertas clicável (leva direto ao lançamento)
- Suporte a PWA — instalar como app no Android e iPhone (`manifest.json`, `sw.js`, ícones)
- Tutorial/guia dentro do próprio app (e-book em PDF + cards visuais), acessível na tela de login e em Ferramentas
- Geração automática de parcelas futuras faltantes ao editar um lançamento parcelado
- Botão de excluir lançamento na aba Terceiros
- Botão "Sair da Demonstração"
- Modo Demo agora pergunta: com dados de exemplo ou vazio (pra testar do zero)
- Submenu "Ferramentas" no menu lateral (organiza exportar, importar, versões, redefinir senha, zerar conta)
- "Esqueci minha senha" (e-mail) e "Redefinir senha" (dentro do app)
- Navegação rápida de mês na barra mobile, sincronizada com a aba Relatório
- Duplicar lançamento para o mês atual (antes só duplicava pro mês seguinte)

### Corrigido
- Conversão de despesa existente em parcelado não gerava as parcelas futuras
- Toast de confirmação bloqueava cliques físicos no rodapé da tela (invisível mas clicável por cima de outros botões)
- Vazamento de dados do Modo Demo para dentro de contas novas recém-criadas
- Vários modais (guia, formulário, categorias, escolha de fatura) ficavam escondidos atrás da tela de login ou de outro formulário (bug de `z-index`)
- Textos longos estourando a borda de botões em vários modais
- Edição em lote ("todas as parcelas") juntava séries de parcelas diferentes que só coincidiam em nome — corrigido pra usar só o `groupId` exato
- Card "Saldo Projetado" navegando para uma página inexistente
- Diversos bugs de layout mobile (menu, Relatório, modais)

### Removido temporariamente
- Opção "Importar OFX/OFC" do menu — tem bugs conhecidos, será reativada após correção

### Pendências conhecidas (não resolvidas nesta versão)
- ~66 lançamentos com IDs `tx001`–`tx0XX` na conta real, de origem não identificada (ver `PROJETO-CFO-DIGITAL.md`)
- Bugs da importação OFX/OFC ainda não corrigidos

---

## Como reverter para uma versão anterior

Peça pro Claude: **"volta pra versão X.Y.Z"** — ele restaura o `index.html`/`controle-financeiro.html` daquela tag e publica de novo. Leva menos de um minuto.
