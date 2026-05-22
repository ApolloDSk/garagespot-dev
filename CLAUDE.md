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
