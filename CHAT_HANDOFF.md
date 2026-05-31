# CHAT_HANDOFF — GarageSpot

> Regra de ouro: tudo decidido no planejamento entra aqui — o que foi confirmado e o que ficou para o futuro.

## Como usar
Em um novo chat com Claude, envie:
"Projeto GarageSpot. Leia o handoff e o CLAUDE.md:
https://raw.githubusercontent.com/ApolloDSk/garagespot-app/refs/heads/master/CHAT_HANDOFF.md
https://raw.githubusercontent.com/ApolloDSk/garagespot-app/refs/heads/master/CLAUDE.md"

## Identidade
- App de controle de garagem para hotéis
- Cliente piloto: Hotel Gumz
- Desenvolvedor: Douglas Nascimento / Apollo DS
- Stack: HTML/JS/CSS single file + Capacitor Android
- App ID: com.apollods.garagespot

## Ambientes
- **Produção** (tablet do hotel): `garagespot-hotelgumz` → https://apollodsk.github.io/garagespot-hotelgumz/  — **NUNCA modificar sem aprovação explícita**
- **Dev** (celular Douglas, APK online): `garagespot-dev` → https://apollodsk.github.io/garagespot-dev/ (APK dev auto-atualiza via Pages)
- **Repo principal de edição:** `garagespot-app` (master)

## Estado atual
- **Versão atual: v1.9.4.4** (Mapa + correções + **edição completa dos detalhes**).
- versionCode: **22** (sem APK desde v1.9.4.1.8)
- Em produção (hotel): versão estável anterior à v1.8 — não atualizada nesta sequência.
- **Próxima: v1.9.4.5** — Gestão + bugs gerais (qualidade de vida).

## Roadmap

### Recarga (concluída)
- ✅ **v1.9.4.3.1** — Visual no mapa + 4 correções (Bug T escudo, raios horizontal, bloqueio Concluir durante preview, ordem do PDF de checkout).
- ✅ **v1.9.4.3.2** — Refinos de UX (barra "A passeio" só no Mapa, ícone responsivo, tempo em horas via `_fmtDurRecarga`) + fluxo (painel redesenhado conforme protótipo, modos de tempo Quantidade de horas + Hora final bidirecionais, lista priorizada, remanejamento, fila).
- ✅ **v1.9.4.3.3** — Correções (iniciar na **vaga real** sem mover; lista priorizando a vaga do ponto, **compartilhado 8C/9C com as duas separadas**) + finalização (estado **"Concluído"**, **encerramento com cobrança** [até programado/até agora/outro], **configuração em Gestão** [módulo on/off, pontos compartilhado/individual, valor/hora, arredondamento 15/30 cima/baixo, cortesia R$ 0,00, alertas], PDF e histórico).

### Pós-Recarga
- ✅ **v1.9.4.4 — Mapa + correções + edição completa**: (1) **Bug T** eliminado — causa-raiz: `MODO_DESIGNACAO` era perdido no reload/recriação do webview Android e o toque na vaga caía no fluxo legado `_clkVDesignar`→`confirmarUsuario` ("Confirma · operador"); corrigido com backup PERSISTENTE em localStorage + restauração auto-validada pela hospedagem (em `clkV`, `_clkVDesignar` e no init), mantendo o escudo anti-clique-fantasma; (2) **ícone de recarga preservado no drag&drop** (`_refrescarRecargaTodos` após `executarMove`); (3) **chevron dentro da barra** do header (overflow/flex/box-sizing); (4) **agrupamento Recarga do dashboard** leva ao painel funcional (sem "Em desenvolvimento"); (5) **recargas registradas como movimentação** (início/encerramento) no painel e nos detalhes, **ordem mais recente → mais antiga**; (6) **EDIÇÃO COMPLETA DOS DETALHES**: formulário = check-in pré-preenchido, edita apto, modelo, cor, placa, hóspede, observações e **DATA DE SAÍDA** sem check-out + novo check-in; **toda alteração REGISTRADA** (campo: 'de' → 'para' + por quem); apto re-chaveado em S/HOSPEDAGENS/VISTORIAS/HISTORICO/anexos; **PDF gerado depois usa o novo apto** no nome.
- ⏳ **v1.9.4.5 — Gestão + bugs gerais** (qualidade de vida): incluir/excluir funcionários do plantão; **botão "Voltar para Gestão"** nas opções (hoje só tem "Fechar"); **cadastro de apartamentos** (opcional — reconhece apto inexistente e pede correção; funciona com ou sem lista; serve para hotel **e** estacionamento comum).
- ⏳ **v1.9.4.6 — Tema** (temas em Gestão) + **Relatórios** + **Histórico**.
- ⏳ **v1.9.4.7 — Backup no Google Drive**.
- 🟢 **Atualização do hotel** — deploy em produção (`garagespot-hotelgumz`).
- ⏳ (pós-hotel) Patches de correção + novas ideias de qualidade de vida do uso real.

### Iniciativas maiores (futuro)
- ⏳ **Módulo Reservas / 3 apps:** GarageSpot (operação) + Reserva de Garagem (reservas futuras) + Combinado (as reservas migram para o GarageSpot; manobristas veem chegadas do dia e futuras). Inclui reestruturação do painel ("Hoje" → "Movimentações"; novo "Programação de Reservas").
- 🚫 **v2.0 — Banco de dados + servidor**: cliente-servidor; multi-dispositivo (PC + celular + tablet em tempo real); isolamento por hotel (multi-tenant); backup e recuperação central. **SÓ depois de tudo rodando 100% no hotel.** Stack candidata: **Supabase** (Postgres + RLS + tempo real + auth) ou Firebase; IndexedDB como cache offline.

## Decisões confirmadas / regras de trabalho
- **Versionamento:** usar `v1.9.x` / `v1.9.x.y`; **NADA de v2.0** até tudo rodar 100% no hotel.
- **Ambientes:** editar `www/index.html` em `ApolloDSk/garagespot-app` (master); deploy DEV em `garagespot-dev` → APK dev auto-atualiza via Pages; PRODUÇÃO = `garagespot-hotelgumz` — **NUNCA tocar sem aprovação**.
- **Sem build de APK** para mudanças HTML/CSS/JS; `versionCode` só muda em mudança nativa (atual: 22). NUNCA build em versões puramente HTML/CSS/JS — só quando mexer em `capacitor.config.json`, plugin Capacitor ou permissões Android (ver `DEPLOY.md`).
- **O app nunca pode quebrar**; migrações não destrutivas e retrocompatíveis.
- **Cópia no desktop a cada versão:** `C:\Users\RBMarketing\Desktop\garagespot-index-vX.X.X.html`
- **Prompts para o Code:** completos e copy-paste, em 12 partes (Fase 0 backup com git tag; declaração de versão; leitura do código antes de editar; preservação; testes Playwright que falham em `pageerror`/`console.error`; validação e deploy `garagespot-app`→`garagespot-dev`→verificar Pages→cópia desktop, rollback após 3 tentativas; relatório; atualização de `CLAUDE.md` e `CHAT_HANDOFF.md`; declaração de validação; checklist).
- O chat de planejamento só envia prompt quando o Douglas pedir.
- Registro: tudo confirmado/futuro entra no handoff imediatamente.
- **Aviso fim de roadmap:** quando o Douglas pedir o "próximo prompt" e só restarem **Atualização do hotel** e **v2.0**, o planejador deve **AVISAR** que essas duas etapas ficam para o fim — a atualização do hotel só quando tudo estiver rodando 100%; a v2.0 só quando houver estrutura (banco/servidor) para isso.

## Especificação da Recarga (confirmada)
- **2 pontos** (padrão, configurável em Gestão): Ponto 1 = **8C/9C COMPARTILHADO** (uma tomada, um carro por vez); Ponto 2 = **1D INDIVIDUAL**.
- **Rótulo do ponto compartilhado:** livre → "8C / 9C"; em uso → a vaga real (8C ou 9C). **Iniciar recarga NÃO move o carro de vaga** (só move se o usuário pedir remanejamento).
- **Ícone no mapa = BOTÃO** que abre o painel Recarga, **distinto do clique na vaga**: raio amarelo = disponível; raio cinza = vaga parceira do ponto compartilhado quando ocupado; bateria animada = carregando; **bateria cheia ✓ = concluída**. Responsivo para celular e tablet (ancorado, sem transbordar).
- **Modos de tempo ao iniciar:** quantidade de horas OU hora final (um ajusta o outro).
- **Lista de carros priorizada:** 1º carro(s) da(s) vaga(s) do ponto (compartilhado = os dois separados); 2º fila; 3º demais. **Remanejamento** só quando necessário e pedido (banner sticky no mapa pedindo tap em vaga livre + `executarMove`).
- **Encerramento com cobrança:** até programado / até agora / outro horário; R$ = horas × valor/hora com arredondamento; **cortesia (valor 0) = R$ 0,00**.
- **Configuração em Gestão:** módulo on/off, pontos (compartilhado/individual), valor/hora, arredondamento (15/30, cima/baixo), cortesia, alertas.
- **Tempo exibido** em horas quando > 60 min ("3h 51min"); minutos quando < 60 min ("45min").
- **Fila:** botão "+ Adicionar carro à fila" no painel; ✕ para remover; quando ponto vagar, `_verificarFilaRecarga` oferece designar o próximo via `showModalAux`.
- **Após encerramento:** PDF (com operador + duração em horas + cortesia se aplicável) + entrada no histórico.

## Gestão (princípio geral)
- Gestão **habilita/desabilita módulos E configura cada um** — completo e bem feito.

## LGPD / dados
- O app guarda placas, apartamentos e fotos de hóspedes (dado pessoal). Manter postura básica de LGPD (finalidade, prazo de guarda das fotos, controle de acesso). Pesa mais no v2.0 (servidor central).

## Bugs conhecidos pendentes
- Dois carros no mesmo apto (GS separado) — validar
- Direita/esquerda vagas B
- Debug merge completo
- ✅ Editar número de apartamento nos detalhes → **resolvido na v1.9.4.4** (edição completa)
- Botão × remover plantão agora → entra na **v1.9.4.5**
- Badge tempo de passeio (avaliar remoção)

## Metodologia de planejamento (oficial)
- Sempre planejar detalhadamente antes do prompt
- Apresentar riscos e alternativas em cada decisão
- Protótipo HTML para qualquer mudança visual
- Consolidar escopo (o que entra + o que NÃO entra)
- Resumo antes de gerar o prompt
- Múltiplos prompts se a atualização for grande
- Documentar tudo no `CHAT_HANDOFF` para próximo chat

## Padrão dos prompts para o Claude Code
- Uma funcionalidade ou conjunto coeso por prompt
- Estrutura: contexto, regras, especificações, fases, deploy, docs
- Linguagem específica e literal (Opus 4.7)
- Listar explicitamente o que NÃO fazer
- Sempre: testar, debugar, atualizar `CLAUDE.md` + `CHAT_HANDOFF.md`
- Sempre finalizar com: sync, push master, deploy dev, **verificar Pages no ar**
- APK build SOMENTE quando necessário

## Fora do escopo deste handoff (registrado à parte)
- Estratégia de preço e venda (folder, pitch, valores, prospecção em Balneário Camboriú e região) — em documento de material de vendas separado.

## Última atualização deste handoff
v1.9.4.4 — 2026-05-31
