# Slovíčka – kartičky s opakováním (jako Anki)

Statická webová aplikace bez serveru a bez instalace závislostí. Funguje v mobilu i na počítači, jde nainstalovat na plochu telefonu a fungovat offline.

## Nasazení na GitHub Pages

1. Na GitHubu vytvoř nový repozitář (např. `slovicka`), může být veřejný.
2. Nahraj do jeho kořene všechny soubory: `index.html`, `manifest.webmanifest`, `sw.js`, `icon.svg`, `README.md`
   (tlačítko **Add file → Upload files**).
3. V repozitáři otevři **Settings → Pages**, u *Build and deployment* vyber **Deploy from a branch**, větev `main` a složku `/ (root)`, potvrď **Save**.
4. Za minutu dvě bude web na adrese `https://TVOJE-JMENO.github.io/slovicka/`.
5. V telefonu adresu otevři a v menu prohlížeče zvol **Přidat na plochu** (Chrome) / **Sdílet → Přidat na plochu** (Safari).

Změny později: stačí soubor v repozitáři upravit/nahradit, web se aktualizuje sám.

## Jak se používá

- **Seznam** = balíček (např. „Angličtina – lekce 1“). Vytvoříš ho na úvodní stránce.
- V seznamu přidáváš kartičky ručně, volitelně i s opačným směrem, nebo hromadně (jedna na řádek: `dog;pes`).
- **Učit**: aplikace ukáže přední stranu → **Otočit** → ohodnotíš: **Znovu / Těžké / Dobré / Snadné**. Na tlačítkách vidíš, za jak dlouho se karta vrátí.
- Číslice nahoře: modrá = nové, červená = učí se (krátké kroky v minutách), zelená = k opakování.

## Plánování

Zjednodušený algoritmus ve stylu Anki (SM-2):

- Nová karta: Znovu → 1 min, Těžké → 6 min, Dobré → 1 den, Snadné → 4 dny.
- Naučená karta: Dobré násobí interval „ease“ faktorem (výchozí 2,5), Těžké ×1,2, Snadné navíc ×1,3 a zvýší ease. Znovu = chyba, interval se zkrátí na polovinu a karta se za 10 minut vrátí.

Parametry jsou ve funkci `sched()` v `index.html`.

## Data

Vše se ukládá do `localStorage` v prohlížeči v daném zařízení. Mezi telefonem a počítačem se nesynchronizuje sama – použij **Nastavení → Exportovat / Importovat** (soubor JSON, slouží i jako záloha). Smazání dat prohlížeče smaže i kartičky, proto čas od času exportuj zálohu.
