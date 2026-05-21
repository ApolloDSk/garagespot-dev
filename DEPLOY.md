# GarageSpot — Checklist de Deploy

## Toda atualização DEVE seguir este checklist

### 1. Antes de começar
- [ ] Versão definida (v1.9.x ou v1.9.x.y — NUNCA v2.0)
- [ ] versionCode incrementado
- [ ] Mudanças isoladas em www/index.html e arquivos relacionados

### 2. Commit e push em garagespot-app
- [ ] Commit com mensagem descritiva no master
- [ ] Push em ApolloDSk/garagespot-app

### 3. Sync automática para garagespot-dev
- [ ] Copiar www/index.html (e demais arquivos modificados) para repo garagespot-dev
- [ ] Commit + push em ApolloDSk/garagespot-dev
- [ ] Aguardar até 2 min pela propagação do GitHub Pages
- [ ] Verificar via curl que apollodsk.github.io/garagespot-dev/ serve a versão nova

### 4. Build do APK
- [ ] GarageSpot-dev.apk: COM server.url (online, atualização automática)
- [ ] Versão produção: SEM server.url (offline empacotado) — só quando aprovada para hotel

### 5. NUNCA tocar em garagespot-hotelgumz
- Salvo aprovação explícita do Douglas
- Hotel está em uso pelo cliente — não pode quebrar

### 6. Documentação
- [ ] CLAUDE.md atualizado com nova versão
- [ ] CHAT_HANDOFF.md atualizado

### 7. Confirmar com Douglas
- Reportar entregáveis
- Aguardar validação antes de avançar para próxima versão
- Se houver bugs, criar v1.9.x.y de correção
