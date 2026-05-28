# GarageSpot — Documentação do Projeto

> **REGRA DE VERSIONAMENTO — IMPORTANTE**
> `v2.0` está **RESERVADA** para a futura migração com banco de dados e servidor externo.
> Toda atualização atual deve usar numeração abaixo de v2.0:
> `v1.9.3 → v1.9.4 → v1.9.5 ... v1.9.99` (subdivisões: v1.9.3.1, v1.9.3.2 etc.)
> **NÃO** pular para v2.0 antes da migração DB/servidor.
>
> **⚠️ APK BUILD — IMPORTANTE**
> NÃO buildar APK em versões puramente HTML/CSS/JS. O `GarageSpot-dev.apk` já é
> online via `server.url` e atualiza automaticamente do `garagespot-dev`.
> Buildar APK APENAS quando mexer em `capacitor.config.json`, plugin Capacitor,
> permissões Android, ou ao gerar release final para o hotel (offline, sem
> `server.url`). Ver `DEPLOY.md` para o protocolo completo.

## Visão Geral
Aplicativo de controle de garagem para hotel, desenvolvido como WebApp empacotado em APK Android via Capacitor.

**Desenvolvido por:** Douglas Nascimento  
**Hotel:** Hotel Gumz  
**App ID:** com.apollods.garagespot

---

## Versões

| Versão | Arquivo | Principais funcionalidades |
|--------|---------|---------------------------|
| v1.0 | garagespot-17.html | Mapa de vagas, check-in/out, passeio, merge vertical/horizontal, drag & drop, PDF/registro, kill switch |
| v1.1 | garagespot-18.html | Usuários com expediente, histórico com responsável, botão histórico (ℹ️), número de hospedagem GS001, compartilhar PDF |
| v1.2 | garagespot-19.html | Renomeação de vagas (mirror flip A/B/C), navbar 3 botões, Painel do Dia, Gestão com PIN, Busca rápida, Indicador plantão, Turnos, Relatórios, checkout auto-share, fotos auto-renomeadas |
| v1.3 | garagespot-20.html | PIN padrão 1200, alterarPIN 3 etapas, Gestão pede PIN toda vez, historico para todas as ações de vaga (movimentacao_vaga/tornar_grande/tornar_pequeno/merge_lateral/desfaz_merge_lateral), botões ← Voltar + ✕ Fechar no histórico modal, cancelamento compartilhar não abre documento, botão ✕ Fechar fixo no documento, fmtNomeArquivo com DD-MM-AA "a" formato, buildRegistroHTML cabeçalho 2 colunas, relatórios redesenhados (Movimentações/Ocupação/Por apartamento) com date pickers e Compartilhar, pilares bugfix setTimeout, remove × apagar/restaurar da barra de passeio, versionCode 3 |
| v1.4 | www/index.html | gerarECompartilharPDF() genérica (todos docs = PDF), busca rápida roxa (pulse 3×, setas ←→, contador), topbar portrait corrigida (labels ocultos, tb-right flex-shrink:0), setinha ▾/▴ oculta/exibe painel passeio E navbar, checkout pergunta "Deseja compartilhar?", relatórios compartilhados como PDF (buildRelMovimentacoesHTML/buildRelOcupacaoHTML/buildRelPorAptoHTML), versionCode 4 |
| v1.5 | www/index.html | Bug fixes: desfazHMerge() antes de mover carro, direita/esquerda corrigido nas vagas B; segundo veículo mesmo apt (identificador obrigatório, GS separado); Relatório por Turno (date pickers + checkboxes + PDF); Plantão Manual (add/remove, localStorage, auto-clear meia-noite); UX: toast retorno passeio, badge ⏱ tempo no passeio, sort recente/antigo, tamanho de fonte (Gestão → Exibição); jsPDF 2.5.1 + JSZip 3.10.1 embutidos; Sistema de Recarga (vagas 8C/9C/1D, estados visuais, fila, alertas, PDF); versionCode 5 |
| v1.6 | www/index.html | Módulos ativos (toggles ⚡ Recarga / 📋 Vistorias em Gestão → Configurações do Sistema); backup local auto (visibilitychange + manual em Gestão → Backup e Conexões); loadRecargas() no init; renderTelaVistorias stub; VISTORIAS declarado; versionCode 6 |
| v1.7 | www/index.html (garagespot-21.html) | Sistema de Vistoria completo (VIST001 counter, 5 SVG 2 colunas, touch damage, canvas assinatura, PDF inline SVGs, ❗ no mapa e passeio, alerta checkout, frase aceite hóspede); status ✅/⚠️/○ na lista; botão ✏️ editar; lixeira com restauração + PIN gestor p/ limpar; vincular à hospedagem no fluxo de confirmação; VISTORIAS_LIXEIRA persistido; vistoria_editada/vistoria_deletada no histórico; dois carros mesmo apt: aviso + campo diferenciador + GS separado; Tema por cliente (10 cores, CSS vars); Histórico por usuário; Relatório de Produtividade; ref() chama refRecarga+refVistoria; versionCode 7 |
| v1.8 | www/index.html (garagespot-22.html) | Novo Check-in Integrado (NCI): fluxo 4 etapas com overlay full-screen (#nci-overlay); STEP2 dados veículo; STEP3 vistoria landscape (lock via @capacitor/screen-orientation, SVG car top-down zona de danos tap→✕ com janelinha excluir/manter, canvas assinatura devicePixelRatio, frase aceite); STEP4 confirmar; STEP5 sucesso + aguardar vaga; CHECKINS_PENDENTES{} com localStorage garagespot_checkins_pendentes; rascunho auto-save garagespot_vistoria_rascunho com resume ao reabrir; "＋ Novo Check-in" em Painel do Dia + seção "🚗 Aguardando vaga (X)" com cards + "Destacar vagas livres"; showOcc detecta apt pendente → designação; _aplicarDesignacao() cria HOSPEDAGENS+HISTORICO+VISTORIAS(se MODULOS.vistorias); fmtNomeArquivo novo formato apt_GS_hospede_DD-MM-YY; vistoria PDF renomeado apt_VIST_DD-MM-YY; npm install @capacitor/screen-orientation; versionCode 8 |
| v1.9 | www/index.html (garagespot-23.html) | Navbar reordenada [📊 Painel][🗺 Mapa][⚡ Recarga][⚙ Gestão]; Painel como tela padrão (navTo('painel') no init); clkV() redesenhado: toque em vaga livre → confirmarUsuario → pedir APT → rotear (passeio retorno / designação NCI / novo NCI); renderPainelDia() 8 seções (cards ocupação, ＋ Novo Check-in, fila pendentes, hospedados, movimentações do dia, status recarga, vistorias pendentes, plantão+backup); renderTelaVistorias() com busca (apt/VIST/data/modelo/hóspede), filtro status ✅/❗, date picker De/Até, contador resultados, toque na linha abre vistoria; PDF vistoria salvo em GarageSpot/Vistorias/[Mês Ano]/; versionCode 9 |
| v1.9.1 | www/index.html | Limpeza vistoria como módulo separado: removido renderTelaVistorias(), toggle módulo vistorias, nav-vistorias, vistorias-wrap, showLixeiraVistorias(), restaurarVistoria(), botão 📋 do topo de showDet; mantido novaVistoria()+verVistoria()+editarVistoria()+assinarVistoria()+deletarVistoria() acessíveis via Anexos; deletarVistoria() agora exclui permanentemente; ❗ no passeio/mapa sempre ativo; Gestão→Configurações mostra apenas módulo Recarga; checkout mostra "✍ Assinar vistoria antes" em vez de "ir para Vistorias" |
| v1.9.2 | www/index.html | NCI step3 com imagem real: VISTORIA_IMG_B64 (ficha JPEG base64 ~271KB) em layout portrait-vst (flex coluna, nci-dz 42vh); removido landscape forçado (_nciLockLandscape/_nciUnlockOrientation e todas chamadas); ✕ danos via tap em coordenadas % sobre a imagem; canvas assinatura devicePixelRatio; versionCode 10 |
| v1.9.3 | www/index.html | **STEP3 do NCI refeito — arquitetura de template imutável.** `VISTORIA_TEMPLATE` (versão v1, imagem somente leitura, zonas em %) carregado uma vez (`_vtPreload`); cada vistoria = camada de marcações (% da imagem natural 1600×1211) + dados, composta num PNG só na confirmação (`_vtComporDocumento`). Coordenadas calculadas sobre o retângulo realmente pintado descontando letterbox de object-fit:contain (`_vtPaintedRect`/`_vtFitLayer`). ZONA A (avarias) e ZONA B (assinatura) em painéis full-screen recriados a cada STEP3 (`_nciDestruirPaineis`/`_nciCriarPaineis`) — zero vazamento de estado entre vistorias. Bug do popup **Excluir** corrigido: stopPropagation + remoção por índice + re-render do zero. Assinatura: canvas DPR, traço 2.5px preto, fundo transparente. PNG anexado à vaga (`_vtAnexarDocumento` → ANEXOS, entra no PDF de checkout) com nome `{apto}_{DD-MM-AA}_{modelo}-{cor}_VIST{nnn}.png`. STEP2: removida pergunta de tamanho, adicionado "Data de saída prevista" obrigatório → `HOSPEDAGENS[gs].saida_prevista` (ISO). verVistoria mostra o documento composto; recompõe ao coletar assinatura pendente. Fix: `logSistema`→`addLogSistema` em `_aplicarDesignacao`. versionCode 11 |
| v1.9.4 | www/index.html | **Vistoria reconstruída em HTML/CSS nativo (não mais JPEG).** Documento real renderizado: cabeçalho com `LOGO_CLIENTE_B64` (Hotel Gumz) + título "Termo de Vistoria Veicular" + VIST/GS/timestamp + linha azul; corpo grid 1.7fr/1fr (landscape) ou 1fr (portrait) com imagem dos 5 ângulos do carro (`CARRO_5VISTAS_B64`, 800×533, transparente) à esquerda e campos digitais (Apartamento / Modelo·Cor / Funcionário / SEM·COM AVARIA com auto-detecção) à direita; texto legal; área de assinatura com linha+label. Telas expandidas com animação `transform:scale + opacity` 250ms `cubic-bezier(.4,0,.2,1)`. Marcações ✕: coords via `getBoundingClientRect()` da `<img>` com 2 casas decimais, validação de bounds 0-100, `vst-mk-wrap` 44×44px ao redor de cada ✕, popup `[Excluir]/[Manter]` (stopPropagation + remoção por índice + re-render — bug Excluir corrigido), debounce 100ms, modal de confirmação em "Limpar todas", `Haptics.impact LIGHT` (fallback `navigator.vibrate(20)`), pinch-to-zoom 1-3× com pan. Assinatura: canvas DPR-scaled, traço 2.5px #000, touch+mouse+pointer, resize com preservação via `toDataURL/drawImage`. Composição: canvas 1200×1700 A4 retrato → PNG anexado em `ANEXOS['v_'+vagaId]` com nome `{apto}_{DD-MM-AA}_{modelo}-{cor}_VIST{nnn}.png` → entra no PDF de checkout. Loading "Finalizando vistoria…" com spinner, toast de sucesso, aviso de orientação portrait (1ª vez, `localStorage`). `capacitor.config.json` com `server.url` para `https://apollodsk.github.io/garagespot-dev/` → APK dev online (atualização automática a cada deploy). versionCode 12 |
| v1.9.4.1 | www/index.html | **NCI refatorado em PÁGINA ÚNICA scrolável (sem steps separados)** com ativação contextual SEM expansão (resolve bugs de mapeamento). 3 seções no overlay: Operador (auto), Dados (form reativo), Vistoria (documento inline com imagem + checkboxes auto SEM/COM AVARIA + assinatura). **10 camadas de garantia de precisão no mapeamento**: (1) listener APENAS na `<img>`, (2) `getBoundingClientRect` direto da img, (3) bounds 0-100 obrigatórios, (4) `stopPropagation` em handlers, (5) layer espelhada com `pointer-events:none` + img com `touch-action:none`, (6) canvas DPR scale+strokeStyle aplicados, (7) resize handler preservando desenho via `toDataURL/drawImage`, (8) logs de debug `[VST DEBUG]` detalhados (mantidos para validação), (9) marcador verde de 6px no ponto exato tocado (debug visual, 2.5s, mantido), (10) implementação espelhada calcular↔renderizar usando mesmo % na mesma layer. **STEP5** com `[Designar vaga agora]` (ativa MODO_DESIGNACAO + navTo mapa) e `[Designar depois]` (volta ao painel). **MODO_DESIGNACAO** estado global `{gs,apt,model,color,plate,guest,obs,vistoria_numero,timestamp}` + banner azul sticky no topo do mapa com botão ✕ cancelar. `clkV` refatorado: prioridade MODO_DESIGNACAO → `_clkVModoDesignacao` → modal direto SEM pedir apto novamente. `_aplicarDesignacaoDireta` com `Haptics LIGHT` + animação `pulse-novo` 2s na vaga. **Aguardando vaga no painel** agora lê CHECKINS_PENDENTES (legacy) **+** HOSPEDAGENS com `status='aguardando_designacao'`; `ativarDesignacaoHosp(gs)` ativa MODO_DESIGNACAO a partir do card. **PDF do checkout** inclui TODAS vistorias da hospedagem (vistorias primeiro, ordenadas por `VIST{nnn}` desc; depois fotos); cada página com título identificador; try/catch + lista de falhas. **Badge `📎 N`** no botão anexos com contador total. **Rascunho silencioso** debounce 500ms + retomar ao reabrir (<4h) + modal voltar `[Cancelar][Salvar e sair][Descartar tudo]`. **Backup canvas** durante app em background via `visibilitychange`. **Limite 20 avarias** com toast. **Meta tags no-cache** (`Cache-Control`, `Pragma`, `Expires`). **UUID `vist-...`** invisível em cada vistoria; **`tipo:'entrada'`** (prep vistoria de saída futura); **`vistorias[]` array** em HOSPEDAGENS (prep v2.0). **Prévia landscape** antes de registrar (modal "vire o celular" se portrait + listener orientationchange). Limpeza código v1.9.4 (steps 2-4 antigos, `_vtCriarPaineis`/`_vtAbrir*`/`_vt*Sig*` modais, etc). versionCode 13 |
| v1.9.4.1.7 | www/index.html + tests/* | **BUG CRÍTICO #1 (anexos somem em Nova Vistoria de carro hospedado) + Bug Q (PDF checkout fotos) + Bug R (assinatura touch) + Bug T (logs) + versão visível no rodapé do Painel.** **BUG #1 Causa A** (race condition fotos): `_nciFotosPromisesPendentes` array global registra cada Promise de `_nciFotoFileToB64Compr`; `_nciFotosSalvarESegue` agora é **async** e `await Promise.all(...)` antes de salvar — bloqueio definitivo de salvar com fotos parcialmente processadas. Reset do array em `_nciAbrirEtapaFotos`. **BUG #1 Causa B** (chave errada — "prancheta 2 mas anexo vazio"): `_nciFotosSalvarESegue` agora detecta `hosp.vaga_inicial` + `S[vagaId].hospedagem===gs` para salvar em **`v_<vagaId>`** quando carro já hospedado (Nova Vistoria adicional) ou **`h_<gs>`** quando aguardando designação. Anexo de foto agora carrega `{usuario, apt, modelo, cor}` para legenda no PDF. **Bug Q** (CAUSA RAIZ CONFIRMADA: `doChk` deletava `ANEXOS[v_<vagaId>]` linha ~2480 ANTES de chamar `compartilharPDF` linha ~2491): snapshot `_snapshotAnexosCheckout={vagaId, gs, fotos, vistorias}` capturado em `doChk` ANTES da liberação da vaga e da deleção dos anexos; passado por `compartilharPDF(apt, dv, hist, anexos, snapshotCheckout)` → `buildRegistroDoc(apt, dv, hist, snapshotCheckout)`; PDF usa snapshot quando fornecido (fluxo checkout) ou busca normal em ANEXOS (fluxo compartilhar avulso). Legendas com `Apt X · Modelo Cor · Data · Funcionário`. **Bug R** (CAUSA RAIZ CONFIRMADA: `getBoundingClientRect()` retornava 0×0 porque canvas estava em `display:none` no momento do setup, então `cv.width=0` era gravado e traços nunca apareciam até `Limpar` disparar nova setup com canvas já visível): novo `_vtSigEsperarEVisivel(tentativa)` força reflow via `void cv.offsetHeight` antes de medir, polling com `requestAnimationFrame + setTimeout(30ms)` até 30 tentativas; `_vtSigSetup` ganhou **guarda dupla** — nunca grava dimensão 0, delega ao esperador se rect 0×0; `_vtSigSetupRetryComObserver` (IntersectionObserver) **REMOVIDO** (não dispara em `display:none`). **Bug T** (logs em `clkV`): rastreia `MODO_DESIGNACAO` no momento do toque; warning se banner visível mas MODO_DESIGNACAO null (estado inconsistente). **Versão visível**: constantes `GS_VERSION='v1.9.4.1.7'`/`GS_VERSION_CODE=20`/`GS_BUILD_TS` no topo do script; rodapé `#gs-versao-rodape` no Painel mostra "GarageSpot v1.9.4.1.7 · build YYYY-MM-DD · versionCode 20". Tag git `v1.9.4.1.6-stable` criada para rollback. **34/34 testes Playwright passaram** incluindo specs novos `bug1-anexos-nova-vistoria.spec.js` (3 testes — chave correta + bloqueio await) e `regression-v1916.spec.js` (5 testes — não-regressão v1.9.4.1.5+.1.6). versionCode 20 |
| v1.9.4.1.6 | www/index.html + tests/* | **Bugs Q/R/S/T/U/W/X + infraestrutura de testes Playwright.** **Bug Q** (PDF checkout sem fotos): logs `[BUG Q]` em `buildRegistroDoc`; filtro ampliado aceita fotos legadas sem `tipo:'foto'` (somente `isImg:true`); try/catch por foto individual com `console.error`; header da página de foto agora tem nome completo `Apt X · Modelo Cor · Data · Funcionário`. **Bug R** (assinatura touch só após Limpar): novo helper `_vtSigSetupRetryComObserver(cv)` com IntersectionObserver + retry exponencial 50→800ms até 20 tentativas; `_vtAtivarAssinatura` reseta contador e dispara dupla tentativa via `requestAnimationFrame` + `setTimeout`; listener `transitionend` no container para re-setup quando animação CSS terminar. **Bug S** (preview fotos NCI): nova função `_nciFotosPreviewModal(foto)` cria overlay z-index 10000 com foto centralizada + botões `[📷 Tirar outra]` e `[✓ Confirmar e voltar]`; nova variante `_nciFotoAdicionarERetornar(b64)` que retorna a foto adicionada; `_nciFotosCapturarCamera` chama o preview após captura aguardando thumb gerar (até 10 tentativas, 100ms cada). **Bug T** (designar pós-checkin pedia operador): logs `[BUG T]` detalhados em `_nciStep5DesignarAgora` e `_aplicarDesignacaoDireta`; 3 camadas de fallback do operador: `d.usuario` → `HOSPEDAGENS[gs].usuario_checkin` → turno ativo único → '—'; bloco `pos_checkin` em `_aplicarDesignacaoDireta` reforçado com `return` explícito após exec. **Bug U** (ordenação vistorias): `_listarVistoriasDaHosp` agora usa fallback múltiplo `ts_finalizacao || ts_assinada || ts_criada || ts_criacao`; log `[BUG U] ordenação:` para inspeção. **Bug W** (storage refactor — sumiço de dados em background): sistema de backup rotativo de 3 slots (`BACKUP_KEYS` para hospedagens/vistorias/anexos/state); `_saveProtegido(key, dados, tipo)` rotaciona bk2←bk1←atual antes de gravar + BLOQUEIA save de objeto vazio quando havia >5 itens (anti-perda crítica); `_loadProtegido(tipo)` tenta principal→bk1→bk2 com toast de aviso se usar backup; contadores persistidos em `garagespot_contadores`; saves forçados em `visibilitychange='hidden'` e `pagehide` para sobreviver ao Android matando o webview; funções globais `gsRecovery()` (mostra estado de todos backups) e `gsRestoreFrom(tipo, slot)` (recovery manual via console). **Bug X** (race condition fotos): contador global `_nciFotosProcessando`; `_nciFotosAtualizarBotaoSalvar()` desabilita botão `#ef-btn-concluir` mudando texto para `⏳ Processando N foto(s)...` enquanto há promises pendentes; `_nciFotosSalvarESegue` BLOQUEIA com toast se contador > 0; `_nciFotosOnFileInput` incrementa antes do processamento e decrementa no `.finally()` de cada Promise. **Infraestrutura de testes Playwright**: 8 specs criados em `tests/specs/` cobrindo cada bug + regression v1.9.4.1.5 + smoke. Fixture compartilhado `tests/fixtures/setup.js` suprime kill-switch e expõe PNG/JPEG 1×1 base64. Tag git `v1.9.4.1.5-stable` criada antes do refactor para rollback. **30/30 testes passaram em 35.2s antes do commit.** versionCode 19 |
| v1.9.4.1.5 | www/index.html | **Bugs O+P (eliminação CRÍTICA do NCI antigo em Nova Vistoria + Designar agora) + Bug J (PDF checkout com vistorias+fotos) + Bug L (vistoria preservada após designar) + Bug N (PDF compartilhar real) + Melhoria 3 (atrasados em Hoje) + toggles em expansões + interatividade completa.** **Bug O**: `_iniciarNovaVistoriaAdicional` substituído — não chama mais `novaVistoria` legacy (modais `_vstStep1`/`_vstStep2b`/`_vstStep4`); novo `_abrirNCIParaNovaVistoria(gs, usuario)` cria `_nciD` pré-preenchido com flag `_modoNovaVistoria=true` + `_gsExistente=gs`; `_aplicarUINovaVistoria()` marca campos readonly via `.campo-readonly`, ajusta título "Nova Vistoria", marca progresso Dados como ✓, troca texto botão para "Registrar Nova Vistoria", scroll para seção vistoria. **Bug O commit**: `_nciCommitCheckin` branch para `_nciCommitNovaVistoriaAdicional` quando flag ativa — NÃO cria nova HOSPEDAGEM, vincula vistoria à existente via `hosp.vistorias.push(numero)`, marca `tipo='adicional'`, anexa PNG em `v_<vagaId>` (se houver vaga) ou `h_<gs>`, registra histórico `vistoria_adicional_criada`. `_nciPosFotos` branch idêntico para Nova Vistoria — pula STEP5, fecha overlay, reabre Detalhes da vaga. **Bug P**: `_aplicarDesignacaoDireta` agora NUNCA pergunta operador quando `origem==='pos_checkin'` — usa `HOSPEDAGENS[gs].usuario_checkin` como fonte autoritativa, fallback '—' se ausente; elimina modal "Confirma · Carlos · Manobrista · Expediente" pós Designar agora. **Bug L**: `_aplicarDesignacaoExec` ganhou snapshot defensivo `vistoriasAntes`/`anexosHospAntes` antes da operação + validação pós-operação (restaura `hosp.vistorias` se perdeu); migração `ANEXOS h_<gs> → v_<vagaId>` ganhou logs de validação total. **Bug J**: `buildRegistroDoc` (PDF checkout) estendido — após tabela de movimentações adiciona páginas com vistorias da hospedagem (ordenadas mais recente→antiga via `ts_finalizacao`/`ts_criada`, renderizadas via `documento_final_b64`) + cada foto em página separada com header data/hora; try/catch por página. **Bug N**: `gerarPDFVistoria` reescrito para usar **jsPDF direto** (não mais HTML) — página 1 com `documento_final_b64` da vistoria; páginas seguintes com cada foto da hospedagem (de `v_<vagaId>` + `h_<gs>`); fallback HTML se jsPDF indisponível. **Painel reestruturado**: tile "Check-outs" do agrupador Hoje agora soma `checkoutsHoje + atrasados`; tile "Check-out atrasado" REMOVIDO de Pendências; badge Pendências conta apenas `semVaga + semAssin` (sem atrasados); tile "Movimentações totais" renomeado "Movimentações". **Toggles nas expansões**: Hoje com `[Tudo][Check-ins][Check-outs][Outras]`, Hospedados com `[Tudo][Na garagem][A passeio]`; cliques em tiles individuais passam filtro inicial via `abrirExpansao(grupo, filtroInicial)`. **Lista check-outs separada por data** (subtítulos HOJE/DD/MM/AAAA descendente); item HOJE → `_iniciarCheckout(vagaId)` (showMenu); item ATRASADO → `_modalCheckoutAtrasado(gs)` com 3 opções (checkout agora, alterar data, cancelar). **Date picker** `_abrirDatePickerNovaData(gs)` aceita apenas datas futuras (min=amanhã), atualiza `saida_prevista` + registra histórico edição. **Interatividade**: check-in/hospedado clicável → `showDet(vagaId)` ou `abrirDetalhesAguardando(gs)` ou `showPasseioDetail(apt)`; designações em "Outras" → mapa com busca; cards Pendências sem-vaga clicáveis no corpo → Detalhes (botões internos `stopPropagation`); card sem-assinatura → Detalhes da vaga; sem chevron/hover/long-press conforme spec. Melhoria 1 (multi-foto NCI) já estava implementada via input multiple + array handler. versionCode 18 |
| v1.9.4.1.4 | www/index.html | **Bug G + Bug H + Bug I + Nova Vistoria em Detalhes.** **Bug G** (preview assinatura não aparecia na vista interna): removido `style="display:none"` inline do `<img id="assinatura-preview">` que sobrescrevia o CSS class-based; `_vtAtualizarSigUI` refatorado para usar inline style + classe simultaneamente (modoAtivo=ativo+canvas, temAssin=preview, default=toque) — defesa em camadas. **Bug H** (coletar assinatura depois aceitava vazio): nova função `_vstCanvasVazio(canvas)` (alpha=0 scan); validação adicionada no botão "Confirmar Assinatura" de `assinarVistoria(id)` — toast "Nenhuma assinatura registrada. Assine antes de confirmar." se vazio + NÃO fecha modal; após sucesso chama `renderAgrupadoresPainel()` para atualizar badge de Pendências. **Bug I** (designação pós-checkin pedia operador + abria NCI): `_aplicarDesignacaoDireta` ganhou fallback de operador via `HOSPEDAGENS[gs].usuario_checkin` quando `origem='pos_checkin'` e `m.operador` ausente; callback do `confirmarUsuario` agora chama `closeOv()` ANTES de `_aplicarDesignacaoExec` — eliminando o click fantasma que abria "Iniciar check-in?" via `_clkVDesignar`; `_nciStep5DesignarAgora` reforçado com fallback duplo (`d.usuario` → `HOSPEDAGENS[d.gs].usuario_checkin`). **Nova Vistoria em Detalhes**: ícone 📋 no Anexos agora abre `abrirMenuVistorias(apt, gs, fromPasseio)` — modal lista TODAS as vistorias da hospedagem ordenadas mais recente → mais antiga (via `_listarVistoriasDaHosp`, prefere GS, fallback por apt) com botões [Visualizar] [📤 PDF] [✍ Coletar assinatura se pendente]; botão "+ Nova Vistoria" no rodapé chama `_iniciarNovaVistoriaAdicional(apt, gs)` que mostra confirmação + dispara `novaVistoria(preApt, preHosp)` legacy — VISTORIAS criadas ficam vinculadas via campo `.hospedagem` e entram no PDF de checkout. Badge 📋 do anexos agora mostra contador "N" + ❗ se houver pendência. Marcação de avarias INTOCADA; composerPNGVistoria INTOCADO; Painel agrupadores PRESERVADO. versionCode 17 |
| v1.9.4.1.3 | www/index.html | **Bug F (duplicação da assinatura ao Concluir no NCI) + REFORMA DO PAINEL com agrupadores em 2 colunas.** Bug F corrigido: `_vtDesativarAssinatura(true)` agora salva base64 + LIMPA canvas + seta `_nciD.assinatura_pendente=false`; `_vtSigSetup` protegido com early-return quando `MODO_VISTORIA_ATIVO!=='assinatura'` (resize/orientationchange não restaura mais o desenho fora do modo edição); CSS reescrito: `.vst-assinatura-box canvas{display:none}` por padrão e `display:block` apenas quando `.ativa`, `.assinatura-img` com `display:none` padrão e `display:block` apenas em `.tem-assinatura:not(.ativa)`, classe `.tem-assinatura` controla visibilidade da label/toque e do preview; `_vtAtualizarSigUI` migrado para abordagem por classe (não mais inline style); `_vtAssinaturaLimparCompleto` remove `.tem-assinatura` e seta `assinatura_pendente=true`; auditado `_vtComporPNG` — já usa `d.assinatura` (base64) exclusivamente, nunca canvas ao vivo. **Reforma do Painel**: removidas seções "HOSPEDADOS lista direta" + "MOVIMENTAÇÕES HOJE lista direta" + "Aguardando vaga inline" + recarga inline + botões "ver mais"; adicionados 4 agrupadores em 2 colunas (`.grupos-grid` grid 1fr/1fr) seguindo estilo Garagem Agora — **Hoje** (check-ins/check-outs/movimentações totais), **Pendências** (sem vaga/sem assin./check-out atrasado com borda amarela + badge dinâmica), **Hospedados** (total/na garagem/a passeio), **Recarga** (carregando/na fila — placeholder). Função `renderAgrupadoresPainel()` recalcula 9 contadores via HOSPEDAGENS/VISTORIAS/S/PASSEIO/HISTORICO e é chamada ao final de `renderPainelDia()` (cobre todos os eventos de re-render existentes). Toque em qualquer agrupador abre `#expansao-overlay` (z-index 500, posição fixed top-bottom) com renders dedicados: `renderExpansaoHoje` (check-ins ordenados recente→antigo + check-outs previstos), `renderExpansaoPendencias` (3 seções com cards reaproveitando `.card-aguardando-vaga` + novo `.card-pend-assin` vermelho + novo `.card-pend-atraso` laranja), `renderExpansaoHospedados` (reaproveita filtro de hospedagens ativas, ordem recente→antigo, tag aguardando), `renderExpansaoRecarga` (Em breve centralizado). `bindHandlersPendencias` reaproveita `abrirDetalhesAguardando`/`ativarDesignacaoHosp`/`assinarVistoria` (NÃO reescritos). Interceptação do botão Voltar Android via `document.addEventListener('backbutton')` fecha overlay sem fechar app; `navTo()` fecha overlay ao trocar de tab. HEADER + barra "A passeio" do topbar + card Garagem Agora + botão Novo Check-in + Plantão (com BACKUP) PRESERVADOS INTACTOS. Marcação de avarias e coletar assinatura depois (`assinarVistoria(id)` com canvas próprio em modal) NÃO TOCADOS. versionCode 16 |
| v1.9.4.1.2 | www/index.html | **Correções finais da vistoria de entrada (5 bugs específicos).** **Bug A (assinatura definitivamente à frente)** — canvas `top:0;left:0;width:100%!important;height:100%!important;z-index:10;pointer-events:none` (auto quando `.ativa`); linha+label `z-index:1`; toque `z-index:2`; canvas cobre TODA a área da box → traços sempre sobrepõem a linha decorativa. **Bug B (sem duplicação assinatura)** — ao tocar área com assinatura existente, modal `[Manter assinatura]/[Refazer assinatura]`; `_vtAssinaturaLimparCompleto` zera canvas + `_nciD.assinatura=null` + `_nciSigBackup=null`; botão `[🗑 Limpar]` da barra contexto chama `_vtAssinaturaLimparCompleto` (limpa TUDO, sem deixar fantasma). **Bug C (modal "Vire o celular" REMOVIDO)** — `_nciShowPrevia` abre `_nciAbrirPreviaLandscape` direto em qualquer orientação; nova media query `@media (orientation:portrait)` para `.vst-modal-content:has(.previa-card)` com max-width 600px width 95% e botões row. **Bug D (câmera funciona na etapa de fotos)** — diagnóstico: anexos de detalhes usam `<input type="file" accept="image/*" capture="environment">` (não plugin Capacitor); refatorado `_nciFotosCapturarCamera` para usar EXATAMENTE o mesmo método (cria input com `capture='environment'` + `click()`); funciona em Android moderno sem precisar de `@capacitor/camera`. **Bug E (não pergunta operador após pos_checkin)** — `MODO_DESIGNACAO` ganha campos `origem ('pos_checkin'\|'painel'\|'vaga_direta')` e `operador`; `_nciStep5DesignarAgora` seta `origem:'pos_checkin', operador:d.usuario`; `ativarDesignacaoHosp` seta `origem:'painel', operador:null`; `_aplicarDesignacaoDireta` verifica `m.operador` — se presente aplica direto, senão chama `confirmarUsuario`. **MARCAÇÃO DE AVARIAS INTOCADA** (REGRA 4 cumprida — `_vtImgPointerUp`, `_vtCoordPercent`, `_vtRenderAvariasLayer`, `_vtRedrawDebugMarkers`, CSS `.vst-area-carros*` e `.vst-carros-img` NÃO alterados). versionCode 15 |
| v1.9.4.1.1 | www/index.html | **Correções estruturais da vistoria + etapa de fotos + designação automática.** **Bug 1 (marcação 1 dedo)** — causa raiz: conflito entre `click` e `touchend` na img + falta de `pointer-events:none` na inativa; correção arquitetural: img tem `pointer-events:none` por padrão e `pointer-events:auto;touch-action:none` quando `.vst-area-carros.ativa`; listeners separados via `pointerup` (não mais `click`+`touchend`): ativação na área externa, marcação só na img. **Bug 2 (assinatura atrás da linha)** — canvas `z-index:3` acima de linha+label (`z-index:1`); barra contexto `z-index:100`. **Bug 3 (landscape durante vistoria)** — wrapper `.vst-body` + `@media (orientation:landscape){grid-template-areas:"carros campos" "assinatura assinatura" "legal legal"}`; `_vtOnResize` debounce 300ms re-renderiza layer + reseta canvas preservando desenho via `toDataURL/drawImage`; `_vtRedrawDebugMarkers` recria marcadores verdes em sincronia. **Bug 4 (desativar ao tocar fora)** — listener global `pointerup` capture phase com guards de dentro/fora; alternar avarias↔assinatura ao tocar em outra área. **Bug 5 (caixa revisão landscape)** — `.vst-modal-content:has(.previa-card){max-width:1100px;width:92%}` + botões `flex-direction:row` lado a lado (portrait intacto). **Bug 6 (vaga inicial)** — variável `vagaInicialNCI` setada ao iniciar NCI via vaga; `_aplicarDesignacaoAutomatica` aplica direto após etapa de fotos (skip STEP5); fallback se vaga ocupar enquanto preenche. **Bug 7 (designar depois)** — `_nciStep5DesignarDepois(event)` com `stopPropagation+preventDefault` + `setTimeout 120ms` antes de re-renderizar painel (evita clique fantasma em "+Novo Check-in" no mesmo ponto). **Etapa de fotos (nova)** — após "Confirmar e Registrar", tela `.etapa-fotos` com `[📷 Tirar Foto]` (Capacitor.Plugins.Camera quality:85, 1920x1080, base64) + `[📁 Selecionar Arquivo]` (file input multiple com compressão JPEG 0.85); thumbnails 200x200 0.7; limite 20; `[Voltar]` preserva fotos e reabre prévia; `[Concluir]` sem fotos → modal "Continuar?"; fotos salvas em `ANEXOS['h_'+gs]` com `tipo:'foto'` e nome `{apto}_{DD-MM-AA}_foto_001.jpg`; rascunho completo `garagespot_rascunho_completo` (24h TTL) protege contra webview morrer ao abrir câmera. **Marcador verde 6px** agora DEFINITIVO (sem timeout) na layer espelhada — sobrevive a giro de tela. **Card aguardando vaga** com 2 botões `[Detalhes]` (abre `abrirDetalhesAguardando(gs)` com dados + anexos sem botão Designar dentro) e `[Designar vaga]` (ativa MODO_DESIGNACAO). **Hospedados corrigido** — filtro `!checkout_ts && (status='ativa'\|\|'aguardando_designacao'\|\|sem-status)`; ordem `checkin_ts` desc; tag `⏳ Aguardando vaga` (`.tag-aguardando`) para hospedagens sem vaga; clique nesses cards abre detalhes em vez de busca. **TTL rascunho NCI** aumentado de 4h para 24h. **Proteção commit duplo** via flag `_nciD._commitFeito` (voltar da etapa de fotos para a prévia e reconfirmar não duplica). versionCode 14 · APK não buildada (puramente HTML/CSS/JS) |

---

## Vistoria — Arquitetura HTML/CSS Nativa (v1.9.4, atual)

> A arquitetura atual da vistoria é um documento HTML/CSS renderizado nativamente — **não mais um JPEG com sobreposições**. A v1.9.3 (template imutável JPEG) está documentada abaixo como referência histórica.

**Conceito:** o documento de vistoria é HTML/CSS real, com layout responsivo (landscape/portrait via `@media`). A imagem dos 5 ângulos do carro é um `<img>` dentro do layout; as marcações ✕ são `<div>` posicionados em % relativos à imagem renderizada. A composição final (PNG 1200×1700) é feita em canvas off-screen **apenas no momento da confirmação**.

**Assets embutidos (base64):**
- `CARRO_5VISTAS_B64` — `vistoria-carro.png` (800×533, transparente, ~494KB)
- `LOGO_CLIENTE_B64` — `Logo-hotel-gumz.jpg` (356×102, ~12KB)

**Estrutura da instância (`VISTORIAS[id]`):** `numero`, `template_versao:'v2'`, `origem:'nci'`, `apt`, `hospedagem`/`hospedagem_gs`, `modelo`, `cor`, `placa`, `hospede`, `funcionario`, `dados{apt,modelo,cor,funcionario,data,hora}`, `avarias[]`/`danos[]` (`{x,y}` em % da imagem renderizada, 2 casas decimais — mantidos espelhados para compatibilidade), `com_avaria`, `assinatura`/`assinatura_b64` (PNG transparente), `assinatura_pendente`, `documento_final_b64` (PNG 1200×1700), `ts_criacao`/`ts_criada`/`ts_finalizacao`/`ts_assinada`.

**CSS:** `.vst-doc` (max-w 1100 landscape / 420 portrait), `.vst-header` (logo + título + códigos + linha azul `#185FA5`), `.vst-body` (grid 1.7fr/1fr ou 1fr), `.vst-carros` + `.vst-avarias-layer`, `.vst-campos` (campo-label/valor), `.check-avarias` (SEM=`#0F6E56` / COM=`#A32D2D`), `.vst-legal`, `.vst-assinatura`. Painéis expandidos `.vst-panel` animados (`scale+opacity` 250ms `cubic-bezier(.4,0,.2,1)`).

**Funções-chave:**
- `_nciStep3` / `_vtRenderDoc` (template HTML) / `_vtRenderAvariasLayer` / `_vtUpdateChecks` (auto SEM/COM AVARIA + counters)
- `_vtDestruirPaineis`/`_vtCriarPaineis` — recriados a cada STEP3 (zero vazamento)
- `_vtAbrirAvarias`/`_vtFecharAvarias` + `_vtBindPinchZoom` (scale 1-3 + pan), `_vtAvariaPopup` (Excluir = `stopPropagation`+índice+re-render), `_vtAvariaLimparTodas`/`_vtAvariaLimparOK`
- `_vtAbrirAssinatura`/`_vtSigSetup`/`_vtSigLimpar`/`_vtFecharAssinatura` — canvas DPR 2.5px #000 transparente, touch+mouse+pointer, resize com preservação
- `_vtHaptic` — `Capacitor.Plugins.Haptics.impact LIGHT` (fallback `navigator.vibrate(20)`)
- `_nciConfirmarVistoria`/`_vtConfSemAssin`/`_vtFinalizar` — modal sem assinatura, loading "Finalizando vistoria…", composição
- `_vtComporPNG` — canvas 1200×1700, header + carros com ✕ + campos + checks + legal + assinatura → PNG base64
- `_vtAnexarDocumento` — `ANEXOS['v_'+vagaId]` com `isImg:true`, nome `{apto}_{DD-MM-AA}_{modelo}-{cor}_VIST{nnn}.png`
- `_vtRecomporVistoria` — recompõe ao coletar assinatura pendente

**Aviso de orientação:** ao abrir STEP3 em portrait pela 1ª vez, toast "Vire o aparelho na horizontal…" (3s). Flag em `localStorage['garagespot_orientacao_aviso_visto']`.

---

## Vistoria — Arquitetura Template Imutável (v1.9.3, legado)

> Referência histórica. **Substituída pela v1.9.4.**

**Conceito:** `vistoria.jpg` (1600×1211) é um TEMPLATE somente leitura, eterno, imutável, carregado uma vez no init e nunca modificado. Toda vistoria é uma camada de marcações + dados sobreposta. O documento final é o resultado da composição na hora de confirmar.

**Estrutura 1 — Template global (`VISTORIA_TEMPLATE`):**
- `versao` ('v1'), `imagem_b64` (= `VISTORIA_IMG_B64`), `natural_w`/`natural_h` (1600/1211)
- `zonas{}`: `desenhos`, `assinatura` (x,y,w,h em %), `campo_apto`, `campo_modelo_cor`, `campo_funcionario`, `campo_data`, `check_sem_avaria`, `check_com_avaria` (x,y em %)
- Calibração das zonas é feita observando a imagem; ajustar os % em `VISTORIA_TEMPLATE.zonas` se necessário.

**Estrutura 2 — Instância (`VISTORIAS[id]`):** `numero`, `template_versao`, `origem:'nci'`, `apt`, `hospedagem`, `modelo`, `cor`, `placa`, `hospede`, `saida_prevista`, `funcionario`, `dados{}`, `danos[]` (cada `{x,y}` em % da imagem natural — SEMPRE começa vazio), `com_avaria`, `assinatura` (PNG transparente), `assinatura_pendente`, `documento_final_b64` (PNG composto), `ts_criada`/`ts_finalizacao`/`ts_assinada`.

**Coordenadas:** todo `{x,y}` é % da imagem natural. A camada (`.vt-layer`) é posicionada exatamente sobre o retângulo realmente pintado (`_vtPaintedRect` desconta o letterbox de `object-fit:contain`); marcações usam % dessa camada → consistentes em qualquer tela/orientação, no STEP3, no painel expandido, no PNG composto e na reabertura.

**Funções-chave:** `_vtPreload`, `_vtPaintedRect`, `_vtFitLayer`/`_vtFitAll`, `_nciStep3`/`_vtRenderMain`, `_nciCriarPaineis`/`_nciDestruirPaineis` (recriados a cada STEP3 → sem vazamento), `_nciZaLayerTap`/`_nciZaPop` (Excluir = stopPropagation + remoção por índice + re-render), `_nciSigSetup` (canvas DPR, traço 2.5px #000, fundo transparente), `_vtComporDocumento` (canvas 1600×1211 → PNG), `_vtAnexarDocumento` (anexo da vaga), `_vtRecomporVistoria` (recompõe ao assinar depois).

**Nomenclatura do arquivo de vistoria:** `{apto}_{DD-MM-AA}_{modelo}-{cor}_VIST{nnn}.png` — ex.: `101_16-05-26_Corolla-Prata_VIST042.png`. Anexado em `ANEXOS['v_'+vagaId]` com `isImg:true` → incluído como página no PDF de checkout (`buildRegistroHTML`).

---

## Localização dos Arquivos

```
garagespot-app/
├── www/
│   └── index.html         ← Arquivo principal do app (WebApp completo)
├── android/               ← Projeto Android/Capacitor
│   └── app/
│       └── build.gradle
├── capacitor.config.json  ← Configuração Capacitor
├── CLAUDE.md              ← Este arquivo
└── package.json
```

---

## Arquitetura JavaScript (em www/index.html)

### Estado Global

```javascript
const S = {}                // Vagas: S[id] = { status, apt, model, color, plate, guest,
                            //   obs, size, overbook, mergedMaster, mergedSlave,
                            //   hmergeWith, hospedagem }
const PASSEIO = {}          // Carros a passeio: PASSEIO[apt] = { model, color, plate,
                            //   guest, obs, lastVaga, size, hospedagem }
const HOSPEDAGENS = {}      // Hospedagens: HOSPEDAGENS[numGS] = { numero, apt, checkin_ts,
                            //   checkout_ts, vaga_inicial, model, color, plate, guest,
                            //   obs, size, usuario_checkin, usuario_checkout }
let USUARIOS = []           // Usuários: [ { id, nome, cargo, horaInicio, horaFim } ]
const HISTORICO = {}        // Histórico: HISTORICO[apt] = [ { tipo, ts, vaga, extra,
                            //   usuario, hospedagem } ]
const ANEXOS = {}           // Fotos/docs: chave 'v_'+vagaId ou 'p_'+apt
```

### Estado Global (v1.2)

```javascript
let TURNOS = []             // Turnos: [ { id, nome, inicio (HH:MM), fim (HH:MM) } ]
                            // Default: Manhã 06-14, Tarde 14-22, Noite 22-06
```

### Chaves localStorage

| Chave | Conteúdo |
|-------|----------|
| `garagem_spot_v1` | Estado das vagas e passeio (backup) |
| `garagespot_hospedagem_counter` | Contador sequencial (nunca reinicia) |
| `garagespot_hospedagens` | Objeto HOSPEDAGENS |
| `garagespot_usuarios` | Array USUARIOS |
| `garagespot_historico` | Objeto HISTORICO |
| `garagespot_anexos` | Objeto ANEXOS (fotos base64) |
| `garagespot_backup_tudo` | Backup antes de reset |
| `garagespot_license_cache` | Cache da verificação de licença |
| `garagespot_turnos` | Array TURNOS (Manhã/Tarde/Noite) |
| `garagespot_gestao_pin` | PIN de 4 dígitos para área de Gestão |
| `garagespot_log_sistema` | Log de operações administrativas |

### Número de Hospedagem

- Formato: `GS` + sequencial 3 dígitos mínimo (GS001, GS002... GS999, GS1000...)
- Gerado em `nextNumHospedagem()` — lê e incrementa o contador no localStorage
- Criado no check-in, armazenado em `S[id].hospedagem` e em `HOSPEDAGENS`

### Layout do Mapa (v1.2)

- Vagas A/B/C renomeadas com mirror flip: coluna física 1 (esq. da 1E) → 1C, ..., coluna física 9 → 9C
- Merge horizontal: vagas 3B-6B (antes era 4B-7B)
- Pilares atualizados: P1=3C|4C, P2=5C|6C, P3=7C|8C, P4=1E|1C, P5=2B|3B, P6=6B|7B

### Navegação (v1.2)

- 3 botões: `🗺 Mapa Garagem` | `📊 Painel do Dia` | `⚙ Gestão ▾`
- `navTo(v)` — alterna entre 'mapa' e 'painel'; 'gestao' abre modal com PIN
- `togglePanel()` — oculta/exibe painel passeio E navbar (#navbar) simultaneamente; arrow ▾/▴
- Painel do Dia: estatísticas do dia, últimas 10 movimentações, staff no plantão
- Gestão: protegida por PIN de 4 dígitos — pede PIN toda vez (sem unlock por tempo) (v1.3)
- PIN padrão `1200` definido automaticamente no primeiro acesso (v1.3)
- `alterarPIN()` — fluxo 3 etapas: confirmar atual → novo → confirmar novo; registra no log do sistema

### Sistema de Usuários

- Cadastro via Gestão → Cadastro de usuários
- Campos: nome, cargo, horaInicio (HH:MM), horaFim (HH:MM)
- `estaNoExpediente(u)` — verifica se hora atual está dentro do expediente (suporta turno noturno)
- `confirmarUsuario(acao, callback)` — modal de seleção usado em check-in, passeio, retorno, checkout, edição

### Turnos

- 3 turnos fixos editáveis: Manhã/Tarde/Noite
- `getTurnoAtual()` — retorna nome do turno atual
- `getTurnoDoEvento(ts)` — retorna nome do turno para um timestamp
- Usado nos Relatórios de Movimentações

### Busca Rápida (v1.4)

- `toggleBusca()` — abre/fecha busca, salva estado do painel em `_buscaPanelWasOpen`
- `executarBusca(q)` — busca em vagas ocupadas + passeio; coleta `_buscaHits` (tipo: 'vaga' ou 'passeio')
- `highlightBuscaResult(idx)` — destaque roxo `vaga-highlight` com pulse 3×; ou `passeio-highlight` no `.oi[data-apt]`
- `buscaNav(dir)` — navega entre resultados com ←→
- `fecharBusca()` — remove destaques, restaura estado do painel
- Busca por: apt, placa, hóspede, modelo, hospedagem

### Fluxo de Movimentações

1. **Check-in**: `showOcc` → `perguntarCheckin` → `confirmarUsuario` → `saveV(isCheckin=true)` → gera hospedagem → toast
2. **Saída passeio**: `showMenu` → `doOut` → `confirmarUsuario` → copia para PASSEIO com hospedagem
3. **Retorno passeio**: `showOcc` → detecta apt em PASSEIO → `confirmarUsuario` → `saveV(isCheckin=false)`
4. **Check-out**: `showMenu` → `doChk` → `confirmarUsuario` → limpa vaga, fecha hospedagem
5. **Check-out a passeio**: lista passeio → `showPasseioCheckout` → `confirmarUsuario` → fecha hospedagem
6. **Mover vaga (drag)**: `dropDrag` → `confirmarUsuario` → `executarMove(ms, destId, usuario)` → `addHistorico('movimentacao_vaga')` (v1.3)
7. **Tornar grande**: `trocarParaGrande` → `confirmarUsuario` → vertical: `saveV` + `addHistorico('tornar_grande')` / horizontal: `aplicarHMerge(id, alvo, usuario)` (v1.3)
8. **Tornar pequeno**: `trocarParaPequeno` → `confirmarUsuario` → `desfazHMerge(id, usuario)` (se hmerge) → `addHistorico('tornar_pequeno')` (v1.3)
9. **Mesclar lateral** (pós check-in/retorno): `perguntarHMerge` → `aplicarHMerge(id, alvo, usuario)` → `addHistorico('merge_lateral')` (v1.3)

### Histórico

- `addHistorico(apt, tipo, vaga, extra, usuario, hospedagem)` — adiciona evento
- `iniciarHistorico(apt, vaga, hospedagem, usuario)` — cria nova entrada para check-in
- `getHistorico(apt)` — retorna array de eventos
- Tipos: `checkin`, `saida_passeio`, `retorno_passeio`, `checkout`, `edicao`, `movimentacao_vaga`, `tornar_grande`, `tornar_pequeno`, `merge_lateral`, `desfaz_merge_lateral`
- `showHistoricoModal(apt, hospedagem)` — abre modal com cards coloridos por tipo
- ℹ️ no título de `showDet` é clicável e abre o histórico

### PDF / Compartilhar

- `buildRegistroHTML(apt, dv, hist, anexos)` — gera HTML; cabeçalho 2 colunas: esq (🅿 GarageSpot + dev), dir (Registro de Movimentação + GS001 · Apto · hóspede · período)
- `compartilharPDF(apt, dv, hist, anexos)` — usa Capacitor Filesystem+Share no APK, fallback browser; cancelamento detectado por message ('cancel'/'dismiss'/'abort'/'close') — não abre documento
- `fmtNomeArquivo(apt, guest, tsEntrada, tsSaida, hospNum)` — formato: GS001_AptX_Hóspede_DD-MM-AA a DD-MM-AA_Registro-Movimentacao_GarageSpot
- `gerarECompartilharPDF(titulo, htmlContent, nomeArquivo)` — **função genérica v1.4**: grava .html via Capacitor Filesystem, compartilha via Share (URL), fallback blob browser; cancel detection pelo errorMessage
- `compartilharPDF(apt, dv, hist, anexos)` — usa `gerarECompartilharPDF`; nome via `fmtNomeArquivo`
- `buildRelMovimentacoesHTML(evts, deVal, ateVal)` — HTML do relatório de movimentações para PDF
- `buildRelOcupacaoHTML(dadosOcup, hospsP, deVal, ateVal)` — HTML do relatório de ocupação para PDF
- `buildRelPorAptoHTML(hosps, aptVal, deVal, ateVal)` — HTML do relatório por apartamento para PDF
- **REGRA v1.4**: todo documento compartilhado pelo app = PDF via `gerarECompartilharPDF()`
- Relatórios (v1.3/v1.4): Movimentações / Ocupação / Por apartamento — todos com ← Voltar + ✕ Fechar, date pickers De/Até, botão Hoje, badges de totais, 📤 Compartilhar (PDF)

---

## Build Android

### Dois modos de build (a partir da v1.9.4)

O `capacitor.config.json` controla qual modo o APK usa:

**Modo ONLINE (DEV — `GarageSpot-dev.apk`):**
```json
{
  "appId": "com.apollods.garagespot",
  "appName": "GarageSpot",
  "webDir": "www",
  "server": {
    "url": "https://apollodsk.github.io/garagespot-dev/",
    "cleartext": false,
    "androidScheme": "https"
  }
}
```
O APK ignora o `www/` empacotado e sempre carrega a versão mais recente do GitHub Pages do dev. **Atualização automática a cada push** — não precisa reinstalar.

**Modo OFFLINE (PRODUÇÃO — `GarageSpot-vX.X.X.apk`):**
```json
{
  "appId": "com.apollods.garagespot",
  "appName": "GarageSpot",
  "webDir": "www"
}
```
Sem `server.url` → o APK usa o `www/` empacotado. Esse é o modo para o tablet do Hotel Gumz. **Funciona sem internet** depois de instalado.

### Comandos de build
```powershell
$env:JAVA_HOME="C:\Program Files\Android\Android Studio\jbr"
cd android
.\gradlew assembleDebug
# Saída: android\app\build\outputs\apk\debug\GarageSpot-debug.apk
```

> **Importante:** o `capacitor.config.json` em `master` está configurado em modo **ONLINE** (para o dev). Antes de buildar a APK de produção do hotel, **remover o bloco `server`** localmente, buildar, e depois restaurar.

### GitHub Pages — Ambientes

| Ambiente | Repositório | URL | Versão |
|----------|-------------|-----|--------|
| **PRODUÇÃO** (tablet hotel) | `ApolloDSk/garagespot-hotelgumz` | https://apollodsk.github.io/garagespot-hotelgumz/ | estável (aprovada) |
| **DESENVOLVIMENTO** (celular Douglas) | `ApolloDSk/garagespot-dev` | https://apollodsk.github.io/garagespot-dev/ | mais recente |

**Regra:** só subir para `garagespot-hotelgumz` quando Douglas aprovar a versão dev.

#### Fluxo de deploy
1. Desenvolver em `www/index.html` → push para `garagespot-app` (master)
2. Copiar para `garagespot-dev` → push → testar no celular com `GarageSpot-dev.apk`
3. Após aprovação: copiar para `garagespot-hotelgumz` → push → tablet atualiza automaticamente

#### APKs
- `GarageSpot-v*.apk` — APK offline (empacota www local), para distribuição
- `GarageSpot-dev.apk` — APK online apontando para garagespot-dev GitHub Pages; sempre busca versão mais recente do dev

---

## Kill Switch
- URL: `https://gist.githubusercontent.com/ApolloDSk/a9b3a7937b71c3e0956f236dcfd3b6d8/raw/license.json`
- Cache: 5 min (aceita cache de até 24h em modo offline)
- Campo verificado: `{ "ativo": true }`
