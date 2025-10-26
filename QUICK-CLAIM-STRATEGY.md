# ⚡ Quick Claim Strategy - Bounty Hunter

## 🎯 OBJETIVO

Reclamar bounties INMEDIATAMENTE cuando aparezcan, antes que la competencia.

---

## 🚨 CUANDO RECIBAS UNA ALERTA

### Paso 1: Verificación Rápida (30 segundos)

```bash
# Ver alerta
gh issue list --repo INDIGOAZUL/INDIGOAZUL --label "bounty-alert" --state open

# Ver detalles del bounty
gh issue view <ISSUE_NUM> --repo <OWNER>/<REPO> --json title,body,assignees,labels,comments
```

**Criterios de GO/NO-GO:**
- ✅ **GO** si: No tiene assignees, monto $100+, tech stack conocido
- ❌ **NO-GO** si: Ya asignado, hardware especializado, >40h de trabajo

---

### Paso 2: Claim INMEDIATO (15 segundos)

**Si es GO, reclamar AHORA:**

```bash
gh issue comment <ISSUE_NUM> --repo <OWNER>/<REPO> --body "I'd like to claim this bounty!

**Quick Info:**
- Starting work immediately
- Will provide updates every 24h
- Expected completion: [X] days

Let me know if you need any additional information!"
```

**CRÍTICO:** Hazlo en <1 minuto de ver la alerta. La competencia es rápida.

---

### Paso 3: Análisis Detallado (5 minutos)

**DESPUÉS de reclamar, analiza:**

```bash
# Ver README del repo
gh repo view <OWNER>/<REPO> --json description,readme

# Ver el issue completo
gh issue view <ISSUE_NUM> --repo <OWNER>/<REPO> --web

# Verificar si hay contribution guidelines
gh repo view <OWNER>/<REPO> --json url
# Abrir: <url>/blob/main/CONTRIBUTING.md
```

**Preguntas a responder:**
1. ¿Cuáles son los pasos exactos para resolver?
2. ¿Qué stack/lenguaje se usa?
3. ¿Hay tests que debo pasar?
4. ¿Cuál es el proceso de PR?
5. ¿Cuánto tiempo me tomará realmente?

---

### Paso 4: Setup de Workspace (10 minutos)

**Opción A: Automático (recomendado)**
```bash
# Usar Workspace Setup Bot
gh workflow run workspace-setup-bot.yml \
  --repo INDIGOAZUL/INDIGOAZUL \
  -f repo_url="https://github.com/<OWNER>/<REPO>" \
  -f issue_number="<NUM>" \
  -f should_fork="true"
```

**Opción B: Manual**
```bash
# Fork (si es necesario)
gh repo fork <OWNER>/<REPO> --clone=true

# O clone directo
git clone https://github.com/<OWNER>/<REPO>.git
cd <REPO>

# Crear branch
git checkout -b bounty-issue-<NUM>

# Instalar deps
npm install  # o cargo build, etc.
```

---

### Paso 5: Actualizar Tracker (2 minutos)

```bash
gh workflow run my-bounty-tracker.yml \
  --repo INDIGOAZUL/INDIGOAZUL \
  -f action="add" \
  -f bounty_url="https://github.com/<OWNER>/<REPO>/issues/<NUM>" \
  -f amount="<AMOUNT>" \
  -f status="claimed"
```

---

## ⏱️ TIMELINE TOTAL

| Paso | Tiempo | Acción |
|------|--------|--------|
| Verificación | 30s | Ver alerta, decidir GO/NO-GO |
| **Claim** | **15s** | **Comentar reclamación** |
| Análisis | 5min | Leer issue completo, requirements |
| Setup | 10min | Fork/clone, install deps |
| Tracker | 2min | Actualizar tracking |
| **TOTAL** | **~18min** | Bounty reclamado y listo para trabajar |

---

## 🎯 REPOS PRIORITARIOS

### CRITICAL Priority (Claim SIEMPRE)
- **Expensify/App** - $250-$10,000 - React Native/JavaScript
- Cualquier bounty $500+

### HIGH Priority (Claim si tech stack coincide)
- ethereum/go-ethereum - Go
- ethereum/solidity - Solidity
- OpenZeppelin/openzeppelin-contracts - Solidity
- Uniswap/v3-core - Solidity
- aave/aave-v3-core - Solidity

### MEDIUM Priority (Evaluar caso por caso)
- nodejs/node - C++/JavaScript
- microsoft/vscode - TypeScript
- facebook/react - JavaScript/TypeScript
- vercel/next.js - TypeScript

---

## 🚫 EVITAR ESTOS BOUNTIES

**NO reclamar si:**
1. ❌ Requiere hardware especializado (ej: Tenstorrent ML)
2. ❌ Tasa horaria <$10/hora
3. ❌ Stack desconocido sin tiempo para aprender
4. ❌ Requiere >40 horas de trabajo
5. ❌ Testing bounties con requisitos extensos (ej: screenpipe)
6. ❌ Security reports ya rechazados
7. ❌ Repos sin programa oficial de bounties

---

## 📋 TEMPLATES DE MENSAJES

### Template 1: Claim Simple
```markdown
I'd like to claim this bounty! Starting work now.

**ETA:** [X] days
**Approach:** [Brief 1-2 sentence description]
```

### Template 2: Claim con Preguntas
```markdown
I'd like to claim this bounty!

**Quick questions:**
1. [Question if needed]
2. [Question if needed]

Starting implementation while waiting for clarification.
```

### Template 3: Claim Competitivo (si hay otros interesados)
```markdown
I'd like to claim this bounty!

**Why me:**
- [Relevant experience]
- Starting immediately
- Can deliver in [X] days

Already setting up workspace. First update in 24h.
```

---

## 🎯 TECH STACK MATCH

**Tu stack fuerte:**
- ✅ JavaScript/TypeScript
- ✅ React/React Native
- ✅ Node.js
- ✅ Web3/Solidity (básico)
- ✅ Python (básico)

**Aceptable con investigación:**
- ⚠️ Go
- ⚠️ Rust
- ⚠️ C++

**Evitar:**
- ❌ ML/AI especializado
- ❌ Hardware-specific (CUDA, etc.)
- ❌ iOS native (Swift/Objective-C)
- ❌ Android native (Kotlin/Java)

---

## 📊 MONITOREO CONTINUO

### Verificar alertas cada hora
```bash
# Ver nuevas alertas
gh issue list --repo INDIGOAZUL/INDIGOAZUL --label "bounty-alert" --state open

# Ver últimos bounties encontrados
cat ~/bounty-hunter-repo/verified-bounty-opportunities.json | head -50
```

### Workflows ejecutan automáticamente:
- Verified Repos Hunter: Cada 3h
- General Bounty Hunter: Cada 6h
- Notifications: Cada 3h

---

## 🏆 OBJETIVO DE ÉXITO

**Meta Semanal:** Reclamar 1-2 bounties
**Meta Mensual:** $1,000-$2,000 ganados
**Tasa horaria objetivo:** $15-25/hora

---

## 🔗 LINKS RÁPIDOS

- **Alerts:** https://github.com/INDIGOAZUL/INDIGOAZUL/issues?q=is%3Aissue+label%3Abounty-alert+is%3Aopen
- **Expensify:** https://github.com/Expensify/App/issues?q=is%3Aopen+is%3Aissue+label%3A%22Help+Wanted%22
- **Workflows:** https://github.com/INDIGOAZUL/INDIGOAZUL/actions
- **My Tracking:** ~/bounty-hunter-repo/my-bounty-tracking.json

---

**Última actualización:** 26 de octubre, 2025
**Sistema:** ✅ Operacional 100%
