## MyClub – web_insp

Tento adresář obsahuje **Next.js / React aplikaci**, která slouží jako:

- **marketingový web** pro MyClub (moderní landing page, sekce Ceník, Funkce, Kontakt…)
- **dokumentační rozhraní** (`/docs`) pro vizi, zadání a roadmapu projektu

Hlavní HTML šablony MyClubu (statické `.html` soubory bez frameworku) jsou v kořeni repozitáře, tato aplikace je doplňuje jako "živá" inspirace a místo pro dokumentaci.

---

## Struktura

Zjednodušený přehled:

```text
web_insp/
  src/
    app/
      page.tsx          # Landing page MyClub
      cenik/            # Ceník (Next.js stránka)
      funkce/           # Přehled funkcí
      kontakt/          # Kontaktní stránka
      o-nas/            # O projektu / o MyClubu
      sluzby/           # Služby / produkty
      docs/             # Zobrazení markdown dokumentace
  content/
    docs/               # Všechny .md dokumenty pro /docs
      readme.md         # Jak používat dokumentaci
      overview.md       # Technický přehled systému
      vize.md           # Produktová vize MyClub
      web.md            # Zadání pro HTML šablony
      progress.md       # Průběh prací na webu
      timeline.md       # Roadmap a fáze projektu
      pricing.md        # Pricing / tarify
      admin.md          # Dokumentace admin rozhraní
      zadani1.md        # Zadání: převod AdminDocsPage do HTML
```

Stránka `/docs` automaticky načítá všechny `.md` soubory z `content/docs` a generuje z nich seznam dokumentace.

---

## Lokální spuštění

1. Nainstalujte závislosti (v adresáři `web_insp`):

   ```bash
   npm install
   # nebo
   pnpm install
   ```

2. Spusťte vývojový server:

   ```bash
   npm run dev
   ```

3. Otevřete [http://localhost:3000](http://localhost:3000) v prohlížeči.

- `/` – hlavní landing page MyClub
- `/cenik`, `/funkce`, `/kontakt`, `/o-nas`, `/sluzby` – dílčí stránky
- `/docs` – přehled dokumentace
- `/docs/<slug>` – konkrétní markdown dokument (např. `/docs/overview`)

---

## Jak aktualizovat dokumentaci

- Otevřete soubory v `web_insp/content/docs/*.md`.
- Úpravy textu se po uložení okamžitě projeví na odpovídající `/docs/<slug>` stránce.
- Po přidání nového `.md` souboru se automaticky objeví i v seznamu na `/docs`.

Pro navigaci v dokumentaci a detailnější popis viz `/docs/readme` v běžícím webu.

