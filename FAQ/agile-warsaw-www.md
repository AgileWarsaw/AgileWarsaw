# Przewodnik zarządzania treścią - Agile Warsaw

## Wprowadzenie

Ten dokument pomoże Ci edytować i dodawać treści na stronie Agile Warsaw. Nie musisz rozumieć jak działa Hugo - wystarczy wiedzieć, które pliki edytować i co w nich zmieniać.

## Struktura plików - gdzie co znajdujesz

```
themes/agilewarsaw/
├── layouts/              ← Tutaj są szablony z treścią
│   ├── index.html       ← Strona główna
│   ├── partials/        ← Części składowe strony
│   │   ├── header.html  ← Nagłówek (logo i opis)
│   │   ├── footer.html  ← Stopka (zespół, kontakty)
│   │   └── sponsors.html ← Lista sponsorów
│   ├── events/          ← Szablony dla wydarzeń
│   └── shortcodes/      ← Małe elementy wielokrotnego użytku
├── static/              ← Pliki statyczne
│   ├── assets/          ← Loga, ikony, flagi
│   ├── images/          ← Zdjęcia zespołu
│   └── css/             ← Wygląd strony
└── archetypes/
    └── event.md         ← Szablon nowego wydarzenia
```

---

## Edycja nagłówka strony

**Plik:** `themes/agilewarsaw/layouts/partials/header.html`

### Zmiana opisu Agile Warsaw

Znajdź linię:
```html
<div id="about">Nieformalna grupa entuzjastów spotykająca się z grubsza co dwa tygodnie.
```

Zmień tekst między `<div id="about">` a `{{ partial "main-menu" . }}` na nowy opis.

**Przykład:**
```html
<div id="about">Społeczność praktyków Agile spotykająca się regularnie w Warszawie.
```

### Zmiana logo

Logo znajduje się w pliku `static/assets/agile-warsaw-logo.png`. Aby je zmienić:
1. Przygotuj nowy plik graficzny w formacie PNG
2. Nazwij go `agile-warsaw-logo.png`
3. Zastąp stary plik w folderze `static/assets/`

---

## Edycja stopki - kontakty i zespół

**Plik:** `themes/agilewarsaw/layouts/partials/footer.html`

### Zmiana linków kontaktowych

Znajdź sekcję:
```html
<p>
    <a href="http://twitter.com/agilewarsaw" target="_blank">Twitter</a>
    |  
    <a href="https://www.youtube.com/agilewarsaw" target="_blank">YouTube</a>
    ...
</p>
```

Aby dodać nowy link, dodaj po znaku `|`:
```html
|
<a href="https://adres.strony" target="_blank">Nazwa</a>
```

### Edycja obecnych organizatorów

Znajdź sekcję `<ul class="team">`. Każdy organizator to blok:

```html
<li class="team-member">
    <h4>Imię Nazwisko</h4>
    <img src="/images/team-XX.jpg" alt="">
    <a target="_blank" href="https://linkedin.com/link">LinkedIn</a>
</li>
```

**Aby dodać nowego organizatora:**
1. Skopiuj cały blok `<li class="team-member">...</li>`
2. Wklej go przed znacznikiem `</ul>`
3. Zmień:
   - Imię i nazwisko w `<h4>`
   - Nazwę pliku zdjęcia w `src="/images/team-XX.jpg"`
   - Link do LinkedIn w `href="..."`

**Aby usunąć organizatora:**
- Usuń cały blok `<li class="team-member">...</li>` tej osoby

### Edycja przyjaciół Agile Warsaw

Znajdź sekcję `<ul class="friends">`. Działa identycznie jak organizatorzy:

```html
<li class="friend">
    <h4>Imię Nazwisko</h4>
    <img src="/images/team-XX.jpg" alt="">
    <a target="_blank" href="https://linkedin.com/link">LinkedIn</a>
</li>
```

### Edycja poprzednich organizatorów

Znajdź sekcję `<ul class="prev-team">`. Działa tak samo:

```html
<li class="prev-team-member">
    <h4>Imię Nazwisko</h4>
    <img src="/images/prev-team-XX.jpg" alt="">
</li>
```

---

## Edycja listy sponsorów

**Plik:** `themes/agilewarsaw/layouts/partials/sponsors.html`

### Dodanie nowego sponsora

Znajdź `<ul class="sponsors">`. Każdy sponsor to:

```html
<li class="sponsor">
    <h4>Nazwa Sponsora</h4>
    <p>sponsor Meetupa</p>
    <a target="_blank" href="https://strona-sponsora.com/">
        <img src="/images/logo-sponsor.svg" alt="Nazwa Sponsora">
    </a>
</li>
```

**Kroki:**
1. Skopiuj całą sekcję `<li class="sponsor">...</li>`
2. Wklej przed `</ul>`
3. Zmień:
   - Nazwę sponsora w `<h4>`
   - Opis w `<p>` (np. "sponsor nagrań", "gospodarz spotkań")
   - Link do strony sponsora w `href="..."`
   - Ścieżkę do logo w `src="/images/logo-sponsor.svg"`
   - Tekst alternatywny w `alt="..."`

### Ukrycie sponsora (komentarz)

Jeśli sponsor nie jest już aktywny, ale chcesz zachować kod:

Dodaj `<!--` przed i `-->` po całym bloku:
```html
<!--
<li class="sponsor">
    ...
</li>
-->
```

---

## Dodawanie nowego wydarzenia

### Krok 1: Przygotuj pliki

**Struktura dla wydarzenia #400:**
```
content/events/400/
├── index.md           ← Opis wydarzenia
├── hero.jpg           ← Główne zdjęcie (opcjonalne)
└── inne-zdjecia.jpg   ← Dodatkowe zdjęcia (opcjonalne)
```

### Krok 2: Utwórz plik opisu

Stwórz plik `content/events/400/index.md` i skopiuj szablon z `themes/agilewarsaw/archetypes/event.md`:

```markdown
---
number: "400"
date: "2023-12-14T19:00:00+01:00"
title: "Tytuł wydarzenia"
speakers: "Jan Kowalski, Anna Nowak"
lang: "pl"
sponsors: ["sponsor1", "sponsor2"]
videoURL: ""
slidesURL: ""
draft: false
---

Opis wydarzenia w formacie Markdown...
```

### Krok 3: Wypełnij dane wydarzenia

**Nagłówek (sekcja między `---`):**

- `number:` - numer wydarzenia (bez znaku #)
- `date:` - data w formacie `"2023-12-14T19:00:00+01:00"`
  - Uwaga: zawsze użyj tego formatu, zmieniając tylko datę i godzinę
- `title:` - tytuł (jeśli zawiera cudzysłów, poprzedź go ukośnikiem: `\"tak\"`)
- `speakers:` - prelegenci oddzieleni przecinkami
- `lang:` - język: `"pl"` lub `"en"`
- `sponsors:` - lista sponsorów wydarzenia
- `videoURL:` - link do nagrania YouTube (jeśli dostępne)
- `slidesURL:` - link do materiałów lub nazwa pliku (jeśli w tym samym folderze)
- `draft: false` - musi być `false` aby wydarzenie było widoczne

**Treść (pod `---`):**

Pisz w formacie Markdown. Najważniejsze zasady:

**Paragrafy:**
```markdown
Pierwszy paragraf.

Drugi paragraf.
```

**Nowa linia bez nowego paragrafu:**
```markdown
Pierwsza linia  
Druga linia (dodaj dwie spacje na końcu poprzedniej)
```

**Nagłówki:**
```markdown
# Nagłówek 1
## Nagłówek 2
### Nagłówek 3
```

**Listy:**
```markdown
* Pierwszy element
* Drugi element

1. Pierwszy numerowany
2. Drugi numerowany
```

**Linki:**
```markdown
<!-- Link w nowym oknie (preferowany dla linków zewnętrznych): -->
<a href="https://example.com" target="_blank">Opis linku</a>

<!-- Link w tym samym oknie: -->
[Opis linku](https://example.com)
```

**Miniaturki zdjęć:**

Jeśli dodajesz zdjęcie do folderu wydarzenia (np. `zdjecie.jpg`):
```markdown
{{< thumbnail src="zdjecie.jpg" alt="Opis zdjęcia" >}}
```

Po kliknięciu miniaturka otworzy zdjęcie w pełnym rozmiarze.

**Ikony:**
```markdown
{{% icon-flag-pl %}}     ← flaga Polski
{{% icon-flag-en %}}     ← flaga UK
{{% icon-yt-red %}}      ← ikona YouTube (czerwona)
{{% icon-yt-gray %}}     ← ikona YouTube (szara)
```

### Krok 4: Dodaj główne zdjęcie (opcjonalne)

Jeśli chcesz główne zdjęcie na górze strony wydarzenia:
1. Umieść plik w folderze wydarzenia
2. Nazwij go `hero.jpg` (lub `hero.png`, `hero.gif`)

Nie musisz nic więcej robić - zdjęcie pojawi się automatycznie.

---

## Edycja istniejącego wydarzenia

1. Znajdź folder wydarzenia, np. `content/events/385/`
2. Otwórz plik `index.md`
3. Edytuj dane w nagłówku (między `---`) lub treść poniżej
4. Zapisz plik

**Typowe zmiany:**

**Dodanie nagrania po wydarzeniu:**
```markdown
videoURL: "https://www.youtube.com/watch?v=XXX"
```

**Dodanie materiałów:**
```markdown
slidesURL: "https://link-do-materialow.com"
```
lub jeśli plik jest w folderze wydarzenia:
```markdown
slidesURL: "materialy.pdf"
```

---

## Zarządzanie plikami statycznymi

### Zdjęcia zespołu

**Lokalizacja:** `static/images/`

**Nazewnictwo:**
- Obecni organizatorzy: `team-XX.jpg` (np. `team-LS.jpg` dla Łukasza)
- Przyjaciele: `team-XX.jpg`
- Poprzedni organizatorzy: `prev-team-XX.jpg` lub `team-XX.jpg`

**Jak dodać:**
1. Przygotuj zdjęcie w formacie JPG
2. Nazwa pliku: małe litery, bez polskich znaków
3. Skopiuj do folderu `static/images/`
4. W odpowiednim pliku HTML (np. `footer.html`) użyj tej nazwy w `src="/images/nazwa.jpg"`

### Loga sponsorów

**Lokalizacja:** `static/images/`

**Nazewnictwo:** `logo-nazwa.svg` lub `logo-nazwa.png`

**Jak dodać:**
1. Przygotuj logo w formacie SVG lub PNG
2. Skopiuj do `static/images/`
3. W `sponsors.html` dodaj sponsora z tym logo (patrz sekcja "Edycja listy sponsorów")

### Ikony i grafiki

**Lokalizacja:** `static/assets/`

Tutaj znajdują się:
- `agile-warsaw-logo.png` - główne logo
- `flag-pl.svg` - flaga Polski
- `flag-uk.svg` - flaga UK
- `YT-red.svg` - ikona YouTube (czerwona)
- `YT-gray.svg` - ikona YouTube (szara)
- `slides.svg` - ikona slajdów

**Aby zamienić ikonę:**
1. Przygotuj nowy plik w tym samym formacie (SVG lub PNG)
2. Nazwij dokładnie tak samo jak oryginalny plik
3. Zastąp stary plik w `static/assets/`

---

## Strona główna

**Plik:** `themes/agilewarsaw/layouts/index.html`

### Liczba wyświetlanych wydarzeń

Znajdź linię:
```html
{{ range first 9 (where .Data.Pages "Section" "events") }}
```

Zmień `9` na inną liczbę, aby pokazać więcej lub mniej wydarzeń.

### Link do zapisów

Znajdź:
```html
<a id="subscription-link" href="https://pragmaticmeet.com/@agile_warsaw/events" target="_blank">
    Zapisy na Pragmatic Meet
</a>
```

Zmień link w `href="..."` jeśli zmienia się platforma zapisów.

---

## Często zadawane pytania

### Jak ukryć wydarzenie?

W pliku `index.md` wydarzenia zmień:
```markdown
draft: false
```
na:
```markdown
draft: true
```

### Jak zmienić kolejność wydarzeń?

Wydarzenia są sortowane automatycznie po dacie. Jeśli chcesz zmienić kolejność, zmień datę w `date:`.

### Czy mogę użyć HTML w opisie wydarzenia?

Tak, możesz mieszać Markdown i HTML w treści wydarzenia.

### Jak dodać wydarzenie w języku angielskim?

Ustaw `lang: "en"` w nagłówku wydarzenia. Przy wydarzeniu pojawi się flaga UK.

### Gdzie sprawdzić poprawność Markdown?

Możesz użyć online'owego edytora, np. https://dillinger.io/

---

## Wsparcie

W razie problemów:
- Sprawdź czy nie pomyliłeś cudzysłowów lub nawiasów
- Upewnij się że nazwy plików nie zawierają polskich znaków
- Skontaktuj się z zespołem technicznym: team@agilewarsaw.com
