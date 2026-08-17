# Tășnad Thermal Spa — weboldal

Háromnyelvű (magyar / román / angol) statikus weboldal a tăşnadi termálstrandról.

## Fájlok

- `index.html` — a teljes weboldal (HTML + CSS + JS egyben)
- `images/` — a képek (webre optimalizálva)
- `.nojekyll` — GitHub Pageshez (kikapcsolja a Jekyll-feldolgozást)
- `_headers` — Cloudflare Pageshez (gyorsítótár + biztonsági fejlécek; GitHub figyelmen kívül hagyja)
- `robots.txt` — keresőknek

Nincs szükség build lépésre, keretrendszerre vagy szerverre — sima statikus oldal.

## Optimalizálás (GitHub + Cloudflare)

Az oldal statikus hosztolásra van optimalizálva:
- **Nincs külső függőség** — nincs CDN, nincs webfont-letöltés; minden a fájlban van.
  Így a szigorú CSP/CDN-korlátok sem okoznak gondot.
- **Helyes HTML-fejléc** — `<!doctype html>`, `charset=utf-8` (ő/ș/ț helyesen jelenik meg),
  `viewport` (mobilon jól méreteződik), `theme-color`, favicon.
- **Közösségi megosztás** — Open Graph / Twitter metaadatok (Facebookon szép előnézet).
- **Optimalizált képek** — átméretezve és tömörítve (JPEG).
- **Cloudflare gyorsítótár** — a `_headers` a képekre 1 éves „immutable" cache-t állít.

### Cloudflare Pages-re telepítés
1. Töltsd fel a mappát GitHubra (lásd lent).
2. Cloudflare dashboard → **Workers & Pages → Create → Pages → Connect to Git**.
3. Válaszd ki a repót. **Build command:** üres. **Build output directory:** `/` (gyökér).
4. **Save and Deploy** — pár perc múlva él a `*.pages.dev` címen (saját domain is köthető).

> Megjegyzés: az `og:image` most relatív útvonal (`images/borito.jpg`). Ha lesz saját
> domained, érdemes teljes URL-re cserélni (pl. `https://sajat-domain.ro/images/borito.jpg`),
> hogy a Facebook-előnézet biztosan megjelenjen.

## Helyi megnyitás

Kattints kétszer az `index.html` fájlra, vagy húzd be egy böngészőbe.

## Feltöltés GitHubra + ingyenes hosztolás (GitHub Pages)

1. Hozz létre egy új repót a GitHubon (pl. `tasnad-strand`).
2. Töltsd fel az egész mappa tartalmát: az `index.html`-t és az `images/` mappát
   (a GitHub oldalán: **Add file → Upload files**, majd húzd be őket).
3. A repóban: **Settings → Pages**.
4. A *Source* alatt válaszd: **Deploy from a branch**, branch: `main`, mappa: `/ (root)`, majd **Save**.
5. 1–2 perc múlva az oldal elérhető lesz itt:
   `https://<felhasznalonev>.github.io/<repo-nev>/`

## Szerkesztés

- Szövegek: az `index.html` alján lévő `const I = { ... }` blokkban van mind a három nyelv.
- Képcsere: tedd az új képet az `images/` mappába, és írd át a hivatkozást az `index.html`-ben
  (pl. `src="images/hero-nagy-medence.jpg"`).

## Jogi rész (FONTOS — töltsd ki!)

A weboldal alján (footer) van: **Impresszum, Adatvédelem, Cookie-tájékoztató,
Jogi nyilatkozat** (felugró ablakban, mindhárom nyelven), valamint egy **cookie-sáv**.

Az **Impresszumban** ki kell töltened a szögletes zárójeles helyeket a valós adataiddal
(üzemeltető neve, e-mail, telefon, cím). Ezt az `index.html`-ben a `const LEGAL = { ... }`
blokkban találod (mindhárom nyelvnél: `hu`, `ro`, `en`), keresd a `[ ... — kitöltendő]`
szövegeket.

### Amit tudnod kell
- Az oldal **nem gyűjt személyes adatot**, nincs űrlap, **nincs nyomkövető süti** — csak a
  nyelvválasztást és a cookie-sáv elfogadását tárolja a böngésződben (localStorage).
  Emiatt GDPR szempontból egyszerű a helyzet.
- **Képek és logó:** ezek a strand tulajdonát képezhetik. Csak akkor tedd ki nyilvánosan,
  ha jogod/engedélyed van használni őket (pl. te üzemelteted a strandot, vagy engedélyt kaptál).
  A Jogi nyilatkozat tartalmaz egy „kérésre eltávolítjuk" záradékot, de ez nem pótolja az engedélyt.
- Ez az oldal jelenleg **nem hivatalos** oldalként van megfogalmazva. Ha ez lesz a hivatalos oldal,
  szólj, és átírom a szövegeket (pl. az Impresszumot és a „nem hivatalos" megjegyzést).

## Megjegyzés

Az árak és információk nyilvános forrásokból származnak és tájékoztató jellegűek.
A pontos, aktuális adatokért a hivatalos Facebook-oldal az irányadó.
