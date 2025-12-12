## MyClub – marketingový a dokumentační web

Tento repozitář obsahuje **Next.js / React aplikaci MyClub**. Slouží jako:

- **marketingový web** pro MyClub (landing page, Ceník, Funkce, FAQ, Kontakt…)
- **dokumentační rozhraní** (`/docs`) pro vizi, technický přehled, pricing a roadmapu

MyClub je moderní SaaS platforma pro sportovní kluby. Umožňuje mimo jiné spravovat týmy, hráče, zápasy, obsah webu, sponzory, newslettery a scoreboard.

Detailní produktovou vizi najdete v `/docs/vize`, technický přehled backendu a celé platformy v `/docs/overview`.

---

## Struktura projektu

Zjednodušený přehled důležitých částí repozitáře:

```text
MyCLUB/
  src/
    app/
      page.tsx              # Landing page MyClub
      cenik/                # Ceník
      funkce/               # Přehled funkcí
      faq/                  # FAQ
      kontakt/              # Kontaktní stránka
      o-nas/                # O projektu / o MyClubu
      sluzby/               # Služby / produkty
      produkty/             # Samostatné produkty a moduly
      obchodni-podminky/    # Obchodní podmínky
      docs/                 # Index dokumentace (/docs)

  content/
    docs/                   # Markdown dokumentace pro /docs
      readme.md             # Jak používat dokumentaci
      vize.md               # Produktová vize MyClub
      overview.md           # Technický přehled (Go backend + frontend)
      web.md                # Zadání pro HTML šablony
      pricing.md            # Pricing / tarify
      progress.md           # Průběh prací na webu
      timeline.md           # Roadmap a fáze projektu
      admin.md              # Dokumentace admin rozhraní
      zadani1.md            # Zadání: převod AdminDocsPage do HTML

  public/                   # Veřejné assety pro Next.js
  images/                   # Dodatečné obrázky / loga

  package.json              # NPM skripty a závislosti
  tsconfig.json             # TypeScript konfigurace
  next.config.ts            # Next.js konfigurace
  Dockerfile                # Build a běh aplikace v Dockeru
  docker-compose.yml        # Jednoduché spuštění přes Docker Compose
```

Stránka `/docs` automaticky načítá všechny `.md` soubory z `content/docs` a generuje z nich seznam dokumentace.

---

## Tech stack

- **Next.js 16 (App Router)** + **React 19**
- **TypeScript**
- **Tailwind CSS 4**
- **Radix UI** + **lucide-react** (ikony)
- **react-markdown + remark-gfm** pro zobrazení Markdownu z `content/docs`
- **Docker** image pro produkční nasazení

Celá platforma MyClub (včetně admin části a API) je navržena s backendem v **Go (Gin)**, databází **PostgreSQL** a další infrastrukturou – viz `/docs/overview`.

---

## Lokální spuštění

### 1. Instalace závislostí

V kořenovém adresáři repozitáře spusťte:

```bash
npm install
```

### 2. Vývojový server

```bash
npm run dev
```

Otevřete [http://localhost:3000](http://localhost:3000) v prohlížeči.

Klíčové stránky:

- `/` – hlavní landing page MyClub
- `/cenik` – přehled plánů a pricingu
- `/funkce` – funkce platformy
- `/faq` – často kladené dotazy
- `/kontakt` – kontaktní stránka
- `/o-nas`, `/sluzby`, `/produkty`, `/obchodni-podminky` – doplňkové stránky
- `/docs` – přehled dokumentace
- `/docs/<slug>` – konkrétní dokument (např. `/docs/vize`, `/docs/overview`)

### 3. Build a produkční režim

```bash
npm run build
npm start
```

---

## Spuštění přes Docker

### Build lokálního Docker image

```bash
npm run docker:build
```

### Rychlé spuštění containeru

```bash
npm run docker:run
```

### Docker Compose

```bash
npm run docker:up
```

Aplikace běží na portu `3000`. Konfigurace je v `Dockerfile` a `docker-compose.yml`.

---

## Dokumentace (`/docs`)

Všechny hlavní podklady k projektu jsou v `content/docs` a dostupné přes `/docs`:

- **Vize produktu** – `/docs/vize`
- **Technický přehled platformy** – `/docs/overview`
- **Zadání HTML webu** – `/docs/web`
- **Pricing a plány** – `/docs/pricing`
- **Admin dokumentace** – `/docs/admin`
- **Průběh prací** – `/docs/progress`
- **Roadmap & fáze projektu** – `/docs/timeline`
- **Zadání převodu admin stránky do HTML** – `/docs/zadani1`

Stručný návod, jak s dokumentací pracovat a jak přidávat nové `.md` soubory, je v `/docs/readme`.

---

## Roadmap a stav projektu

Souhrnnou roadmapu a fáze projektu najdete v kořenovém souboru `TIMELINE.md` a také v dokumentu `/docs/timeline`.

Detailní check-list konkrétních úkolů pro HTML šablony a další práci je v `/docs/progress`.

---

## Platby a GoCardless (plán)

Do budoucna je počítáno s integrací **GoCardless** jako poskytovatele plateb (inkaso / předplatné) pro tarifní plány MyClubu.

Základní směr integrace:

- **Konfigurace přes prostředí** – API klíče a webhook secret pouze v `.env.local` / produkčních secretech:
  - `GOCARDLESS_API_KEY`
  - `GOCARDLESS_ENVIRONMENT` (`sandbox` / `live`)
  - `GOCARDLESS_WEBHOOK_SECRET`
- **Backend logika v Next.js** – samostatné API route handlery (plán):
  - `POST /api/gocardless/checkout` – vytvoření payment linku / předplatného podle zvoleného tarifu
  - `POST /api/gocardless/webhook` – příjem a ověřování webhooků (podle `GOCARDLESS_WEBHOOK_SECRET`)
- **Sdílená logika** v helperu, např. `src/lib/gocardless.ts`:
  - načtení konfigurace z `process.env`
  - vytvoření GoCardless klienta (po přidání oficiální GoCardless SDK)
- **Napojení na UI**:
  - stránka `/cenik` bude používat tyto API routy pro vytvoření platby / předplatného
  - budoucí sekce v administraci může zobrazovat stav předplatného klubu

Implementace SDK, datových modelů a bezpečnostních kontrol je záměrně mimo rámec tohoto repozitáře – zde je popsán pouze architektonický plán a potřebné proměnné prostředí.

---

## UI / UX a vizuální směr

Web MyClub je navržen jako **moderní B2B SaaS landing & marketing web** v **světlém (white) režimu**.

Designové principy inspirované stylem jako [Untitled UI](https://www.untitledui.com/):

- **Světlé plátno** – bílé pozadí, jemné rozdělovací linie a sekce.
- **Karty a panely** – informace seskupené do karet (pricing, funkce, reference, FAQ) s decentními rámečky a shadow.
- **Typografie** – čitelná sans-serif, zvýrazněné nadpisy, menší sekundární text v tlumené barvě.
- **Barvy** – jedna primární značka (MyClub), doplňkové neutrální odstíny pro panely, badge a oddělovače.
- **Komponenty** – konzistentní použití buttonů, badge, tabů, gridů a karet napříč stránkami (`/`, `/cenik`, `/funkce`, `/faq`, `/kontakt`…).

Technicky je UI postavené na **Tailwind CSS 4** + vlastních komponentách (tlačítka, karty, taby…) a může být dále laděno do vzhledu „Untitled UI‑like“:

- vyčištěním nadbytečných stylů z původních inspirací,
- sjednocením spacingu, zaoblení a borderů,
- doplněním konzistentní sady stavů (hover, focus, disabled),
- rozšířením komponent o varianty (např. "primary", "secondary", "ghost") pro SaaS scénáře.

Všechny tyto kroky spadají do UI/UX polish fází popsaných v `TIMELINE.md`.
