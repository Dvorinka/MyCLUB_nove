# MyClub – Roadmap & Timeline (souhrn)

Tento soubor shrnuje *fáze prací* na projektu MyClub napříč celým repozitářem:

- produktová vize a dlouhodobý cíl (`/docs/vize`)
- technický návrh celé platformy (`/docs/overview`)
- zadání pro veřejný HTML web (`/docs/web`)
- pricing a obchodní model (`/docs/pricing`)
- průběžný postup prací (`/docs/progress`)
- detailní roadmapa v dokumentační části (`/docs/timeline`)

Kořenový `TIMELINE.md` je „velký přehled“, na který se můžete dívat bez nutnosti lézt do všech jednotlivých `.md` souborů.

---

## 0. Aktuální stav

Shrnutí podle `content/docs/progress.md` a HTML šablon:

- ✅ Na homepage (`index.html`) je hotová sekce s videem, carousel recenzí a upravený footer.
- ✅ Navigace je zjednodušená (Domů, O nás, Funkce, Integrace, Ceník, Podpora, Kontakt), ale **stále obsahuje zbytky demo mega‑menu** – nutný úklid.
- ✅ V `assets2/` jsou připravené základní obrázky (soubory/statistiky/vyhledávání/sportcreative/loga MyClubu…).
- ✅ V Next.js aplikaci (`/src/app`) existuje moderní landing page a několik podstránek:
  - `/` (landing), `/cenik`, `/funkce`, `/faq`, `/kontakt`, `/o-nas`, `/sluzby`, `/produkty`, `/obchodni-podminky`
- ✅ V `content/docs` je kompletní dokumentace:
  - `vize.md` – produktová vize
  - `overview.md` – technický přehled (Go backend + moderní frontend)
  - `web.md` – zadání pro HTML šablony
  - `pricing.md` – pricing
  - `admin.md` – admin dokumentace
  - `progress.md` – průběh prací na HTML webu
  - `timeline.md` – roadmapa (podrobná verze tohoto souhrnu)
  - `zadani1.md` – úkol: převést AdminDocsPage do čistého HTML

Cílový stav v této fázi: **jednotná roadmapa v kořeni (tento soubor) + detailní podklady v `content/docs/*.md`.**

---

## 1. Fáze – Dokončení statických HTML šablon

Cíl: mít **konzistentní marketingový web** v čistém HTML/CSS (bez zbytků demo šablon, bez zásahů do `<head>` a bez JS, pokud nutně není potřeba).

### Stránky, které se mají používat

Podle `hlavni_akce.md` a `PROGRESS.md` je cílová sada HTML souborů:

- `index.html` – homepage
- `o-nas.html`
- `funkce.html`
- `integrace.html`
- `cenik.html`
- `reference.html`
- `dokumentace.html`
- `podpora.html`
- `faq-page.html` (případně později přejmenovat na `faq.html`)
- `kontakt.html`
- `kariera.html`, `kariera-detail.html`
- `sluzby.html`
- `zmeny.html`
- `obchodni-podminky.html`
- `reklamace.html`
- `gdpr-page.html`
- `404.html`

### Konkrétní úkoly

- [ ] **Dokončit navigaci v `index.html`**
  - odstranit všechny odkazy na `home-page-02.html` až `home-page-35.html`
  - odstranit staré mega‑menu „Pages“ a další demo části
  - sjednotit strukturu menu (Domů, O nás, Funkce, Integrace, Ceník, Podpora, Kontakt)
- [ ] **Zkopírovat aktuální header + footer do všech cílových HTML stránek** (viz seznam výše)
- [ ] **Odstranit blog sekce** z původní šablony na všech stránkách, kde ještě zůstaly
- [ ] **Zkontrolovat responzivitu** po úpravách (mobil / tablet / desktop), bez změn v JS

Detailní checklist viz také `/docs/progress` a `/docs/timeline` (sekce „Fáze 1“).

---

## 2. Fáze – Obsah a vizuální doplnění

Cíl: přiblížit se reálnému nasazení – **vyplněný obsah a lepší využití assetů**.

- [ ] **Doplnit reálný obsah ceníku** podle `/docs/pricing`:
  - tarify (LITE / STANDARD / PRO / SELF‑HOSTED)
  - měsíční / roční ceny a případné jednorázové setup poplatky
- [ ] **Doplnit obsah stránek „O nás“, „Funkce“, „Podpora“** podle `/docs/vize` a `/docs/overview`:
  - stručně vysvětlit, komu MyClub pomáhá
  - jaké oblasti systém pokrývá (zápasy, obsah, fanoušci, sponzoři…)
- [ ] **Vložit reálné YouTube video** – nahradit `YOUR_VIDEO_ID` v sekci videa na `index.html`
- [ ] **Zapojit obrázky z `assets2/` do klíčových sekcí** (funkce, statistiky, soubory, značka SportCreative…)
- [ ] **Doplnit reference** (až budou reálné texty) na homepage i na `reference.html`
 - [ ] **UI/UX polish v "SaaS stylu"** – sjednotit spacing, karty, typografii a komponenty tak, aby web působil jako moderní B2B SaaS (inspirace např. Untitled UI, ale vlastní implementace přes Tailwind komponenty).

---

## 3. Fáze – Admin dokumentace jako HTML stránka

Cíl: mít **samostatnou dokumentační HTML stránku** pro administraci, založenou na existující React komponentě.

Zadání je zapsané v `content/docs/zadani1.md`:

> „převést admin docs page do HTML, CSS, JS místo TSX (`AdminDocsPage.tsx`) a nasadit ji jako stránku pro dokumentaci projektu.“

Konkrétní kroky:

- [ ] **Najít komponentu `AdminDocsPage.tsx`** v projektu / referenčním kódu
- [ ] **Převést rozložení a obsah do čistého HTML + CSS (+ případně drobný JS)**
  - zachovat strukturu sekcí, nadpisy, tipy, checklisty
  - nepoužívat React ani žádný bundler
- [ ] **Vytvořit stránku `dokumentace.html`** v sadě statických šablon
- [ ] **Napojit ji do navigace** (např. v sekci Podpora → Dokumentace)

Obsah a strukturu administrace popisuje `content/docs/admin.md`.

---

## 4. Fáze – Next.js marketing & docs web (`src/app` + `content/docs`)

Cíl: mít **živý marketingový web a dokumentační rozhraní**, které odpovídá skutečnému stavu projektu.

### Co už je hotové

- Landing page `/` s ukázkou produktu (sekce, statistiky, reference, CTA)
- Podstránky:
  - `/cenik` – pricing
  - `/funkce` – funkce produktu
  - `/faq` – často kladené dotazy
  - `/kontakt` – kontaktní informace a formulář
  - `/o-nas`, `/sluzby`, `/produkty`, `/obchodni-podminky`
- `/docs` – index dokumentace nad `content/docs/*.md`

### Další kroky

- [ ] **Doplnit dokumentaci pro jednotlivé HTML stránky** do `content/docs` (nebo do samostatné sekce):
  - krátký popis (`účel stránky`, `hlavní sekce`, `jaké obrázky použít`)
  - pro každou stránku uvést název HTML souboru (`o-nas.html`, `funkce.html`…)
- [ ] **Provázat dokumentaci s HTML šablonami**:
  - v docs přidat „Odpovídající HTML: `o-nas.html`“ apod.
  - případně přidat odkazy na screenshoty v `public/` nebo `images/`
- [ ] **Udržovat `content/docs/progress.md` jako changelog** – krátké záznamy, co se změnilo
- [ ] Volitelně: přidat další technické dokumenty (design system, komponenty, integrace FAČR…)

---

## 5. Fáze – Backend, integrace a nasazení

Cíl: postupně se přiblížit plnohodnotné platformě, jak je popsaná v `content/docs/overview.md`.

> Tato fáze je dlouhodobá – zatím je projekt primárně o webu a dokumentaci.

Plán:

- [ ] **Základ backendu v Go (Gin)** podle struktury v `/docs/overview` (`cmd/`, `internal/`, `pkg/`…)
- [ ] **Návrh API pro veřejný web i admin**:
  - uživatelé a autentizace (JWT)
  - články, týmy, hráči, zápasy, události
  - média, sponzoři, newsletter, scoreboard
- [ ] **Integrace GoCardless pro platby / předplatné**:
  - nastavit proměnné prostředí (`GOCARDLESS_API_KEY`, `GOCARDLESS_ENVIRONMENT`, `GOCARDLESS_WEBHOOK_SECRET`) podle `.env.example`
  - přidat helper `src/lib/gocardless.ts` pro práci s GoCardless API
  - vytvořit základní API routy v Next.js (`/api/gocardless/checkout`, `/api/gocardless/webhook`)
  - napojit tarifní logiku na stránku `/cenik` a případně admin část
- [ ] **Napojení frontendů**:
  - statický HTML web postupně doplnit/nahrazovat dynamickými daty z API
  - případně připravit separátní SPA / Next.js frontend přímo na API
- [ ] **DevOps a provoz**:
  - Docker + docker-compose (základ už je v tomto repo)
  - CI/CD (GitHub Actions) – build + nasazení
  - monitoring (např. Prometheus) a logování

Detailní technický popis je v `content/docs/overview.md`.

---

## 6. Jak s touto timeline pracovat

Doporučený způsob používání:

- Pro **rychlý přehled fází** a kontext používejte tento `TIMELINE.md`.
- Pro **konkrétní úkoly a checklist**:
  - sledujte `/docs/progress` (postup prací na HTML a Next.js)
  - využijte `/docs/timeline` jako detailnější variantu (v dokumentační části webu)
- Pokud se změní zadání nebo priorita:
  - nejprve aktualizujte `content/docs/web.md`, `content/docs/vize.md`, `content/docs/overview.md`
  - následně upravte `content/docs/timeline.md` a tento kořenový `TIMELINE.md`

Tím zůstane tento soubor i dokumentace pod `/docs` vždy **jednotným zdrojem pravdy** o stavu a směru projektu MyClub.
