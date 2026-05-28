# GarageSpot — Handoff para novo chat de planejamento

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
- Produção (tablet do hotel): garagespot-hotelgumz → apollodsk.github.io/garagespot-hotelgumz/
- Dev (celular Douglas, APK online): garagespot-dev → apollodsk.github.io/garagespot-dev/
- Repo principal de edição: garagespot-app (master)
- NUNCA modificar garagespot-hotelgumz sem aprovação explícita

## Regras críticas
- v2.0 RESERVADA para migração com banco de dados + servidor
- Atualizações atuais: v1.9.x, v1.9.x.y (nunca pular para 2.0)
- Toda atualização vai PRIMEIRO no dev (sync automática), depois aprovação manual para hotel
- APK dev online (server.url) atualiza automaticamente; APK hotel offline empacotado
- **NÃO buildar APK em versões puramente HTML/CSS/JS** — só quando mexer em capacitor.config.json, plugin Capacitor ou permissões Android. Ver DEPLOY.md

## Versão atual
- Em produção (hotel): versão estável anterior à v1.8
- Em dev: v1.9.4.1.6
- Storage com backup rotativo de 3 slots + bloqueio anti-perda; saves forçados em visibilitychange/pagehide; canvas assinatura inicializa via IntersectionObserver+retry; preview modal de foto NCI; ordenação vistorias com fallback múltiplo; PDF checkout aceita fotos legadas; race condition fotos resolvida com bloqueio de botão. **30 testes Playwright automatizados em tests/specs/**. Próxima etapa: v1.9.4.3.1 (Recarga visual)

## Roadmap
1. ✅ v1.9.4.1.6 — Bugs Q (PDF fotos), R (assinatura touch), S (preview fotos), T (designar pós-checkin reforçado), U (ordenação vistorias), W (storage refactor c/ 3 backups + bloqueio anti-perda), X (race fotos) + infraestrutura Playwright (8 specs, 30 testes)
2. ✅ v1.9.4.1.5 — Bugs O+P (eliminação CRÍTICA do NCI antigo em Nova Vistoria + Designar agora pós-checkin) + Bug J (PDF checkout com vistorias+fotos) + Bug L (vistoria preservada após designar) + Bug N (PDF compartilhar real) + Melhoria 3 (atrasados em Hoje) + toggles em expansões + interatividade completa
2. ✅ v1.9.4.1.4 — Bug G (preview assinatura na vista interna), Bug H (validar canvas vazio em coletar depois), Bug I (designação pós-checkin sem pedir operador nem abrir NCI) + Nova Vistoria em Detalhes via menu de vistorias
2. ✅ v1.9.4.1.3 — Bug F (duplicação assinatura ao Concluir no NCI) + Reforma do Painel com agrupadores em 2 colunas e overlays de expansão
3. ✅ v1.9.4.1.2 — Correções finais vistoria (assinatura z-index, sem duplicação, sem modal vire celular, câmera funcional, operador pré-preenchido pos_checkin)
3. ✅ v1.9.4.1.1 — Correções vistoria (1 dedo, assinatura, landscape, desativar, revisão) + etapa de fotos + designação automática via vaga + Hospedados corrigido
3. ⏳ v1.9.4.3 — Recarga visual (bateria animada)
4. ⏳ v1.9.4.4 — Recarga fluxo
5. ⏳ v1.9.4.5 — Recarga finalização (PDF + config + painel)
6. ⏳ v1.9.4.6 — Mapa: bugs + drag&drop + UX + Gestão (qualidade vida)
7. ⏳ v1.9.4.7 — Tema + Relatórios + Histórico
8. ⏳ v1.9.4.8 — Google Drive backup (APK build necessário)
9. 🟢 Atualização do app do hotel (versão estabilizada)
10. ⏳ v2.0 — Banco de dados + servidor externo

## Bugs conhecidos pendentes
- Dois carros no mesmo apto (GS separado) — validar
- Direita/esquerda vagas B
- Debug merge completo
- Editar número de apartamento nos detalhes
- Botão × remover plantão agora
- Badge tempo de passeio (remover)

## Metodologia de planejamento (oficial)
- Sempre planejar detalhadamente antes do prompt
- Apresentar riscos e alternativas em cada decisão
- Protótipo HTML para qualquer mudança visual
- Consolidar escopo (o que entra + o que NÃO entra)
- Resumo antes de gerar o prompt
- Múltiplos prompts se a atualização for grande
- Documentar tudo no CHAT_HANDOFF para próximo chat

## Padrão dos prompts para o Claude Code
- Uma funcionalidade ou conjunto coeso por prompt
- Estrutura: contexto, regras, especificações, fases, deploy, docs
- Linguagem específica e literal (Opus 4.7)
- Listar explicitamente o que NÃO fazer
- Sempre: testar, debugar, atualizar CLAUDE.md + CHAT_HANDOFF.md
- Sempre finalizar com: sync, push master, deploy dev, verificar Pages
- APK build SOMENTE quando necessário

## Última atualização deste handoff
v1.9.4.1.6 — 2026-05-28
