---
title: Roadmap a timeline projektu MyClub
order: 5
summary: Vysokourovňový plán, jak se dostat od statických HTML šablon k plně integrované platformě MyClub.
---

# Roadmap a timeline projektu MyClub

Tento dokument shrnuje *fáze prací* na projektu MyClub na základě:

- **vizí a produktového zadání** – viz `/docs/vize` a `/docs/overview`
- **zadání pro web** – viz `/docs/web`
- **dosavadního postupu** – viz `/docs/progress`
- **požadavku na admin dokumentaci** – viz `/docs/admin` a `/docs/zadani1`

Slouží jako přehled toho, *co už je hotové* a *co se má dělat dál* (HTML šablony + Next.js docs + budoucí backend).

---

## 0. Kde jsme teď

Shrnutí aktuálního stavu podle `PROGRESS.md` a obsahu v tomto repo:

- ✅ V HTML šabloně `index.html` je hotová sekce s videem, recenze a upravený footer.
- ✅ Navigace je zjednodušená, ale stále obsahuje zbytky demo menu (nutný úklid).
- ✅ V `assets2/` jsou připravené klíčové obrázky (např. `soubory.png`, `statistiky.png`, `vyhledat.png`, `sportcreative.png`, `články.png`, `myclub.svg`).
- ✅ V tomto Next.js projektu (`web_insp`) existuje moderní homepage a dokumentace v `content/docs`:
  - `overview.md` – technický přehled systému
  - `vize.md` – produktová vize MyClub
  - `web.md` – zadání pro statický web
  - `pricing.md` – návrh pricingu
  - `admin.md` – dokumentace admin rozhraní
  - `progress.md` – dosavadní průběh prací na HTML šablonách
  - `zadani1.md` – úkol na převedení AdminDocsPage do HTML

---

## 1. Fáze – Dokončení statických HTML šablon

Cíl: Mít **konzistentní marketingový web** v čistém HTML/CSS bez zbytků demo šablony.

- [ ] **Dokončit navigaci v `index.html`**
  - odstranit všechny odkazy na `home-page-02.html` až `home-page-35.html`
  - odstranit staré "Pages" / mega menu sekce
  - sjednotit strukturu menu podle `PROGRESS.md` (Domů, O nás, Funkce, Integrace, Ceník, Podpora, Kontakt)
- [ ] **Zkopírovat navigaci + footer do všech cílových stránek** (viz také `hlavni_akce.md` a `PROGRESS.md`):
  - `o-nas.html`, `funkce.html`, `integrace.html`, `cenik.html`
  - `reference.html`, `dokumentace.html`, `podpora.html`, `kontakt.html`, `faq-page.html`
  - `kariera.html`, `kariera-detail.html`, `sluzby.html`
  - `zmeny.html`, `obchodni-podminky.html`, `reklamace.html`, `gdpr-page.html`, `404.html`
- [ ] **Odstranit blog sekce** na všech stránkách, kde ještě zůstaly z původní šablony.
- [ ] **Zkontrolovat responzivitu** po úpravách (mobil / tablet / desktop) – bez zásahu do JS.

---

## 2. Fáze – Obsah a vizuální doplnění

Cíl: Mít **realistický obsah** (kopii) a lepší využití připravených assetů.

- [ ] **Doplnit reálný obsah ceníku** na základě `/docs/pricing` (zatím placeholdery).
- [ ] **Doplnit sekce "O nás", "Funkce", "Podpora"** podle `/docs/vize` a `/docs/overview`.
- [ ] **Vložit reálné YouTube video** – nahradit `YOUR_VIDEO_ID` v sekci videa na homepage.
- [ ] **Zapojit obrázky z `assets2/` do vhodných sekcí**:
  - např. `soubory.png`, `statistiky.png`, `vyhledat.png`, `sportcreative.png`, `články.png`, `myclub.svg`, `myclub_text.svg`
- [ ] **Doplnit reference** (až budou k dispozici reálné texty) – sekce recenzí na homepage i na `reference.html`.

---

## 3. Fáze – Admin dokumentace jako HTML stránka

Cíl: Mít **samostatnou dokumentační stránku** v čistém HTML, inspirovanou `AdminDocsPage.tsx`.

- [ ] **Převést React komponentu `AdminDocsPage.tsx` do HTML/CSS/JS**:
  - zachovat strukturu sekcí, nadpisy a obsah (návody, tipy, checklisty)
  - viz zadání v `/docs/zadani1`
- [ ] **Nasadit stránku jako `dokumentace.html`** v sadě HTML šablon.
- [ ] **Napojit stránku z navigace** (položka "Dokumentace" v Podpora / Support menu).
- [ ] Volitelně: přidat jednoduché JS pro scrollování na sekce (anchor odkazy), ale bez závislosti na frameworku.

---

## 4. Fáze – Next.js dokumentační a marketingový web (`web_insp`)

Cíl: Mít **živou dokumentaci** a moderní marketingový web, který odráží skutečný stav projektu.

- ✅ Vytvořit základní homepage v Next.js (`src/app/page.tsx`).
- ✅ Přenést hlavní podklady do markdown dokumentů v `content/docs`.
- [ ] **Doplnit dokumentaci pro jednotlivé stránky HTML webu**:
  - krátký popis pro `o-nas`, `funkce`, `integrace`, `cenik`, `podpora`, `kontakt`, `kariera`…
  - pro každou stránku: účel, hlavní sekce, jaké obrázky z `assets2` použít.
- [ ] **Propojit dokumentaci s hotovými HTML šablonami**:
  - u každé stránky v docs uvést název HTML souboru a hlavní anchor sekce
  - doplnit odkazy na náhledy / screenshoty (z `public/` nebo `assets2/`).
- [ ] **Udržovat `progress.md` jako changelog** – krátké záznamy, co bylo upraveno v HTML/Next.js.
- [ ] Volitelně: přidat další sekce do `/docs` (např. "Design system", "Komponenty", "Integrace s FAČR").

---

## 5. Fáze – Backend, integrace a nasazení

Cíl: Přiblížit se plnohodnotné platformě popsané v `/docs/overview`.

> Tato fáze je spíše plán do budoucna – zatím není implementovaná.

- [ ] **Základ backendu v Go (Gin)** podle struktury v `/docs/overview` (`cmd/`, `internal/`, `pkg/` atd.).
- [ ] **API pro veřejný web a admin**:
  - uživatelé a autentizace (JWT)
  - články, týmy, hráči, zápasy, události
  - média, sponzoři, newsletter, scoreboard…
- [ ] **Napojení frontendů**:
  - statický HTML web postupně nahradit nebo doplnit o dynamická data z API
  - případně vytvořit separátní SPA/Next.js frontend napojený na backend.
- [ ] **DevOps / provoz** podle `overview.md`:
  - Docker + docker-compose
  - CI/CD (GitHub Actions)
  - monitoring (Prometheus) a logování

---

## Jak s tímto dokumentem pracovat

- Pro **konkrétní check-list úkolů** sledujte `/docs/progress`.
- Tento dokument slouží jako **mapa fází** – můžete si k jednotlivým bodům doplnit data / odhady.
- Pokud se změní zadání (např. rozsah HTML stránek nebo funkce platformy), aktualizujte nejdříve:
  - `/docs/web` – co má umět veřejný web
  - `/docs/vize` a `/docs/overview` – dlouhodobá vize a technický přehled
  - a následně i tuto `timeline.md`.
