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
- Em dev: v1.9.4.1
- Próxima etapa: validação do Douglas no celular

## Roadmap
1. ✅ v1.9.4.1 — Vistoria + Check-in + Designação (NCI página única + ativação contextual)
2. ⏳ v1.9.4.2 — Recarga visual (bateria animada)
3. ⏳ v1.9.4.3 — Recarga fluxo
4. ⏳ v1.9.4.4 — Recarga finalização (PDF + config + painel)
5. ⏳ v1.9.4.5 — Mapa: bugs + drag&drop + UX + Gestão (qualidade vida)
6. ⏳ v1.9.4.6 — Tema + Relatórios + Histórico
7. ⏳ v1.9.4.7 — Google Drive backup (APK build necessário)
8. 🟢 Atualização do app do hotel (versão estabilizada)
9. ⏳ v2.0 — Banco de dados + servidor externo

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
v1.9.4.1 — 2026-05-21
