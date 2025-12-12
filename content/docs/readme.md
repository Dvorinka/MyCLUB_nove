---
title: Jak používat dokumentaci MyClub
order: 1
summary: Krátký přehled, co v dokumentaci najdete a kde začít.
---

# Jak používat dokumentaci MyClub

Tato dokumentace slouží jako **centrální místo pro zadání, vizi, pricing a postup prací** na projektu MyClub.
Je psaná hlavně pro vás jako pro:

- 🔹 **vlastníka produktu** (co má MyClub umět a komu pomáhá)
- 🔹 **vývojáře / integrátora** (jak je systém navržený technicky)
- 🔹 **správce webu / admina klubu** (jak se s webem bude pracovat)

---

## Kde začít

1. **Chcete rychle pochopit produkt?**
   - Začněte dokumenty:
     - [`/docs/vize`](/docs/vize) – produktová vize v češtině
     - [`/docs/overview`](/docs/overview) – technický přehled (Go backend + moderní frontend)
2. **Řešíte konkrétně veřejný web a HTML šablony?**
   - Projděte si:
     - [`/docs/web`](/docs/web) – zadání pro HTML šablony (index, o-nas, funkce…)
     - [`/docs/progress`](/docs/progress) – co je na statickém webu hotové a co zbývá
     - [`/docs/timeline`](/docs/timeline) – dlouhodobější roadmap a fáze
3. **Potřebujete vědět, co uvidí admin klubu?**
   - Podívejte se na:
     - [`/docs/admin`](/docs/admin) – dokumentace administrace (podle AdminDocsPage)
     - [`/docs/zadani1`](/docs/zadani1) – úkol na převedení admin dokumentace do čistého HTML
4. **Zajímá vás obchodní stránka (plány, pricing)?**
   - Viz:
     - [`/docs/pricing`](/docs/pricing) – návrh tarifů a licencí

---

## Struktura složky `content/docs`

Všechny markdown soubory, které se zobrazují na `/docs`, najdete v adresáři:

```text
web_insp/
  content/
    docs/
      admin.md
      overview.md
      pricing.md
      progress.md
      timeline.md
      vize.md
      web.md
      zadani1.md
      readme.md   ← tento soubor
```

Každý `.md` soubor se automaticky stane stránkou na `/docs/<slug>`, kde `<slug>` je název souboru bez přípony.

- `title` a `summary` se berou z **YAML frontmatteru** (úvod mezi `---`), pokud je přítomen.
- Pokud `title` ve frontmatteru chybí, zobrazí se první `#` nadpis v souboru.
- Seznam všech dokumentů a jejich `summary` najdete na stránce [`/docs`](/docs).

---

## Jak přidat nový dokument

1. Vytvořte nový soubor v `content/docs`, např. `faqs-implementation.md`.
2. Na začátek doplňte (doporučeně) frontmatter:

   ```md
   ---
   title: FAQ k implementaci
   order: 10
   summary: Odpovědi na nejčastější otázky při nasazení MyClubu.
   ---
   ```

3. Pod to napište obsah v běžném Markdownu.
4. Po uložení se stránka automaticky objeví na `/docs/faqs-implementation` a na indexu `/docs`.

> **Poznámka:** V navigaci `/docs` se dokumenty řadí podle `order` (pokud je vyplněný), jinak abecedně podle názvu.

---

## Jak souvisí tato dokumentace s HTML šablonami

- Tato Next.js aplikace (`web_insp`) slouží jako **živá dokumentace a inspirace designu**.
- Statické HTML šablony (v kořeni projektu) jsou **cílový výstup**, který se bude nasazovat na klubové weby.
- Postup prací na HTML šablonách i na této dokumentaci sledujte v:
  - [`/docs/progress`](/docs/progress)
  - [`/docs/timeline`](/docs/timeline)

Pokud dojde ke změně zadání, *nejdřív aktualizujte markdown v `content/docs`* a teprve potom upravujte HTML / Next.js kód. Díky tomu zůstane dokumentace konzistentní s implementací.
