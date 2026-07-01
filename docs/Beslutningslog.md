---
titel: TeachingOS — Beslutningslog
dato: 2026-07-01
status: aktiv
relateret: TeachingOS_PRD_v0.1.md (§12)
---

# Beslutningslog

Korte beslutningsnotater (ADR-lignende) for TeachingOS. Kan bruges som
tekst til GitHub Issues — én Issue pr. beslutning, luk den med en kommentar
der linker til denne log.

------------------------------------------------------------------------

## B1 — LMS-eksportformat: Common Cartridge

**Status:** Besluttet · 2026-07-01

**Beslutning:** Eksport til LMS sker via **Common Cartridge** (kursuspakke).
QTI bruges kun som indlejret quiz-format inde i pakken, ikke som selvstændigt
eksportspor.

**Hvorfor:** Common Cartridge pakker et helt kursus (struktur + indhold +
quiz) og importeres af både Moodle og Canvas. Ét format frem for to
reducerer vedligehold.

**Konsekvens:** PRD §6 F14 sigter mod CC. Prioritet forbliver "Could"
(efter v1.0).

------------------------------------------------------------------------

## B2 — Studenterfeedback: manuel indtastning i første version

**Status:** Besluttet · 2026-07-01

**Beslutning:** Feedback indtastes **manuelt** i evalueringsnoten i første
version. Import fra eksterne værktøjer (spørgeskema, Kahoot m.m.) udskydes.

**Hvorfor:** Holder datamodellen enkel og undgår ekstern integration i MVP.
Understøtter GDPR-princippet om lokal, anonymiseret/aggregeret feedback.

**Konsekvens:** PRD §7 (evaluerings-frontmatter) og §9. Import kan blive et
senere "Could"-krav.

------------------------------------------------------------------------

## B3 — Lokal AI-model: Qwen 3 + nomic-embed-text

**Status:** Besluttet · 2026-07-01

**Beslutning:** Anbefalet standard i dokumentationen er **Qwen 3** til
generering og **nomic-embed-text** til RAG-embeddings. **Llama 3.1 8B**
angives som let fallback.

**Hvorfor:** Undervisning foregår på dansk; Qwen 3 leder på flersproget
kvalitet og er stærk til forløb, quizzer og kodeeksempler. Størrelse efter
hardware: 14B ved ~12 GB+ VRAM/RAM, ellers 8B; Llama 3.1 8B kører fra
~6 GB.

**Konsekvens:** Kun en anbefaling — brugeren kan vælge enhver Ollama-model.
Dokumenteres under AI-modul/offline-first.

------------------------------------------------------------------------

## B4 — Vault-struktur: én vault pr. uddannelse

**Status:** Besluttet · 2026-07-01

**Beslutning:** **Én vault pr. uddannelse** (ikke én stor fælles vault).

**Hvorfor:** Bedre Dataview-ydelse (mindre datamængde pr. vault) og renere
adskillelse mellem uddannelser.

**Konsekvens / afvejning:** Genbrug *på tværs* af uddannelser bliver
sværere. Afhjælpes ved et lille delt bibliotek-vault (eller delt mappe) til
aktivitets- og ressourcebiblioteket. Påvirker PRD §9 og skabelonstruktur.
