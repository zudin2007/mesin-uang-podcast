# CLAUDE.md — Mesin Uang Podcast Repository Guide

This file documents the repository structure, conventions, and workflows for AI assistants working on the **Mesin Uang** podcast content repository.

---

## Project Overview

**Mesin Uang** ("Money Machine") is an Indonesian-language podcast by IFBTC (Islamic Finance & Bitcoin Community Indonesia). The podcast covers passive income, halal investing, Islamic finance, and cryptocurrency for Muslim Indonesians.

- **Host:** Izzuddin Edi Siswanto — 21+ years Islamic finance practitioner, OJK & Bappenas consultant, Founder IFBTC Indonesia
- **Platform:** Spotify ([open.spotify.com/show/033GdByxOvu264tMkk1SEb](https://open.spotify.com/show/033GdByxOvu264tMkk1SEb))
- **Language:** Bahasa Indonesia (all content)
- **Frequency:** 1 episode per week (target: Sunday), 15–35 minutes each

This is a **content repository** — there is no application code, build system, or test suite. All files are Markdown documents.

---

## Repository Structure

```
mesin-uang-podcast/
├── README.md          # Master episode index + per-episode details
├── ROADMAP.md         # Planned future episodes grouped by series
├── TEMPLATE.md        # Canonical template for new episode shownotes
├── CLAUDE.md          # This file
├── .gitignore         # (empty — no build artifacts to ignore)
└── episodes/          # One Markdown file per published episode
    ├── .gitkeep
    ├── ep01-jebakan-sunyi.md
    ├── ep02-mindset-mesin-uang.md
    ├── ep03-mesin-uang-edisi-crypto.md
    ├── ep04-gaji-numpang-lewat.md
    └── ep05-berhenti-menjual-waktu.md
```

---

## File Conventions

### Episode Shownote Files (`episodes/`)

**Naming:** `epXX-kebab-case-short-title.md`
- Two-digit zero-padded episode number (e.g., `ep01`, `ep10`)
- Kebab-case title derived from the episode title (abbreviated if long)
- Examples: `ep01-jebakan-sunyi.md`, `ep05-berhenti-menjual-waktu.md`

**Structure:** Follow `TEMPLATE.md` exactly:

```markdown
# Ep. XX — [Judul Episode]

**Podcast:** Mesin Uang by IFBTC
**Durasi:** XX menit
**Spotify:** [Dengarkan di sini](SPOTIFY_EPISODE_URL)
**Rilis:** [Tanggal or Bulan Tahun]

---

## Deskripsi Episode

[Episode description — same text published on Spotify]

🎙️ *Mesin Uang by IFBTC — Ekosistem Passive Income untuk Muslim Indonesia*

---

## Poin Utama

- Poin 1
- Poin 2
- Poin 3

---

## Referensi

- Referensi 1

---

## Lanjutan

- Episode sebelumnya: [Ep. XX — Judul](epXX-nama-file.md)
- Episode berikutnya: [Ep. XX — Judul](epXX-nama-file.md)
```

**Notes:**
- The `## Referensi` section may be omitted if the episode has no external references.
- The `## Lanjutan` section uses relative links within `episodes/` (e.g., `ep04-gaji-numpang-lewat.md`), except `ROADMAP.md` which is referenced as `../ROADMAP.md`.
- For the most recent episode, use `../ROADMAP.md` as the "next" link.

---

## README.md Structure

`README.md` has two synchronized sections that must both be updated when an episode is added:

1. **Index table** — compact overview of all published episodes:
   ```markdown
   | # | Judul | Topik | Durasi | Link |
   |---|-------|-------|--------|------|
   | 01 | [Title](#anchor) | Short topic description | XX mnt | [▶ Spotify](URL) |
   ```
   - The anchor in the title link follows GitHub's auto-anchor format (lowercase, spaces → `-`, special chars stripped).

2. **Detail section** — one `###` block per episode:
   ```markdown
   ### Ep. 01 — Jebakan Sunyi
   **Durasi:** 2 menit | **Rilis:** Juni 2026
   **Topik:** One-line topic summary

   > Pull quote from the episode

   📎 [Shownotes](episodes/epXX-name.md) | [▶ Dengarkan](SPOTIFY_URL)
   ```

---

## ROADMAP.md Structure

Tracks all episode planning. Two main sections:

- **Sudah Publish** — table of live episodes (status `✅ Live`)
- **Pipeline (Dalam Perencanaan)** — grouped by content series

When an episode is published, move its row from Pipeline to the Published table and mark `✅ Live`.

**Content series currently planned:**
| Series | Episodes |
|--------|----------|
| Passive Income Halal | Ep 06–09 (reksa dana, ORI/SBN, DIRE/REIT, saham dividen) |
| Crypto & Islamic Finance | Ep 10–14 (Bitcoin halal/haram, stablecoin, Kaspa, DeFi, tokenisasi) |
| Mindset & Sistem | Ep 15–18 (3-Layer system, compounding, skill as asset, zakat kripto) |
| OJK & Regulasi | Ep 19–21 (POJK 27/2024, DAKS, DSN-MUI fatwa) |

---

## Workflow: Adding a New Episode

When a new episode is recorded and published on Spotify:

1. **Create shownote file** in `episodes/` using `TEMPLATE.md` as the base.
   - File name: `epXX-short-title.md`
   - Fill in all sections (Deskripsi, Poin Utama, Referensi, Lanjutan)

2. **Update `README.md`:**
   - Add a row to the index table (maintain ascending order by episode number)
   - Add a `###` detail block in the Detail section (below the previous episode's block)
   - Update the previous episode's shownote to add the "next episode" link if it pointed to ROADMAP

3. **Update `ROADMAP.md`:**
   - Move the episode row from Pipeline to the Sudah Publish table
   - Change status to `✅ Live`

4. **Update the previous episode's shownote:**
   - Change `## Lanjutan` → episode berikutnya from `../ROADMAP.md` to the new episode file

---

## Key Domain Terms

| Term | Meaning |
|------|---------|
| Mesin Uang | "Money Machine" — the podcast name and core concept |
| IFBTC | Islamic Finance & Bitcoin Community Indonesia |
| Passive income | Income generated without active time exchange |
| Halal | Islamically permissible |
| Riba | Interest/usury — forbidden in Islamic finance |
| Gharar | Excessive uncertainty — forbidden in Islamic finance |
| Shownotes | Episode companion document (the files in `episodes/`) |
| OJK | Otoritas Jasa Keuangan — Indonesia's financial regulator |
| DSN-MUI | Dewan Syariah Nasional — Indonesia's Islamic finance fatwa body |
| SBN / ORI | Indonesian government bonds (state securities / retail bonds) |
| DIRE / REIT | Real estate investment funds in Indonesia |
| Reksa dana | Mutual fund |
| DES | Daftar Efek Syariah — OJK's list of Sharia-compliant securities |
| ISSI | Indeks Saham Syariah Indonesia — Islamic stock index |
| 3-Layer System | IFBTC's tiered revenue model: L1 (cashflow), L2 (products), L3 (institution) |

---

## Content Tone & Style

- All content is in **Bahasa Indonesia**.
- Tone is direct and practical — not motivational fluff, not religious lecturing.
- Claims are backed by data, research, or named references.
- The standard sign-off line for episode descriptions is:
  `🎙️ *Mesin Uang by IFBTC — Ekosistem Passive Income untuk Muslim Indonesia*`
- Avoid adding content that is not grounded in Islamic finance principles or Indonesian market context.

---

## What AI Assistants Should and Should Not Do

**Do:**
- Follow the TEMPLATE.md structure exactly for new episode files
- Keep all text in Bahasa Indonesia
- Maintain the episode numbering and file naming conventions
- Update all three places (episode file, README.md, ROADMAP.md) when adding an episode
- Use relative links between episode files

**Do not:**
- Add code files, build scripts, or non-Markdown assets
- Change the established episode file naming pattern
- Write content in English (except for technical terms that are conventionally used in English in Indonesian finance discourse)
- Invent Spotify URLs — only use URLs provided by the repository owner
- Add episode entries to README.md without a corresponding file in `episodes/`
