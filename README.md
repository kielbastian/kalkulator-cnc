# Kalkulator CNC

Projekt Marka Kulczyckiego. Stożek Morsa, pasowania ISO, identyfikacja gwintu,
gwintowanie sztywne i toczenie gwintu (G76/G92/G32).

Działa w całości w przeglądarce — bez instalacji, bez internetu (offline).

## Zainstaluj na telefonie (Android)

Otwórz w Chrome na telefonie:

**https://kielbastian.github.io/kalkulator-cnc/**

Menu (trzy kropki) → **„Zainstaluj aplikację"**. Dostaniesz ikonę na ekranie
głównym, własne okno bez paska adresu i działanie offline.

> **Zanim ten adres zacznie działać — jednorazowe kliknięcie.**
> Settings → Pages → Source: **GitHub Actions** → Save.
> Tego pierwszego włączenia nie da się zrobić z poziomu workflow: token
> Actions nie ma uprawnienia do *utworzenia* strony Pages
> (`Resource not accessible by integration`). Po tym jednym kliknięciu
> workflow publikuje sam przy każdym pushu — nic więcej nie trzeba.
> Potem uruchom ponownie: Actions → „Publikacja na GitHub Pages" → Re-run.

## Zainstaluj na Windows

Pobierz folder [`windows/`](windows/) i kliknij dwukrotnie
`Zainstaluj-KalkulatorCNC.bat`. Tworzy skrót na pulpicie i w menu Start.
Szczegóły w [`windows/CZYTAJ-Windows.txt`](windows/CZYTAJ-Windows.txt).

## Bez instalacji

Otwórz [`kalkulator_cnc.html`](kalkulator_cnc.html) w dowolnej przeglądarce —
jeden plik, nic więcej nie trzeba.

## Plik APK

Mając już adres powyżej, wejdź na https://www.pwabuilder.com, wklej go
i wygeneruj podpisany plik `.apk`. Szczegóły w
[`CZYTAJ-Android.txt`](CZYTAJ-Android.txt) (SPOSÓB 3).

## Co jest w repozytorium

| Ścieżka | Co to jest |
|---|---|
| `index.html` + `manifest.webmanifest` + `sw.js` + ikony | aplikacja PWA, publikowana na GitHub Pages |
| `kalkulator_cnc.html` | wersja jednoplikowa do otwarcia lokalnie |
| `windows/` | instalator skrótu na Windows plus deinstalator |

Publikacja na Pages dzieje się sama przy każdym pushu do `main`
(workflow `.github/workflows/deploy-pages.yml`).

## Uwaga: wersje różnią się logiką gwintu

Trzy pliki HTML w tym repozytorium **nie są identyczne**. Wersja
w `windows/` jest nowsza — liczy inaczej wysokość gwintu wewnętrznego 60°:

- `windows/kalkulator_cnc.html` — rozróżnia gwint **zewnętrzny** (0,6134·P)
  i **wewnętrzny** (0,5413·P, czyli H1 = 5/8 H)
- `index.html` i `kalkulator_cnc.html` — używają 0,6134·P w obu przypadkach

Jeśli poprawka z wersji Windows jest tą właściwą, trzeba ją przenieść
do pozostałych dwóch plików — dotyczy to także aplikacji na telefon.
