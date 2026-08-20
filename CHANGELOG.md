# Changelog — CFO Digital

Histórico de versões do app. Cada versão é uma tag no git (`git tag`), marcando um ponto testado e funcionando — se algo quebrar depois, é pra essa marca que voltamos.

Formato: [semver](https://semver.org/lang/pt-BR/) — `MAIOR.MENOR.CORREÇÃO`. Aumenta MAIOR em mudanças grandes de arquitetura, MENOR a cada funcionalidade nova, CORREÇÃO a cada bugfix.

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
