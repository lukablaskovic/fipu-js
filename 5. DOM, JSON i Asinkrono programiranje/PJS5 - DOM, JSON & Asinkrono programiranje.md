# Programiranje u skriptnim jezicima

**Nositelj**: doc. dr. sc. Nikola Tanković  
**Asistenti**:

- Luka Blašković, univ. bacc. inf.
- Alesandro Žužić, univ. bacc. inf.

**Ustanova**: Sveučilište Jurja Dobrile u Puli, Fakultet informatike u Puli

<img src="https://raw.githubusercontent.com/lukablaskovic/FIPU-PJS/main/0.%20Template/FIPU_UNIPU.png" style="width:40%"></img>

# [5] DOM, JSON i Asinkrono programiranje


<img src="https://github.com/lukablaskovic/FIPU-PJS/blob/main/0.%20Template/logojs/js5.png?raw=true" style="width:9%; float:right;"></img>

<p style="float: clear">Prilikom izrade web aplikacija i stranica, često ćete na neki način manipulirati strukturom dokumenata i njihovim sadržajem. U ovom poglavlju upoznat ćemo se s Document Object Model (DOM) standardom, koji predstavlja aplikacijsko programsko sučelje (API) za kontrolu HTML-a koristeći Document objekt. Važno je razumjeti kako funkcionira DOM budući da se svi poznati JavaScript razvojni okviri temelje na njemu (React, VUE, Angular, jQuery...). Dodatno, upoznat ćemo se s JSON formatom (JavaScript Object Notation) koji se koristi za razmjenu podataka između klijenta i servera te predstavlja jedan od najčešćih, ako ne i najčešće korišteni format za razmjenu podataka. Za sam kraj ćemo proći asinkrono programiranje i time postaviti dobre temelje za uvod u svijet programskog inženjerstva i razvoja web aplikacija.</p>

## Sadržaj

- [Programiranje u skriptnim jezicima](#programiranje-u-skriptnim-jezicima)
- [\[5\] DOM, JSON i Asinkrono programiranje](#5-dom-json-i-asinkrono-programiranje)
  - [Sadržaj](#sadržaj)
- [0. Ponavljanje HTML-a i CSS-a](#0-ponavljanje-html-a-i-css-a)
    - [Primjer upotrebe `id` atributa:](#primjer-upotrebe-id-atributa)
    - [Primjer upotrebe `class` atributa:](#primjer-upotrebe-class-atributa)
    - [Primjer kombiniranja `id` i `class` atributa:](#primjer-kombiniranja-id-i-class-atributa)
    - [CSS (Cascading Style Sheets)](#css-cascading-style-sheets)
- [1. DOM manipulacija](#1-dom-manipulacija)
  - [1.1 Osnovni DOM element](#11-osnovni-dom-element)
  - [1.2 Dohvaćanje DOM elemenata](#12-dohvaćanje-dom-elemenata)
    - [Primjer 1. - Dohvaćanje elemenata](#primjer-1---dohvaćanje-elemenata)
  - [1.3 Svojstva DOM elemenata](#13-svojstva-dom-elemenata)
    - [Primjer 2 - Pristupanje sadržaju, `id`-u, `tag`-u, atributima i klasama elementa](#primjer-2---pristupanje-sadržaju-id-u-tag-u-atributima-i-klasama-elementa)
    - [Vježba 1](#vježba-1)
    - [Primjer 3 - Manipulacija klasama](#primjer-3---manipulacija-klasama)
    - [Vježba 2](#vježba-2)
    - [Primjer 4 - Dohvaćanje `child` i `sibling` elemenata.](#primjer-4---dohvaćanje-child-i-sibling-elemenata)
    - [Vježba 3](#vježba-3)
  - [1.4 Dodavanje i brisanje DOM elemenata](#14-dodavanje-i-brisanje-dom-elemenata)
    - [Primjer 5 - Stvaranje, dodavanje, brisanje i izmjena DOM elemenata](#primjer-5---stvaranje-dodavanje-brisanje-i-izmjena-dom-elemenata)
    - [Vježba 4](#vježba-4)
  - [1.4 DOM events](#14-dom-events)
    - [Primjer 6 - `click` event](#primjer-6---click-event)
    - [Vježba 5](#vježba-5)
    - [Primjer 7 - `focus` events](#primjer-7---focus-events)
    - [Vježba 6](#vježba-6)
    - [Primjer 8 - `mouse` events](#primjer-8---mouse-events)
    - [Vježba 7](#vježba-7)
    - [Primjer 9 - `input` event](#primjer-9---input-event)
    - [Vježba 8](#vježba-8)
- [Samostalni zadatak za vježbu 8](#samostalni-zadatak-za-vježbu-8)


<br>

# 0. Ponavljanje HTML-a i CSS-a
U ovoj sekciji ćemo se osvrnuti na osnove HTML-a i CSS-a. **HTML** (HyperText Markup Language) je markup jezik za označavanje struktura web stranica, dok je CSS (Cascading Style Sheets) jezik za stilizaciju tih struktura. Kombinacija ova dva jezika omogućuje nam da oblikujemo i prikažemo sadržaj web stranica na željeni način.

Kako bi vam HTML i CSS jezici već trebali biti poznati, u nastavku ćemo se osvrnuti na neke osnovne koncepte i primjere korištenja HTML i CSS elemenata. U skripti se dalje nećemo detaljno baviti HTML i CSS jezicima, već ćemo se fokusirati na JavaScript, odnosno kako možemo **manipulirati HTML elementima** pomoću JavaScripta.

>**HTML (HyperText Markup Language)**

**HTML** je markup jezik (***eng. [markup language](https://en.wikipedia.org/wiki/Markup_language#:~:text=July%202023content%20to%20facilitate%20automated%20processing.)***) koji se koristi za strukturiranje sadržaja web stranica. Sastoji se od HTML elemenata koji se koriste za označavanje dijelova sadržaja. Svaki HTML element sastoji se od otvarajuće oznake (***eng. start tag***), sadržaja elementa (***eng. content***) i zatvarajuće oznake (***eng. end tag***).

Osnovna struktura HTML dokumenta često se može podijeliti na `head` i `body` dijelove. `head` dio obično sadrži meta informacije o dokumentu, kao što su naslov stranice, veze prema CSS datotekama, skripte itd. `body` dio sadrži glavni sadržaj stranice, poput zaglavlja (**header**), navigacije (**nav**), članaka (**article**) i podnožja (**footer**). 

```html
<head>
    <title>Moja web stranica</title>
</head>

<body>
    <header>
        <h1>Naslov</h1>
        <nav>
            <ul>
                <li><a href="#">Početna</a></li>
                <li><a href="#">O nama</a></li>
                <li><a href="#">Kontakt</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <article>
            <h2>Članak 1</h2>
            <p>Ovo je prvi članak.</p>
        </article>

        <article>
            <h2>Članak 2</h2>
            <p>Ovo je drugi članak.</p>
        </article>
    </main>

    <footer>
        <p>&copy; 2022 Web Stranica</p>
    </footer>
</body>
```


>Treba napomenuti da je dolaskom HTML5 standarda uvedeno mnogo novih elemenata i atributa koji omogućuju bolje semantičko označavanje sadržaja web stranica. Semantičko označavanje je važno jer pomaže tražilicama i drugim alatima da bolje razumiju strukturu i značenje sadržaja na web stranici. Svakako je moguće gotovo sve elemente stilizirati pomoću CSS-a i svesti na `div` i `span` elemente, ali korištenje semantičkih elemenata poboljšava pristupačnost i [SEO](https://developers.google.com/search/docs/fundamentals/seo-starter-guide#:~:text=SEO%E2%80%94short%20for%20search%20engine,site%20through%20a%20search%20engine.) (Search Engine Optimization) web stranice.

U najnovijem HTML standardu za vrijeme pisanja ove skripte (svibanj 2024), postoji 142 HTML elementa. U tablici ispod prikazani su neki od najčešće korištenih HTML elemenata, zajedno s njihovim opisima, atributima i primjerima korištenja. Svakako provjerite i [HTML5 specifikaciju](https://www.spiceworks.com/tech/tech-general/articles/what-is-html-five/).

| Naziv elementa | Opis | Atributi | Primjer |
|----------------|------|----------|---------|
| `<html>`       | Korijenski element HTML dokumenta | `lang` | `<html lang="en"> ... </html>` |
| `<head>`       | Sadrži meta-informacije o dokumentu | - | `<head> ... </head>` |
| `<title>`      | Naslov dokumenta, prikazan u naslovnoj traci preglednika | - | `<title>Naslov stranice</title>` |
| `<meta>`       | Definira metapodatke o HTML dokumentu | `charset`, `name`, `content`, `http-equiv` | `<meta charset="UTF-8">` |
| `<link>`       | Povezuje vanjske resurse, poput CSS datoteka | `rel`, `href`, `type` | `<link rel="stylesheet" href="style.css">` |
| `<style>`      | Sadrži CSS stilove za dokument | `type` | `<style> body { background-color: lightblue; } </style>` |
| `<script>`     | Sadrži ili povezuje JavaScript kod | `src`, `type` | `<script src="script.js"></script>` |
| `<body>`       | Glavni sadržaj HTML dokumenta | - | `<body> ... </body>` |
| `<h1>` do `<h6>` | Naslovi različitih razina | - | `<h1>Naslov 1</h1>` |
| `<p>`          | Paragraf teksta | - | `<p>Ovo je paragraf.</p>` |
| `<a>`          | Hiperlink (poveznica) | `href`, `target` | `<a href="https://example.com">Link</a>` |
| `<img>`        | Ugrađena slika | `src`, `alt`, `width`, `height` | `<img src="slika.jpg" alt="Opis slike">` |
| `<ul>`         | Neuređena lista (bez numeriranja) | - | `<ul><li>Prva stavka</li><li>Druga stavka</li></ul>` |
| `<ol>`         | Uređena lista (numerirana) | - | `<ol><li>Prva stavka numerirano</li><li>Druga stavka numerirano</li></ol>` |
| `<li>`         | Stavka liste | - | `<li>Stavka</li>` |
| `<table>`      | Tablica | - | `<table> ... </table>` |
| `<tr>`         | Redak u tablici | - | `<tr> ... </tr>` |
| `<td>`         | Ćelija u tablici | `colspan`, `rowspan` | `<td colspan="2">Ćelija</td>` |
| `<th>`         | Zaglavlje ćelije u tablici | `colspan`, `rowspan`, `scope` | `<th scope="col">Zaglavlje</th>` |
| `<form>`       | Forma za unos podataka | `action`, `method` | `<form action="/submit" method="post"> ... </form>` |
| `<input>`      | Unos podataka | `type`, `name`, `value`, `placeholder` | `<input type="text" name="ime" placeholder="Unesite ime">` |
| `<button>`     | Gumb | `type` | `<button type="submit">Pošalji</button>` |
| `<div>`        | [Block element](https://www.w3schools.com/html/html_blocks.asp#:~:text=A%20block%2Dlevel%20element%20always,p%3E%20and%20.) za grupiranje sadržaja | - | `<div> ... </div>` |
| `<span>`       | [Inline element](https://www.w3schools.com/html/html_blocks.asp#:~:text=A%20block%2Dlevel%20element%20always,p%3E%20and%20.) za grupiranje sadržaja | - | `<span> ... </span>` |
| `<br>`         | Prelom linije | - | `Tekst<br>Prelomljena linija` |
| `<hr>`         | Horizontalna linija | - | `<hr>` |
| `<b>`          | Podebljani tekst | - | `<b>Podebljano</b>` |
| `<i>`          | Kurziv tekst | - | `<i>Kurziv</i>` |
| `<u>`          | Podvučeni tekst | - | `<u>Podvučeno</u>` |

### Primjer upotrebe `id` atributa:
Atribut `id` koristi se za jedinstveno identificiranje gotovo bilo kojeg HTML elementa na stranici. `id` atribut mora biti **jedinstven unutar cijelog dokumenta**. 

Sintaksa: `<tag id="jedinstveniID">`.

```html
<style>
    #jedinstveniElement {
        color: blue;
        font-size: 20px;
    }
</style>
<body>
    <p id="jedinstveniElement">Ovo je paragraf s jedinstvenim ID atributom.</p>
</body>
</html>
```

### Primjer upotrebe `class` atributa:
Atribut `class` koristi se za grupiranje više elemenata koji dijele iste stilove ili ponašanje. Elementi mogu imati **više klasa odvojenih razmakom**. 

Sintaksa: `<p class="klasa1 klasa2 klasa3 klasaN...">`.

```html
<style>
    .crveniTekst {
        color: red;
    }
    .velikiTekst {
        font-size: 24px;
    }
</style>
<body>
    <p class="crveniTekst">Ovo je paragraf s crvenim tekstom.</p>
    <p class="velikiTekst">Ovo je paragraf s velikim tekstom.</p>
    <p class="crveniTekst velikiTekst">Ovo je paragraf s crvenim i velikim tekstom.</p>
</body>
</html>
```

### Primjer kombiniranja `id` i `class` atributa:
U ovom primjeru koristimo oba atributa kako bismo jedinstveno identificirali jedan element, dok ostala dva grupiramo pomoću klase `podnaslov`.

```html
<style>
    #glavniNaslov {
        color: green;
        font-size: 28px;
    }
    .podnaslov {
        color: gray;
        font-size: 18px;
    }
</style>
<body>
    <h1 id="glavniNaslov">Ovo je glavni naslov s ID atributom.</h1>
    <h2 class="podnaslov">Ovo je podnaslov s class atributom.</h2>
    <h2 class="podnaslov">Ovo je još jedan podnaslov s class atributom.</h2>
</body>
```
### CSS (Cascading Style Sheets)
**CSS** je jezik za stilizaciju HTML elemenata. Omogućuje nam definiranje izgleda i rasporeda elemenata na web stranici. CSS pravila sastoje se od selektora (***[eng. selectors](https://www.w3schools.com/cssref/css_selectors.php)***) i deklaracija svojstava ([***eng. declarations***](https://www.w3schools.com/css/css_syntax.ASP)). 

Sljedeća tablica pokriva osnovna CSS svojstva:

| Naziv svojstva | Opis | Vrijednosti | Primjer |
|----------------|------|-------------|---------|
| `color`        | Boja teksta | Naziv boje, heksadecimalna, RGB, RGBA, HSL, HSLA | `color: red;` |
| `background-color` | Boja pozadine | Naziv boje, heksadecimalna, RGB, RGBA, HSL, HSLA | `background-color: #f4f4f4;` |
| `background-image` | Slika pozadine | URL slike | `background-image: url('slika.jpg');` |
| `background-size` | Veličina slike pozadine | cover, contain, px, % | `background-size: cover;` |
| `font-size`    | Veličina fonta | px, em, rem, %, vw, vh | `font-size: 16px;` |
| `font-family`  | Obitelj fonta | Naziv fonta, lista fontova | `font-family: Arial, sans-serif;` |
| `font-weight`  | Debljina fonta | normal, bold, bolder, lighter, 100-900 | `font-weight: bold;` |
| `text-align`   | Poravnanje teksta | left, right, center, justify | `text-align: center;` |
| `margin`       | Vanjski razmak | px, em, %, auto | `margin: 10px;` |
| `padding`      | Unutarnji razmak | px, em, %, auto | `padding: 10px;` |
| `border`       | Obrub elementa | širina tip stil boje | `border: 1px solid #ccc;` |
| `border-radius` | Zaobljenost rubova | px, %, em | `border-radius: 5px;` |
| `width`        | Širina elementa | px, em, %, vw | `width: 100%;` |
| `height`       | Visina elementa | px, em, %, vh | `height: 50px;` |
| `display`      | Način prikaza | block, inline, inline-block, flex, grid, none | `display: block;` |
| `position`     | Pozicioniranje elementa | static, relative, absolute, fixed, sticky | `position: absolute;` |
| `top`, `right`, `bottom`, `left` | Pozicija elementa | px, %, em | `top: 10px;` |
| `overflow`     | Upravljanje preljevom sadržaja | visible, hidden, scroll, auto | `overflow: hidden;` |
| `z-index`      | Redoslijed prikazivanja elemenata | brojčana vrijednost | `z-index: 10;` |
| `opacity`      | Prozirnost elementa | vrijednost od 0 do 1 | `opacity: 0.5;` |
| `box-shadow`   | Sjenka okvira | x-offset y-offset blur-radius spread-radius boja | `box-shadow: 0 4px 8px rgba(0,0,0,0.1);` |
| `text-shadow`  | Sjenka teksta | x-offset y-offset blur-radius boja | `text-shadow: 1px 1px 2px black;` |
| `flex-direction` | Smjer fleksibilnog kontejnera | row, row-reverse, column, column-reverse | `flex-direction: row;` |
| `justify-content` | Poravnanje stavki duž glavne osi | flex-start, flex-end, center, space-between, space-around | `justify-content: center;` |
| `align-items`  | Poravnanje stavki duž poprečne osi | flex-start, flex-end, center, baseline, stretch | `align-items: center;` |
| `transition`   | Definira glatku animaciju prijelaza između različitih stilova | svojstvo, trajanje, kašnjenje, funkcija | `transition: width 0.3s ease-in-out;` |

Postoje i CSS pseudo-klase (***[Pseudo-classes](https://www.w3schools.com/css/css_pseudo_classes.asp)***) kao što su `:hover`, `:active`, `:focus` i druge koje se mogu nadodati na CSS klase. Mogu se koristiti za primjenu stilova na elemente u određenim stanjima ili uvjetima.

Tablica prikazuje neke od najčešće korištenih CSS pseudo-klasa:

| Pseudo-klasa | Opis | Primjer |
|--------------|------|---------|
| `:hover`     | Primjenjuje stil kada korisnik prelazi mišem preko elementa. | ```css a:hover { color: blue; } ``` |
| `:active`    | Primjenjuje stil kada je element aktiviran (npr. kliknut). | ```css button:active { background-color: green; } ``` |
| `:focus`     | Primjenjuje stil kada je element u fokusu (npr. odabran tipkovnicom). | ```css input:focus { border-color: red; } ``` |
| `:visited`   | Primjenjuje stil na posjećene linkove. | ```css a:visited { color: purple; } ``` |
| `:link`      | Primjenjuje stil na neposjećene linkove. | ```css a:link { color: blue; } ``` |
| `:first-child` | Primjenjuje stil na prvi dijete elementa. | ```css p:first-child { font-weight: bold; } ``` |
| `:last-child` | Primjenjuje stil na zadnji dijete elementa. | ```css p:last-child { font-style: italic; } ``` |
| `:nth-child(n)` | Primjenjuje stil na n-ti dijete elementa. | ```css li:nth-child(2) { color: red; } ``` |
| `:not(selector)` | Primjenjuje stil na sve elemente koji ne odgovaraju zadanom selektoru. | ```css p:not(.highlight) { color: grey; } ``` |
| `:checked`   | Primjenjuje stil na odabrane (checked) elemente kao što su checkbox ili radio button. | ```css input:checked { background-color: yellow; } ``` |
| `:disabled`  | Primjenjuje stil na onemogućene (disabled) elemente. | ```css input:disabled { background-color: lightgrey; } ``` |
| `:enabled`   | Primjenjuje stil na omogućene (enabled) elemente. | ```css input:enabled { background-color: white; } ``` |
| `:empty`     | Primjenjuje stil na elemente koji nemaju djece (prazne elemente). | ```css div:empty { display: none; } ``` |

# 1. DOM manipulacija
Nakon stjecanja osnovnog razumijevanja JavaScript varijabli, funkcija, struktura i metoda, sada smo spremni za početak manipulacije **Document Object Model**, odnosno DOM-om, što uključuje dinamičko upravljanje HTML elementima i njihovim CSS svojstvima.

**Document Object Model (DOM)** je standard koji definira strukturu i način pristupa HTML dokumentima. DOM predstavlja HTML dokument kao stablo objekata, gdje svaki HTML element predstavlja objekt, a svaki atribut i sadržaj elementa predstavlja svojstvo tog objekta.

<img src="./screenshots/DOM.png" style="width:25%"></img> 
> Izvor: https://en.wikipedia.org/wiki/Document_Object_Model

## 1.1 Osnovni DOM element

`Document` objekt je ključna komponenta u JavaScriptu koja predstavlja cijelu web stranicu u trenutnom pregledniku. On omogućava pristupanje i manipulaciju svim elementima na stranici, kao i njihovim svojstvima i sadržaju. Olakšava dinamičko upravljanje sadržajem stranice, što je ključno za stvaranje interaktivnih i responzivnih korisničkih iskustava.

Možemo ga zamisliti kao korijenski čvor HTML dokumenta (slika iznad).

`document` objekt možemo referencirati direktno ili preko `window` objekta.

```javascript
// Referenciranje document objekta
let doc = document;

// ili
let doc = window.document;
```

`document` objekt ima brojna svojstva i metode, mi ćemo u ovoj skripti baviti prvenstveno metodama, no to mogu biti i svojstva. Na primjer, `document.title` vraća naslov stranice, a `document.URL` vraća URL stranice.

```javascript
console.log(document.title); // Ispisuje naslov stranice
console.log(document.URL); // Ispisuje URL stranice
```

## 1.2 Dohvaćanje DOM elemenata
Kako bismo uopće mogli raditi sa DOM elementima prvo ih moramo "dohvatiti".

Imamo zadan sljedeći HTML gdje želimo izvući vrijednosti iz pojedinih elemenata.
```html
<p id="mojID">Ja sam paragraf 1</p> <!-- ID -->
<input type="text" name="ime" id="form_ime" class="mojInput" value="Marko" /> <!-- ID, class -->
<input type="text" name="prezime" id="form_prezime" class="mojInput" value="Marić" /> <!-- ID, class -->
<p class="mojaKlasa">Ja sam paragraf 2</p> <!-- class -->
<span class="mojaKlasa">Ja sam span</span> <!-- class -->
<p>Ja sam paragraf 3</p>
```

HTML elementi se mogu dohvatiti na sljedeće načine:

| Metoda | Objašnjenje |	Sintaksa |	Primjer |
|--------|-------------|-------------|----------|
| `getElementById(x)` | Vraća prvi element po jedinstvenom `Id`-u. | `document.getElementById(x)` | `document.getElementById("mojID")`
| `getElementsByTagName(x)` | Vraća sve elemente po HTML `tagu`-u. | `document.getElementsByTagName(x)` | `document.getElementsByTagName("p")`
| `getElementsByClassName(x)` | Vraća sve elemente po klasi/klasama ili kombinaciji HTML `tag`-a i klase (`class`). | `document.getElementsByClassName(x)` | `document.getElementsByClassName("mojaKlasa")`
| `getElementsByName(x)` | Vraća sve elemente po imenu. | `document.getElementsByName(x)` | `document.getElementsByName("ime")`
| `querySelector(x)` | Vraća **prvi element** koji odgovara određenom selektoru ili grupi selektora. Ako nema pronađenih podudaranja, vraća `null`. | `document.querySelector(x)` | `document.querySelector("#mojID")`<br>`document.querySelector(".mojaKlasa")`<br>`document.querySelector("p")`<br>`document.querySelector("input[name='ime']")`
| `querySelectorAll(x)` | Vraća **sve elemente** koji odgovaraju određenom selektoru ili grupi selektora. Ako nema pronađenih podudaranja, vraća `null`. | `document.querySelectorAll(x)` |  `document.querySelectorAll("#mojID")`<br>`document.querySelectorAll(".mojaKlasa")`<br>`document.querySelectorAll("p")`<br>`document.querySelectorAll("input[name='ime']")`

U sljedećem JavaScript kôdu možete vidjeti primjere dohvaćanja elemenata koristeći metode iz tablice.

```javascript
// Dohvaćanje prvog DOM elementa po ID-u
const mojDiv = document.getElementById('mojID');
console.log("Dohvaćen po ID-u: " + mojDiv.innerHTML);

// Dohvaćanje DOM elemenata po tagu
const paragrafi = document.getElementsByTagName('p');
for (let paragraf of paragrafi){
    console.log("Dohvaćen po tagu: " + paragraf.innerHTML);
}

// Dohvaćanje DOM elemenata po klasi
const sveKlase = document.getElementsByClassName('mojaKlasa');
for (let klasa of sveKlase){
    console.log("Dohvaćen po klasi: " + klasa.innerHTML);
}

// Dohvaćanje DOM elemenata po imenu
const svaImena = document.getElementsByName('ime');
for (let ime of svaImena){
    console.log("Dohvaćen po imenu: " + ime.value);
}

// Dohvaćanje prvog DOM elemenata koristeći querySelector
const query1 = document.querySelector('#form_prezime');
console.log("Dohvaćen koristeći querySelector: " + query1.value);
const query2 = document.querySelector('span');
console.log("Dohvaćen koristeći querySelector: " + query2.innerHTML);
const query3 = document.querySelector('.mojaKlasa');
console.log("Dohvaćen koristeći querySelector: " + query3.innerHTML);
const query4 = document.querySelector("input[name='ime']");
console.log("Dohvaćen koristeći querySelector: " + query4.value);

// Dohvaćanje svih DOM elemenata koristeći querySelectorAll
const queryAll = document.querySelectorAll('p');
for (let query of queryAll){
    console.log("Dohvaćen koristeći querySelectorAll: " + query.innerHTML);
}
```

> `querySelector` uvijek prvo pretražuje po `tag`-u, za pretraživanje po `id`-u treba koristiti oznaku `#`.
>  za pretraživanje po klasi treba koristiti `.` dok za pretraživanje po imenu ili drugim atributima prvo treba staviti ime `tag`-a pa unutar uglatih zagrada pretragu `[atribut = vrijednost]`

### Primjer 1. - Dohvaćanje elemenata
Za zadani HTML kôd, treba dohvatiti `<input>` s vrijednošću **TOČNO**. Ne smijemo koristiti `id` atribut i naknadno mijenjati HTML.
```html
<div class="moja-forma glavni2">
    <span name="ime">KRIVO</span>
    <span name="prezime">KRIVO</span>
</div>
<span class="moja-forma glavni">
    <span name="ime">KRIVO</span>
    <span name="prezime">KRIVO</span>
</span>
<div class="moja-forma glavni">
    <span name="prezime">KRIVO</span>
    <span name="ime">TOČNO</span>
    <i name="ime">KRIVO</i>
</div>
<div class="druga-forma glavni">
    <span name="prezime">KRIVO</span>
    <span name="ime">KRIVO</span>
</div>
```
Treba dohvatiti prvi `<span>` element s imenom `"ime"`: (`<span name="ime"/>`), a koji se nalazi unutar `<div>` elementa s klasama `"moja-forma glavni"` (`<div class="moja-forma glavni">`)."

>Rješenje:
```javascript
const query = document.querySelector("div.moja-forma.glavni span[name='ime']"); // Pogledati definiciju selektora u tablici
console.log(query.innerHTML) 
```

## 1.3 Svojstva DOM elemenata
DOM Elementi imaju mnogo svojstava, od kojih smo već neka koristili neka za dohvaćanje sadržaja elemenata poput `innerHTML`.

**Možemo ih podijeliti u svojstva za**: 
- dohvaćanje i postavljanje atributa, 
- dohvaćanje sadržaja, 
- dohvaćanje stilova, 
- dohvaćanje djece i susjeda.

U sljedećoj tablici su prikazana neka od bitnijih svojstava:

| Svojstvo | Objašnjenje | Sintaksa |
|----------|-------------|----------|
| `id` | Vraća ili postavlja vrijednost `id` atributa elementa. | `element.id` | `"mojID"` |
| `tagName` | Vraća ime `tag`-a elementa velikim slovima. | `element.tagName` | `"DIV"` |
| `classList` | Vraća kolekciju klasa elementa. | `element.classList` |
| `className` | Vraća ili postavlja vrijednost `class` atributa elementa. | `element.className` |
| `innerHTML` | Vraća ili mijenja HTML sadržaj unutar elementa. | `element.innerHTML` |
| `outerHTML` | Vraća HTML elementa, uključujući sam element i njegov sadržaj. | `element.outerHTML` |
| `attributes` | Vraća kolekciju svih atributa elementa. | `element.attributes` |
| `style` | Vraća `style` atribut elementa. | `element.style` |
| `childElementCount` | Vraća broj direktne djece elementa. | `element.childElementCount` |
| `children` | Vraća kolekciju direktne djece elementa. | `element.children` |
| `firstElementChild` | Vraća prvo direktno dijete elementa. | `element.firstElementChild` |
| `lastElementChild` | Vraća posljednje direktno dijete elementa. | `element.lastElementChild` |
| `nextElementSibling` | Vraća sljedeći element nakon `element` u roditeljskom elementu. | `element.nextElementSibling` |
| `previousElementSibling` | Vraća element prije `element` u roditeljskom elementu. | `element.previousElementSibling` |

### Primjer 2 - Pristupanje sadržaju, `id`-u, `tag`-u, atributima i klasama elementa
```html
<div class="text-5xl">
    Hi!
</div>
<div id="mojID" class="text-5xl h-16 w-36 overflow-scroll">
    Hello, World!
</div>
```

```javascript
const element = document.getElementById('mojID');

console.log(element.innerHTML); // Output: " Hello, World! "
console.log(element.outerHTML); // Output: "<div id="mojID" class="text-5xl h-16 w-36 overflow-scroll"> Hello, World! </div>"

console.log(element.id); // Output: "mojID"
console.log(element.tagName); // Output: "DIV"

for (const attr of element.attributes) {
  console.log(`attr: ${attr.name} -> ${attr.value}`); 
  // Output: "attr: id -> mojID"
  // Output: "attr: class -> text-5xl h-16 w-36 overflow-scroll"
}
```
Međutim, kolekciju klasa možemo dohvatiti preko `className` ili `classList` svojstva. `className` vraća `string` svih klasa dok `classList` vraća `DOMTokenList` objekt koji omogućava korištenje `forEach` petlje.
```javascript
// Dohvaćanje klasa preko className
console.log(element.className); // Output: "text-5xl h-16 w-36 overflow-scroll"

// Dohvaćanje klasa preko classList
element.classList.forEach( klasa => {
  console.log(`class: ${klasa}`); 
  // Output: class: -> text-5xl
  // Output: class: -> h-16
  // Output: class: -> w-36
  // Output: class: -> overflow-scroll
})
```

>  `attributes` svojstvo **ne vraća polje objekata već objekt objekata** kao povratnu vrijednost, tako da je za iteraciju najbolje koristiti `for of` petlju. Međutim, `classList` vraća `DOMTokenList` koja omogućava korištenje `forEach` petlje.
> 
> `attributes` vraća kolekciju tipa `NamedNodeMap` koja nema mogućnost korištenja `forEach` petlje.

Elementu možemo direktno mijenjati ili dodati `id` koristeći `id` svojstvo. 

Možemo dohvatiti prvi `div` element s tekstom `"Hi!"` i dodati mu `id`: `"prviDiv"`.

```javascript
const element = document.querySelector('div')
console.log(element.outerHTML); //Output: "<div class="text-5xl"> Hi! </div>"
element.id = "prviDiv" // Dodavanje ID-a
console.log(element.outerHTML); //Output: "<div class="text-5xl" id="prviDiv"> Hi! </div>"
```

Sadržaj mu možemo promijeniti preko `innerHTML` svojstva.
```javascript
element.innerHTML = " Pozdrav! " //Mjenjanje sadržaja
console.log(element.outerHTML); //Output: "<div class="text-5xl" id="prviDiv"> Pozdrav! </div>"
```

> Mijenjanjem sadržaja preko `outerHTML` svojstva možemo prekrižiti cijeli element pa nije pametno to koristiti. 
> 
> Međutim, za navedeno postoje metode koje ćemo proći u poglavlju `Dodavanje i brisanje DOM elemenata`

### Vježba 1
**EduCoder šifra**: `funte_u_eure`

Pronašli smo idealni web shop u Engleskoj, međutim sve cijene su prikazane u funtama, a stranica nema ugrađenu konverziju valuta. Želimo da nam se automatski prikažu sve cijene u valuti eura. Zadatak nam je malo "hakirati" ovaj web shop bez da mijenjamo HTML kôd.

```html
<div class="item">
    <b>-</b>
    <span> Laptop </span>
    <u>1200</u>
    <span class="symbol">£</span>
</div>
<div class="item">
    <b>-</b>
    <span> PC </span>
    <u>1800</u>
    <span class="symbol">£</span>
</div>
<div class="item">
    <b>-</b>
    <span> Mouse & Keyboard </span>
    <u>200</u>
    <span class="symbol">£</span>
</div>
```
- Napišite funkciju `azurirajSimbol(klasa, noviSimbol)` koja će za danu klasu promijeniti unutarnji sadržaj svih klasa na novi sadržaj.
- Napišite funkciju `azurirajCijenu(tag)` koja će za dani `tag` napraviti konverziju unutarnjeg sadržaja (cijena) svih `tag`-ova iz cijene u funtama u cijenu u eurima, zaokruženo na dvije decimale.
- Devizni tečaj: `1£ = 1.16547€`

✅Rezultat:

![alt text](./screenshots/funte_u_eure.png)

>Rješenje:
```javascript
function azurirajSadrzaj(klasa, noviSimbol) {
  const query = document.querySelectorAll("."+klasa)
  for (let element of query) {
    element.innerHTML=noviSimbol; // Promjena sadržaja elementa
  }
}
function azurirajCijenu(tag) {
  const query = document.querySelectorAll(tag)
  for (let element of query) {
    element.innerHTML=(Number.parseFloat(element.innerHTML)*1.16547).toFixed(2); // Promjena sadržaja elementa (sadržaj dohvaćen s innerHTML je tipa string pa ga treba pretvoriti u broj, zato koristimo parseFloat metodu)
  }
}
azurirajSadrzaj("symbol", "€"); // Promjena simbola svugdje gdje imamo klasu "symbol"
azurirajCijenu("u"); // Ažuriraj cijenu svugdje gdje imamo tag "u"
```
### Primjer 3 - Manipulacija klasama

>Ako DOM elementu želimo direktno mijenjati ili dodati klasu `class` onda koristimo `className` svojstvo, ne `classList` svojstvo.

Primjerice, želimo ažurirati klasu elementa s ID-om `prviDiv` iz `text-5xl` u `text-6xl`

```html
<div id="prviDiv" class="text-5xl">
    Hi!
</div>
```

```javascript
const element = document.querySelector('#prviDiv')
console.log(element.outerHTML); //Output: "<div class="text-5xl id="prviDiv""> Hi! </div>"
element.className = "text-6xl" // Promjena klase elementa
console.log(element.outerHTML); //Output: "<div class="text-6xl" id="prviDiv"> Hi! </div>"
```

> `className` služi za postavljanje i dohvaćanje cijelog atributa klase odabranog elementa. Za dodavanje dodavanje, brisanje, promjenu i provjeru pojedine klase bolje je koristiti `classList` svojstvo.

Nad svojstvom `classList` mogu se pozvati dodatne metode koje nam olakšavaju manipulaciju klasom (`class`) elementa. 

| Metoda | Objašnjenje | Sintaksa |
|--------|-------------|---------|
| `add(className1, className2, ...)` | Dodaje jednu ili više CSS klasa elementu | `element.classList.add(x);` |
| `contains(className)` | Provjerava sadrži li element određenu CSS klasu | `element.classList.contains(x);` |
| `remove(className1, className2, ...)` | Uklanja jednu ili više CSS klasa iz elementa | `element.classList.remove(x);` |
| `replace(oldClassName, newClassName)` | Zamjenjuje postojeću CSS klasu s novom CSS klasom | `element.classList.replace(x, y);` |
| `toggle(className)` | Dodaje CSS klasu ako ju element nema/uklanja ako ju ima | `element.classList.toggle(x);` |


```html
<div id="mojID" class="text-6xl">
    Hello, World!
</div>
```

```javascript     
const element = document.querySelector('#mojID')
element.classList.add('italic'); // Dodajemo klasu "italic"
console.log(element.className); //Output: "text-6xl italic"

console.log(element.classList.contains('text-6xl')); // Output: true
element.classList.remove('text-6xl'); // Uklanjamo klasu "text-6xl"
console.log(element.className); //Output: "italic"

element.classList.replace('italic', 'underline'); // Zamjenjujemo klasu "italic" s "underline"
console.log(element.className); //Output: "underline"
element.classList.toggle('font-bold') // Dodajemo klasu "font-bold" jer je nema
console.log(element.className); //Output: "underline font-bold"
```

### Vježba 2
**EduCoder šifra**: `books`

Naišli smo na staru web stranicu s bibliotekom knjiga. Na stranici su prikazane knjige u tablici. Želimo promijeniti stil tablice i ćelija kako bi bila nam bila preglednija.

Zadan je sljedeći CSS i HTML kôd:
```html
<style>
    .slika {
        overflow: hidden;
        border-radius: 100%;
    }
    .tekst {
        color: black;
        font-size: 18x;
    }
    .tablica {
        width: 100%;
        background-color: white;
    }
    .celija {
        border: 1px solid #dddddd;
        text-align: left;
        padding: 8px;
    }
    .naslov {
        background-color: #00000065;
        font-size: 20px;
    }
    .velika {
        background-color: #4cb05065;
    }
    .broj-stranica {
        font-weight: bold;
    }
</style>   
<table class="slika tekst">
    <tr>
        <th>Naslov</th>
        <th>Autor</th>
        <th>Broj stranica</th>
    </tr>
    <tr>
        <td>Harry Potter and the Philosopher's Stone</td>
        <td>J. K. Rowling</td>
        <td class="broj-stranica">500</td>
    </tr>
    <tr>
        <td>The Lord of the Rings</td>
        <td>J. R. R. Tolkien</td>
        <td class="broj-stranica">1077</td>
    </tr>
    <tr>
        <td>Don Quixote</td>
        <td>Miguel de Cervantes</td>
        <td class="broj-stranica">120</td>
    </tr>
</table>
```
Koristeći `querySelector` i `classList` metode dodajte "tablica", "celija" i "naslov" na odgovarajuće elemente, ćeliji s najvećim brojem stranica dodajte klasu "velika".

![alt text](./screenshots/tablica_books.png)

> Rješenje:
```javascript
document.querySelector('table').classList.replace('slika', 'tablica'); // Zamjenjujemo klasu "slika" s "tablica"
document.querySelectorAll('th, td').forEach(element => { // Dodajemo klasu "celija" na sve <th> i <td> elemente
    element.classList.add('celija');
});
document.querySelectorAll('th').forEach(element => { // Dodajemo klasu "naslov" na sve <th> elemente
    element.classList.add('naslov');
});

let maxBrojStranica = 0;
let maxCelijaIndex = -1;
let query = document.querySelectorAll('.broj-stranica'); // Dohvaćamo sve elemente s klasom "broj-stranica"
query.forEach((celija, index) => { // Pronalazimo najveći broj stranica
    const brojStranica = parseInt(celija.innerHTML); // Pretvaramo sadržaj u broj
    if (brojStranica > maxBrojStranica) { // Ako je trenutni broj stranica veći od maksimalnog
        maxBrojStranica = brojStranica; // Postavljamo novi maksimalni broj stranica
        maxCelijaIndex = index; // Postavljamo index najvećeg broja stranica
    }
});
query[maxCelijaIndex].classList.add('velika')  // Dodajemo klasu "velika" na ćeliju s najvećim brojem stranica
```

### Primjer 4 - Dohvaćanje `child` i `sibling` elemenata.
Naučili smo dohvaćati elemente koristeći `querySelector` i `getElements` metode. Međutim, ponekad želimo dohvatiti djecu ili susjede određenog elementa. Za to možemo koristiti sljedeća svojstva:
`childElementCount`, 
`children`, 
`lastElementChild`, 
`nextElementSibling`, 
`previousElementSibling`

Imamo sljedeći HTML kôd:

```html
<div>
    Hi!
</div>
<div id="mojID">
    <span>Hello</span>
    <span>,</span>
    <span>World!</span>
</div>
<div>
    Bye!
</div>
```

Upotrijebit ćemo `querySelector` metodu za dohvaćanje elementa s ID-om `mojID` te potom iskoristiti navedena svojstva za dohvaćanje djece i susjeda tog elementa.

```javascript         
const element = document.querySelector('#mojID')
// Dohvaćanje broja djece elementa
console.log(element.childElementCount); // Output: 3

// Dohvaćanje djece elementa
for (const child of element.children) {
  console.log(`child: ${child.outerHTML}`); 
  // Output: "child: <span>Hello</span>"
  // Output: "child: <span>,</span>"
  // Output: "child: <span>World</span>"
}

// Ili tradicionalnom for petljom
for (let i = 0; i < element.childElementCount; i++) {
  console.log(`child: ${element.children.item(i).outerHTML}`); 
  // Output: "child: <span>Hello</span>"
  // Output: "child: <span>,</span>"
  // Output: "child: <span>World</span>"
}

console.log(element.firstElementChild.outerHTML); // Output: <span>Hello</span>
console.log(element.lastElementChild.outerHTML); // Output: <span>World</span>

console.log(element.nextElementSibling.outerHTML); // Output: "<div class="text-5xl"> Bye! </div>"
console.log(element.previousElementSibling.outerHTML); // Output: "<div class="text-5xl"> Hi! </div>"
```

> `children` svojstvo vraća `HTMLCollection` nad kojime se ne može pozvati `forEach` metoda. Međutim, imamo svojstvo `childElementCount` koje nam vraća broj djece elementa te omogućava iteraciju kroz djecu koristeći tradicionalnu `for` petlju i pristupanje pojedinom djetetu preko indexa metodom `item()`

### Vježba 3
**EduCoder šifra**: `web_scraping`

Radimo na projektu analize podataka, gdje trebamo prikupiti informacije s više web stranica škola. Nažalost, te stranice nemaju svoj API za dohvaćanje podataka.
Možemo koristiti web scraping, tehniku koja se koristi za ekstrakciju podataka s web stranica. U te svrhe moramo dobro poznavati HTML strukturu stranice, kao i manipulaciju DOM elementima.

Zadan je sljedeći HTML kôd:
```html
<div id="studenti">
    <div>
        <b>Ivo</b>
        <b>Ivić</b>
        <u class="email">ivoivic@skole.hr</u>
        <span>3</span>
    </div>
    <div>
        <b>Ana</b>
        <b>Anić</b>
        <span>5</span>
    </div>
    <div>
        <b>Maja</b>
        <b>Majić</b>
        <u class="email">majamajic@skole.hr</u>
        <span>none</span>
    </div>
    <div>
        <b>Marko</b>
        <b>Marić</b>
        <u class="email">markomaric@skole.hr</u>
        <span>1</span>
    </div>
</div>
```

Zadan je konstruktor `Student`:
```javascript
function Student(ime, prezime, email, ocjena, opisnaOcjena) {
    this.ime = ime;
    this.prezime = prezime;
    this.email = email;
    this.ocjena = ocjena;
    this.opisnaOcjena = opisnaOcjena;
    this.oStudentu = () => console.log(`${this.ime} ${this.prezime} s emailom ${this.email} ima ocjenu ${this.opisnaOcjena}`)
}
```
1. Napišite funkciju `dodajStudente(id, poljeStudenata)` koja:
- Za svako dijete elementa s danim `id`-em
    - Ekstrahira podatke o *imenu*, *prezimenu*, *emailu* i *ocjeni* koristeći samo `firstElementChild`, `lastElementChild`, `nextElementSibling`, `previousElementSibling` i `classList` metode
    - Ako nedostaje *email*, postavlja ga na `"nema podatka"`
    - Pretvara ocjenu u format: od "odličan" do "nedovoljan" za ocjene od `5` do `1`, ili "nema ocjenu" za ostalo
    - Dodaje svakog studenta u polje studenti i vraća novoizgrađeno polje

2. Spremite sve studente koji imaju ocjenu u polje `filtriraniStudenti`.
- Za svakog studenta koji ima ocjenu, pozovite metodu `oStudentu()` (metoda već definirana u konstruktoru `Student`)

Napišite funkciju `prosjekStudenata(poljeStudenata)` koja vraća prosjek studenata:
- spremite u `sumaOcjena` varijablu sumu svih ocjena studenata koristeći `reduce()` metodu
- spremite u `prosjek` varijablu prosjek ocjena zaokruženo na dvije decimale

Konstruktor `Student` možete ažurirat ako je potrebno s dodatnim metodama ili ažurirat metodu `oStudentu()`.

✅Rezultat:
```javascript         
dodajStudente('studenti');

// Output: "Ivo Ivić s emailom "ivoivic@gmail.com" ima ocjenu dobar"
// Output: "Ana Anić s emailom "nema podatka" ima ocjenu odličan"
// Output: "Marko Marić s emailom "markomaric@gmail.com" ima ocjenu nedovoljan"

console.log(`Prosjek ocjena studenata: ${prosjekStudenata(filtriraniStudenti)}`);

// Output: "Prosjek ocjena studenata: 3.00"
```
   
>Rješenje:

```javascript      
function dodajStudente(html_element_id) {
    const elementiStudenata = document.getElementById(html_element_id).children;
    const poljeStudenata = [];
    // Iteriramo tradicionalnom for petljom kroz svu djecu elementa s danim ID-em (html_element_id)
    // Kôd počiva na pretpostavci da su svi elementi u polju redom: ime, prezime, email, ocjena
    for (let i = 0; i < elementiStudenata.length; i++) {
        const student = elementiStudenata[i];

        const imeElement= student.firstElementChild;
        const ime = imeElement.innerHTML;
        const prezime = imeElement.nextElementSibling.innerHTML;

        const ocjenaElement = student.lastElementChild;
        const ocjena = student.lastElementChild.innerHTML;

        let opisnaOcjena = "nema ocjenu";
        let email = "nema podatka";

        if (ocjenaElement.previousElementSibling.classList.contains('email'))
          email = ocjenaElement.previousElementSibling.innerHTML;

        switch (ocjena) {
            case "5":
                opisnaOcjena = 'odličan';
                break;
            case "4":
                opisnaOcjena = 'vrlo dobar';
                break;
            case "3":
                opisnaOcjena = 'dobar';
                break;
            case "2":
                opisnaOcjena = 'dovoljan';
                break;
            case "1":
                opisnaOcjena = 'nedovoljan';
                break;
            default:
                opisnaOcjena = 'nema ocjenu';
                break;
        }
        // Pozivanjem konstruktora stvaramo novi objekt s ekstrahiranim podacima
        poljeStudenata.push(new Student(ime, prezime, email, ocjena, opisnaOcjena));
    }
    return poljeStudenata;
}

// Pozivamo funkciju za ID "studenti"
let studenti = dodajStudente('studenti');

// U polje filtriraniStudenti spremamo sve studente koji imaju ispravnu ocjenu
const filtriraniStudenti = studenti.filter(student => student.opisnaOcjena != "nema ocjenu");
filtriraniStudenti.forEach(student => student.oStudentu());

function prosjekStudenata(poljeStudenata) {
  let sumaOcjena = poljeStudenata.reduce((total, student) => total+Number.parseInt(student.ocjena), 0);
  let prosjek = (sumaOcjena/poljeStudenata.length).toFixed(2);
  return prosjek;
}

console.log(`Prosjek ocjena studenata: ${prosjekStudenata(filtriraniStudenti)}`);
```

## 1.4 Dodavanje i brisanje DOM elemenata
Dodavanje i brisanje elemenata omogućuje dinamičke izmjene stranice temeljem korisničkih akcija ili događaja. 

Dosad smo naučili kako da dohvaćamo i mijenjamo elemente, međutim dodavanje novih elemenata je dosta nezgodno koristeći svojstvo `innerHTML`. Iz tog razloga postoje i metode za dodavanja, umetanje i brisanje elemenata:

| Metoda                   | Objašnjenje                                                  | Sintaksa                                              |
|--------------------------|--------------------------------------------------------------|-------------------------------------------------------|
| `createElement()`        | Stvara novi HTML element prema definiranom `tag`-u                                   | `document.createElement(tagName)`                    |
| `append()`               | Dodaje element(e) (`newElement`) kao posljednje dijete.           | `element.append(child1, child2, ...)`                 |
| `prepend()`              | Dodaje element(e) (`newElement`) kao prvo dijete.                 | `element.prepend(child1, child2, ...)` | 
`before()`               | Dodaje element(e) (`newElement`) ispred odabranog elementa.                | `element.before(newElement)`                  |
| `after()`                | Dodaje element(e) (`newElement`) iza odabranog elementa.                   | `element.after(newElement)`                           |                       |
| `insertAdjacentElement()`| Dodaje novi element u odabrani element, na zadanu poziciju (`position`).| `element.insertAdjacentElement(position, newElement)` |
| `insertAdjacentHTML()`   | Dodaje HTML tekst u odabrani element, na zadanu poziciju (`position`).| `element.insertAdjacentHTML(position, html)`          |
| `remove()`               | Uklanja element iz DOM-a.                                   | `element.remove()`                                    |
| `replaceWith()`          | Zamjenjuje odabrani element novim elementom (`newElement`).                | `element.replaceWith(newElement)`                    |

U kôdu za `insertAdjacentElement()` i `insertAdjacentHTML()` koristimo atribut `position` koji označava gdje se sadržaj dodaje, mora biti postavljen na jednu od sljedećih vrijednosti:

- `beforebegin`: prije elementa
- `afterbegin`: unutar elementa, prije njegovog prvog djeteta
- `beforeend`: unutar elementa, nakon njegovog posljednjeg djeteta
- `afterend`: nakon elementa

### Primjer 5 - Stvaranje, dodavanje, brisanje i izmjena DOM elemenata

```html
<style>
    #mojID {
        background-color: lightgray;
    }
    .hello-world {
        background-color: darkGray;
    }
</style>
<div id="mojID">
    <div class="hello-world">
        Hello, World!
    </div>
</div>
```
Dodavanje novih elemenata koristeći metode: `append()`, `prepend()`, `before()`, `after()`
```javascript
const mojElement = document.getElementById('mojID');

// Stvaramo nove elemente
const divAppend = document.createElement('div')
const divPreppend = document.createElement('div')
const divAfter = document.createElement('div')
const divBefore = document.createElement('div')

// Postavljamo sadržaj novih elemenata
divAppend.innerHTML = 'divAppend'
divPreppend.innerHTML = 'divPreppend'
divAfter.innerHTML = 'divAfter'
divBefore.innerHTML = 'divBefore'

// Raspoređujemo nove elemente
mojElement.append(divAppend);
mojElement.prepend(divPreppend);
mojElement.after(divAfter);
mojElement.before(divBefore);
```
Ili s metodom: `insertAdjacentElement()`
```javascript
const mojElement = document.getElementById('mojID');

// Stvaramo nove elemente
const divAppend = document.createElement('div')
const divPreppend = document.createElement('div')
const divAfter = document.createElement('div')
const divBefore = document.createElement('div')

// Postavljamo sadržaj novih elemenata
divAppend.innerHTML = 'divAppend'
divPreppend.innerHTML = 'divPreppend'
divAfter.innerHTML = 'divAfter'
divBefore.innerHTML = 'divBefore'

// Raspoređujemo nove elemente
mojElement.insertAdjacentElement("beforebegin", divBefore);
mojElement.insertAdjacentElement("afterbegin", divPreppend);
mojElement.insertAdjacentElement("beforeend", divAppend);
mojElement.insertAdjacentElement("afterend", divAfter);
```
Ili pak s metodom: `insertAdjacentHTML()`
```javascript
const mojElement = document.getElementById('mojID');

// Stvaramo nove elemente u obliku HTML stringa
const divAppend = "<div> divAppend </div>"
const divPreppend = "<div> divPreppend </div>"
const divAfter = "<div> divAfter </div>"
const divBefore = "<div> divBefore </div>"

// Raspoređujemo nove elemente
mojElement.insertAdjacentHTML("beforebegin", divBefore);
mojElement.insertAdjacentHTML("afterbegin", divPreppend);
mojElement.insertAdjacentHTML("beforeend", divAppend);
mojElement.insertAdjacentHTML("afterend", divAfter);
```
![alt text](screenshots/dodavanje_elementa.png)

Brisanje radimo jednostavno koristeći metodu `remove()`. Na primjer, brisanje prvog `child` elementa, `div`-a gdje je `id`=`"mojDiv"`
```javascript
const elementZaBrisanje = mojElement.firstElementChild;
elementZaBrisanje.remove()
```
![alt text](screenshots/brisanje_elementa.png)

Izmjena `div` elementa nakon `div`-a gdje je `id`=`"mojDiv"`:
```javascript
const elementZaMjenjanje = mojElement.nextElementSibling;

const newBoldElement = document.createElement('b')
newBoldElement.innerHTML = "newBoldElement"

elementZaMjenjanje.replaceWith(newBoldElement)
```
![alt text](screenshots/replace_element.png)

### Vježba 4 
**EduCoder šifra**: `html_from_object`

U web programiranju često ćemo morati grafički prikazati podatke iz dinamičkih struktura i različitih izvora podataka. Ako se mijenjaju samo pojedinačne vrijednosti u strukturi, dovoljno je samo izmjeniti postojeće definirane HTML elemente. Međutim, ako se struktura mijenja, ili se povečava/smanjuje količina podataka, tada je potrebno dinamički i dodavati/brisati HTML elemente.

U praksi često za nas ove probleme rješavaju razvojni okviri za JavaScript, ili neka biblioteka, ali je dobro znati kako stvari funkcioniraju "ispod haube".

Zadan je sljedeći HTML/CSS kôd:
```html
<style>
    #kupac {
        margin: 16px;
        padding: 16px;
        border-radius: 8px;
        background: #dedede;
        border: 1px solid darkgray;
        color: black;
        width: 400px;
        position: absolute;
        left: 50%;
        transform: translatex(-50%);
    } 
    h1 {
        font-size: 32px;
        font-weight: bold;
        text-align: center;
    }
    hr {
        border: 1px solid black;
        margin: 12px 0px;
    } 
    table {
        width: 100%;
    }
    th {
        text-align: left;
        border-bottom: 1px solid darkgray;
        padding-bottom: 4px;
    }
</style>
<div id="kupac">
</div>
```
Zadan je objekt `kupac`:
```javascript
let kupac = {
  ime: "Ivo",
  prezime: "Ivić",
  adresa: {
    ulica: "Ulica 123",
    grad: "Pula",
    postanskiBroj: "52100",
  },
  kontakt: {
    telefon: "0911234567",
    email: "iivic@gmail.com",
  },
  narudzbe: [
    {
      stavke: [
        {
          naziv: "Mobitel",
          kolicina: 1,
          cijena: 300,
        },
        {
          naziv: "Slušalice",
          kolicina: 1,
          cijena: 20,
        },
        {
          naziv: "Punjač",
          kolicina: 2,
          cijena: 10,
        },
      ],
      ukupnaCijena: function () {
        return this.stavke.reduce((ukupno, stavka) => ukupno+stavka.kolicina*stavka.cijena,0);
      },
      valuta: "eur",
    },
  ],
};
```

Objekt treba prikazati u obliku HTML-a koristeći metode za dodavanje elemenata.

✅Rezultat:

![alt text](screenshots/kupac.png)

>Rješenje: 
```javascript
// Dohvaćamo element s ID-om "kupac"
const divKupac = document.getElementById("kupac");
// Dodajemo naslov "KUPAC" u div element 
divKupac.insertAdjacentHTML("beforeend", "<h1>KUPAC</h1>")
// Dodajemo horizontalnu liniju
divKupac.append(document.createElement("hr"));
```
Kada smo dodali naslov i liniju, slijedi ispisivanje informacije o kupcu. Stvarat ćemo nove `div` elemente te im dodavati sadržaj koristeći `innerHTML` svojstvo.
```javascript	
const divImePrezime = document.createElement("div");
divImePrezime.innerHTML = `Ime i prezime: <b> ${kupac.ime} ${kupac.prezime} </b`
divKupac.append(divImePrezime);

const divAdresa = document.createElement("div");
divAdresa.innerHTML = `Adesa: <b> ${kupac.adresa.grad}, ${kupac.adresa.postanskiBroj} - ${kupac.adresa.ulica}</b>`
divKupac.append(divAdresa);

const divKontakt = document.createElement("div");
divKontakt.innerHTML = `Email: <b> ${kupac.kontakt.email} </b> | Telefon: <b> ${kupac.kontakt.telefon} </b>`
divKupac.append(divKontakt);

// Dodajemo horizontalnu liniju
divKupac.append(document.createElement("hr"));
```
Nakon što smo dodali informacije o kupcu, slijedi dodavanje tablice s narudžbama. Stvorit ćemo prvo tablicu, a naslove stupaca dodati koristeći `insertAdjacentHTML()` metodu.
```javascript
const tableNarudzbe = document.createElement("table");
const tableHeaders = document.createElement("tr");

tableHeaders.insertAdjacentHTML("beforeend", "<th>Naziv</th>")
tableHeaders.insertAdjacentHTML("beforeend", "<th>Kolicina</th>")
tableHeaders.insertAdjacentHTML("beforeend", "<th>Cijena</th>")
tableHeaders.insertAdjacentHTML("beforeend", "<th>Ukupno</th>")

tableNarudzbe.append(tableHeaders);
```
Nakon što smo dodali naslove stupaca, slijedi dodavanje redova tablice s podacima o narudžbama. Iterirat ćemo kroz sve stavke narudžbe i dodati ih u tablicu.
```javascript
for (let stavka of kupac.narudzbe[0].stavke) {
  const tableRow = document.createElement("tr");
  tableRow.insertAdjacentHTML("beforeend", `<td>${stavka.naziv}</td>`)
  tableRow.insertAdjacentHTML("beforeend", `<td>${stavka.kolicina}</td>`)
  tableRow.insertAdjacentHTML("beforeend", `<td>${stavka.cijena}</td>`)
  tableRow.insertAdjacentHTML("beforeend", `<td>${stavka.cijena*stavka.kolicina}</td>`)
  tableNarudzbe.append(tableRow);
}

divKupac.append(tableNarudzbe);
// Još jedna horizontalna linija
divKupac.append(document.createElement("hr"));
```
Na kraju, dodajemo boldano ukupnu cijenu narudžbe.
```javascript
const divUkupno = document.createElement("div");
divUkupno.innerHTML = `Ukupno: <b> ${kupac.narudzbe[0].ukupnaCijena()} </b> ${kupac.narudzbe[0].valuta.toUpperCase()}`
divKupac.append(divUkupno);

console.log(divKupac.outerHTML);
```

## 1.4 DOM events

DOM događaji (**eng. DOM events**) omogućuju JavaScriptu da reagira na korisničke akcije kao što su klikovi mišem, različite kretnje mišem, unos na tipkovnici i sl. Događaj se na `element` dodaje metodom `addEventListener(event, callbackFn)`.
- `callbackFn`: callback koji prima argument `event` a koji se odnosi na pozvani događaj. Da bi se moglo pristupati elementu nad kojim se pozvao `event`, koristi se svojstvo `target`.

Sintaksa ove callback funkcije metode `addEventListener` je sljedeća:
```javascript
// Select the element to attach the event listener to
const element = document.querySelector('#yourElementId'); // Replace '#yourElementId' with the actual element selector

// Define the callback function
function callbackFn(event) {

    // Prevencija defaultne akcije (npr. spriječavanje slanja forme unutar <form> elementa)
    event.preventDefault();

    // Dohvaćanje svojstava: target, type, itd (najčešće se dohvaća target)
    const target = event.target;
    const eventType = event.type;

    // Neka akcija koja se izvršava kada se događaj aktivira
    console.log(`Event type: ${eventType}`);
    console.log(`Event target: ${target}`);

    // Primjer: change the background color of the element
    target.style.backgroundColor = 'yellow';
}
```

Uzmimo primjer gdje želimo promijeniti boju pozadine elementa kada se klikne na njega:
```html
<button id="btn">Klikni me</button>
```
Prvo dohvaćamo element na koji želimo dodati događaj:
```javascript
const btn = document.getElementById("btn");
```
Zatim dodajemo događaj klikanja na taj element:
```javascript
// 1. način
btn.addEventListener("click", function (event) {
    console.log(event.target.outerHTML)
});
// Output: "<button id="btn">Klikni me</button>" 
```
`callbackFn` se može pisati i kao arrow funkcija:
```javascript
// 2. način
btn.addEventListener("click", (event) => {
    console.log(event.target.outerHTML)
});

// 3. način (kratki zapis jer je samo jedan argument)
btn.addEventListener("click", event => {
    console.log(event.target.outerHTML)
});

// 4. način (kratki zapis jer je samo jedan argument i jedna naredba)
btn.addEventListener("click", event => console.log(event.target.outerHTML));

// 5. način (callback funkcija je definirana izvan metode addEventListener)
const ispis = (event) => console.log(event.target.outerHTML);
btn.addEventListener("click", ispis);
```

`event` argument sadrži informacije o događaju koji se dogodio.
Napament ih nema smisla učiti (osim najčešće korištenih poput `click`, `input`, `focus`...) jer se mogu lako pronaći na internetu, ovisno o potrebi.

Ima ih mnogo, neki od najčešće korištenih na webu su:

| Metoda      | Objašnjenje                                      | Sintaksa                                       | Primjer                                   |
|-------------|--------------------------------------------------|------------------------------------------------|-------------------------------------------|
| click       | Poziva se kada se klikne mišem na element.       | `element.addEventListener('click', function() {})` | `button.addEventListener('click', function() { console.log('Kliknuto!'); })` |
dblclick    | Poziva se kada se dvaput klikne na element mišem. | `element.addEventListener('dblclick', function() {})` | `image.addEventListener('dblclick', function() { console.log('Dvaput kliknuto!'); })` |
| focus       | Poziva se kada element dobije fokus.             | `element.addEventListener('focus', function() {})` | `input.addEventListener('focus', function() { console.log('Fokusiranje!'); })` |
| focusin     | Poziva se kada element ili njegovi potomci dobiju fokus. | `element.addEventListener('focusin', function() {})` | `div.addEventListener('focusin', function() { console.log('Fokusiranje!'); })` |
| focusout    | Poziva se kada element ili njegovi potomci izgube fokus. | `element.addEventListener('focusout', function() {})` | `input.addEventListener('focusout', function() { console.log('Izgubio fokus!'); })` |
| blur        | Poziva se kada element izgubi fokus.             | `element.addEventListener('blur', function() {})`  | `input.addEventListener('blur', function() { console.log('Izgubio fokus!'); })` |
| mousedown   | Poziva se kada se pritisne miš na element.       | `element.addEventListener('mousedown', function() {})` | `div.addEventListener('mousedown', function() { console.log('Miš pritisnut!'); })` |
| mouseenter  | Poziva se kada miš uđe u element.                | `element.addEventListener('mouseenter', function() {})` | `div.addEventListener('mouseenter', function() { console.log('Miš unutar elementa!'); })` |
| mouseleave  | Poziva se kada miš napusti element.              | `element.addEventListener('mouseleave', function() {})` | `div.addEventListener('mouseleave', function() { console.log('Miš izvan elementa!'); })` |
| mousemove   | Poziva se kada se miš pomiče preko elementa.    | `element.addEventListener('mousemove', function() {})` | `div.addEventListener('mousemove', function() { console.log('Miš se pomiče!'); })` |
| mouseout    | Poziva se kada miš napusti element ili njegovog potomka. | `element.addEventListener('mouseout', function() {})` | `div.addEventListener('mouseout', function() { console.log('Miš napustio element!'); })` |
| mouseover   | Poziva se kada miš uđe u element ili njegovog potomka. | `element.addEventListener('mouseover', function() {})` | `div.addEventListener('mouseover', function() { console.log('Miš ušao u element!'); })` |
| mouseup     | Poziva se kada se miš otpusti iznad elementa.    | `element.addEventListener('mouseup', function() {})` | `div.addEventListener('mouseup', function() { console.log('Miš otpušten!'); })` |
| input       | Poziva se kada se promijeni vrijednost input elementa, a korisnik i dalje ostaje u polju. | `element.addEventListener('input', function() {})` | `input.addEventListener('input', function() { console.log('Vrijednost promijenjena!'); })` |
| change      | Poziva se kada se promijeni vrijednost elementa, a korisnik se miče od polja. | `element.addEventListener('change', function() {})` | `inputElement.addEventListener('change', function() { console.log('Vrijednost promijenjena!'); })` |

> Kroz sljedeće primjere i vježbe ćemo pokazati kako se koriste DOM događaji u JavaScriptu.

U svim primjerima koristit ćemo sljedeći CSS kôd:

```css
<style>
    div {
        padding: 4px 16px;
    }
    input, button {
        background: transparent;
        border: 1px solid gray;
        border-radius: 4px;
        padding: 2px 8px;
        margin: 4px 2px;
        &:hover {
            background: #a9a9a950;
        }
        &:focus {
            background: #4cb05050;
        }
        &:active {
            background: #ffeb3c50;
        }
    }
</style>
```

### Primjer 6 - `click` event

Dodajemo `input` polje i dva `button` elementa. Input polje predstavlja brojač, a dva button elementa povećavaju i smanjuju brojač za jedan.

```html
<div>
    <button id="increaseBtn">+</button>
    <input type="number" disabled name="broj" value="0"/>
    <button id="decreaseBtn">-</button>
</div>
```
Prvi korak je naravno dohvat elemenata:
```javascript
const increaseBtn = document.getElementById("increaseBtn");
const decreaseBtn = document.getElementById("decreaseBtn");
const broj = document.getElementsByName("broj")[0];
```
Zatim dodajemo događaje na `click` event za oba button elementa:
```javascript
increaseBtn.addEventListener("click", () => broj.value++) // povećava brojač za 1
decreaseBtn.addEventListener("click", () => broj.value--) // smanjuje brojač za 1
```

### Vježba 5
**EduCoder šifra**: `methods_to_methods`

Želimo napraviti aplikaciju koja će omogućiti korisniku da unese podatke o korisniku (ime, prezime, email) i da ih dodaje u listu korisnika. Korisnik može dodavati korisnike na početak ili kraj liste, te ih može brisati s početka ili kraja liste.

Koristit ćemo dobro poznate metode `Array` objekta. Za dodavanje korisnika koristit ćemo metode `push()` i `unshift()`, a za brisanje korisnika metode `pop()` i `shift()`.

Zadan je sljedeći HTML kôd:
```html
<div id="forma">
    Ime: <input type="text" name="Ime" placeholder="Ime..." />
    Prezime: <input type="text" name="Prezime" placeholder="Prezime..." />
    Email: <input type="text" name="Email" placeholder="Email..." />
</div>
<div>
    <!--Svaku metodu predstavit ćemo zasebnim gumbom-->
    <button id="push">push</button>
    <button id="pop">pop</button>
    <button id="unshift">unshift</button>
    <button id="shift">shift</button>
</div>
<div style="font-size: 24px;"><b>Korisnici:</b></div>
<div id="lista">
</div>
```

Zadatak je napisati implementacije funkcija: `dohvatiVrijednosti()`, `dodajNoviElement(pozicija)`, `ukloniElement(pozicija)` i dodati eventListenere za svaki button. 
```javascript
const inputs = document.getElementsByTagName('input');
const lista = document.getElementById('lista');
const forma = document.getElementById('forma');

const btn_push = document.getElementById('push');
const btn_pop = document.getElementById('pop');
const btn_unshift = document.getElementById('unshift');
const btn_shift = document.getElementById('shift');

let emailPolje = []

function dohvatiVrijednosti() {
    // Pseudokod:

    // Funkcija dohvaća vrijednosti iz "inputs" i vraća novi formatirani div element
    // Koristeći "for of" petlju ili "forEach" metodu iterira se kroz "inputs" (name, value) za svaki input
    // Ako je input prazan, defaultna vrijednost je "blank"
    return div; 
    /* Primjer div-a:
        <div>
            <b>Ime</b>: Ivan 
            <b>Prezime</b>: Ivić
            <b>Email</b>: iivic@gmail.com 
        </div>
    */
}
function dodajNoviElement(pozicija) {
    // Pseudokod:

    // Funkcija dodaje novi element ovisno o poziciji ("push", "unshift") switch(pozicija)
    // Vrijednost elementa dohvaća pomoću funkcije dohvatiVrijednosti()
    // Prije dodavanja provjerava je li email već dodan, ako je:
    // dodaje upozorenje "<div id="upozorenje" style="color: red;">Email već postoji!</div>"
    // inače dodaje novi element u polje i html te miče upozorenje
} 
function ukloniElement(pozicija) {
    // Pseudokod:

    // Funkcija briše element ovisno o poziciji ("pop", "shift") switch(pozicija)
    // Prije brisanja provjerava postoji li element
    // Ako postoji briše element iz polja
    // Miče upozorenje bez obzira postoji li element ili ne
}

//dodati eventListener-e za svaki button
```
✅Rezultat:

![alt text](screenshots/methods_to_methods.png)

>Rješenje:
 
```javascript
// Dohvaćamo sve elemente
const inputs = document.getElementsByTagName('input');
const lista = document.getElementById('lista');
const forma = document.getElementById('forma');

const btn_push = document.getElementById('push');
const btn_pop = document.getElementById('pop');
const btn_unshift = document.getElementById('unshift');
const btn_shift = document.getElementById('shift');

let emailPolje = []
// Funkcija koja dohvaća vrijednosti iz input polja i vraća novi formatirani div element
function dohvatiVrijednosti() {
  let div = document.createElement("div");
  for (const input of inputs) {
    div.innerHTML += `<b>${input.name}</b>: `;
    if (input.value == "") {
      div.innerHTML += "blank ";
    } else {
      div.innerHTML += input.value + " ";
    }
  }
  return div;
}

// Funkcija koja dodaje novi element ovisno o poziciji ("push", "unshift")
function dodajNoviElement(pozicija) {
  const email = document.getElementsByName('Email')[0].value;
  if (emailPolje.includes(email)) {
    if (document.getElementById("upozorenje") == undefined)
      forma.insertAdjacentHTML("afterend", `<div id="upozorenje" style="color: red;">Email već postoji!</div>`);
  }
  else {
    // Brišemo upozorenje
    let element = document.getElementById("upozorenje");
    if (element) element.remove();

    let vrijednost = dohvatiVrijednosti();
    switch(pozicija) {
      case "push": 
        lista.append(vrijednost);
        emailPolje.push(email);
        break;
      case "unshift": 
        lista.prepend(vrijednost);
        emailPolje.unshift(email);
        break;
    }
  }
}

// Funkcija koja briše element ovisno o poziciji ("pop", "shift")
function ukloniElement(pozicija) {
  switch(pozicija) {
    case "shift": 
      if (lista.firstElementChild != undefined)  {
        lista.firstElementChild.remove()
        emailPolje.shift();
      }
      break;
    case "pop": 
      if (lista.lastElementChild != undefined)  {
        lista.lastElementChild.remove()
        emailPolje.pop();
      }
      break;
  }
// Brišemo upozorenje
let element = document.getElementById("upozorenje");
if (element) element.remove();

}

// Dodajemo eventListenere za svaki button
btn_push.addEventListener("click", () => dodajNoviElement("push"))
btn_pop.addEventListener("click", () => ukloniElement("pop"))
btn_unshift.addEventListener("click", () => dodajNoviElement("unshift"))
btn_shift.addEventListener("click", () => ukloniElement("shift"))
```

### Primjer 7 - `focus` events
```html
<div id="inputi">
    <b>Ime:</b> <input id="ime" placeholder="Ime ..."/>
    <b>Prezime:</b> <input id="prezime" placeholder="Prezime ..."/>
</div>

<div>
    <b>Broj godina:</b> <input id="brojGodina" type="number" placeholder="Godina ..."/>
</div>

<div>
    <b>Element event:</b> <span id="event"> </span>
</div>
```
```javascript
const inputi = document.getElementById('inputi');
const inputBrojGodina = document.getElementById('brojGodina');

const span = document.getElementById('event');

inputBrojGodina.addEventListener('focus', event => span.textContent = "focus: " + event.target.outerHTML);
inputi.addEventListener('focusin', event => span.textContent = "focusin: " + event.target.outerHTML);
inputi.addEventListener('focusout', event => span.textContent = "focusout: " + event.target.outerHTML);
inputBrojGodina.addEventListener('blur', event => span.textContent = "blur: " + event.target.outerHTML);
```

> `focus` i `blur` se pozivaju samo za trenutni element, ignoriraju potomke, dok se `focusin` i `focusout` pozivaju za element i svakog potomka zasebno.

### Vježba 6
**EduCoder šifra**: `focus`

Zadan je sljedeći kôd:
```html
<div id="inputs">
    Lozinka: <input name="password" type="password"/>
    Ponovi lozinku: <input name="repeatPassword" type="password"/>
</div>
<div id="hint" style="color: green;">
</div>
```
```javascript
const inputs = document.getElementById('inputs');
const hint = document.getElementById('hint');
/* 
Potrebno je dodati dva event listener-a:
 > kada je input fokusiran, ovisno o inputu treba pisat odgovarajući hint
    za Lozinku:
      - Minimalna duljina lozinke mora biti 8
      - Lozinka mora imati barem jedno veliko slovo
      - Lozinka mora imati barem jedan broj
    za Ponovi lozinku:
      - Lozinke moraju biti iste
 > kada se izađe iz fokusa, hint treba biti prazan
*/
```

✅Rezultat:

![alt text](screenshots/fokus.png)

>Rješenje:

```javascript
const inputs = document.getElementById('inputs');
const hint = document.getElementById('hint');

inputs.addEventListener("focusin", (event) => {
  switch(event.target.name) {
    case "password":
      hint.innerHTML = `
      - Minimalna duljina lozinke mora biti 8 <br>
      - Lozinka mora imati barem jedno veliko slovo <br>
      - Lozinka mora imati barem jedan broj
      `;
      break;
    case "repeatPassword":
      hint.innerHTML = `
      - Lozinke moraju biti iste
      `;
      break;
  }
})
inputs.addEventListener("focusout", () => {
    hint.innerHTML = ``;
})

```

Zadan je sljedeći kôd:

### Primjer 8 - `mouse` events
```html
<div id="buttons" style="background: lightblue;">
    <button id="btn_1">1</button>
    <button id="btn_2">2</button>
    <button id="btn_3">3</button>
    <button id="btn_4">4</button>
</div>
```
```javascript
const buttons = document.getElementById('buttons');
const btn_1 = document.getElementById('btn_1');
const btn_2 = document.getElementById('btn_2');
const btn_3 = document.getElementById('btn_3');
const btn_4 = document.getElementById('btn_4');
const btnList = [btn_1, btn_2, btn_3, btn_4]

const span = document.getElementById('event');

buttons.addEventListener('mouseover', event => span.textContent = "mouseover: " + event.target.id);
buttons.addEventListener('mouseout', event => span.textContent = "mouseout: " + event.target.id);

buttons.addEventListener('mouseenter', event => console.log("mouseenter: " + event.target.id));
buttons.addEventListener('mouseleave', event => console.log("mouseleave: " + event.target.id));

for (const btn of btnList) {
  btn.addEventListener('mousedown', event => {
    console.log("[1] mousedown: " + event.target.id);
    span.textContent = "mousedown: " + event.target.id
  });
  btn.addEventListener('mouseup', event =>  {
    console.log("[2] mouseup: " + event.target.id);
    span.textContent = "mouseup: " + event.target.id
  });
  btn.addEventListener('click', event => console.log("[3] click: " + event.target.id));
}
```

> `mouseenter` i `mouseleave` se pozivaju samo za trenutni element, ignoriraju potomke, dok se `mouseover` i `mouseout` pozivaju za element i svakog potomka zasebno.

> `click` se uvijek poziva nakon `mousedown` i `mouseup` točno tim redom.

### Vježba 7
**EduCoder šifra**: `gallery`

Zadan je sljedeći kôd:
```html
<style>
.gallery {
  display: flex;
  flex-wrap: wrap;
}

.artwork {
  transition: all 0.2s ease-in-out;
  position: relative;
  height: 200px;
  width: auto;
  border-radius: 4px;
  margin: 10px;
  &:hover {
    scale: 105%;
  }
}

.opis { padding: 16px; }
h1 { font-size: 24px; font-weight: bold; }
h2 { font-size: 20px; }
h3 { font-size: 14px; }
</style>

<div class="gallery">
    <img class="artwork" id="artwork1" src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Mona_Lisa%2C_by_Leonardo_da_Vinci%2C_from_C2RMF_retouched.jpg/1200px-Mona_Lisa%2C_by_Leonardo_da_Vinci%2C_from_C2RMF_retouched.jpg">    
    <img class="artwork" id="artwork2" src="https://upload.wikimedia.org/wikipedia/en/1/14/Picasso_The_Weeping_Woman_Tate_identifier_T05010_10.jpg">    
    <img class="artwork" id="artwork3" src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/66/VanGogh-starry_night_ballance1.jpg/290px-VanGogh-starry_night_ballance1.jpg">
</div>
<div class="opis">
    <h1></h1>
    <h2></h2>
    <h3></h3>
</div>
```
```javascript
let galerija = [
  {
    id: "artwork1",
    naziv: "Mona Lisa",
    umjetnik: "Leonardo da Vinci",
    godina: 1503
  },
  {
    id: "artwork2",
    naziv: "The Weeping Woman",
    umjetnik: "Pablo Picasso",
    godina: 1937
  },
  {
    id: "artwork3",
    naziv: "The Starry Night",
    umjetnik: "	Vincent van Gogh",
    godina: 1889
  }
]
/* 
Potrebno je dodati dva event listener-a:
 > kada se mišem pređe preko slike
    - treba iz polja galerije iščitati točne podatke i prikazati ih u opisu
 > kada se mišem izađe iz galerije
    - isprazniti opis
*/
```

✅Rezultat:

![alt text](screenshots/gallery.png)

>Rješenje:
```javascript
let galerija = [
  {
    id: "artwork1",
    naziv: "Mona Lisa",
    umjetnik: "Leonardo da Vinci",
    godina: 1503
  },
  {
    id: "artwork2",
    naziv: "The Weeping Woman",
    umjetnik: "Pablo Picasso",
    godina: 1937
  },
  {
    id: "artwork3",
    naziv: "The Starry Night",
    umjetnik: "	Vincent van Gogh",
    godina: 1889
  }
]

const gallery = document.getElementsByClassName("gallery")[0];
const opis = document.getElementsByClassName("opis")[0];

gallery.addEventListener("mouseover", event => {
  let id = event.target.id;
  if (id == "") return;
  let artwork = galerija.find(g => g.id == id);
  opis.children[0].innerHTML =  artwork.naziv;
  opis.children[1].innerHTML =  artwork.umjetnik;
  opis.children[2].innerHTML =  artwork.godina+".";
})
gallery.addEventListener("mouseleave", event => {
  opis.children[0].innerHTML = "";
  opis.children[1].innerHTML = "";
  opis.children[2].innerHTML = "";
})
```

### Primjer 9 - `input` event
```html
<div>
    Lozinka: <input id="password" type="password"/>
    Ponovi lozinku: <input id="repeatPassword" type="password"/>
    Lozinke iste: <b id="same"></b>
</div>
```
```javascript
const password = document.getElementById("password");
const repeatPassword = document.getElementById("repeatPassword");
const same =  document.getElementById("same");

password.addEventListener("input", event => {
  same.innerHTML = event.target.value == repeatPassword.value;
});
repeatPassword.addEventListener("input", event => {
  same.innerHTML = event.target.value == password.value;
});
```

### Vježba 8
**EduCoder šifra**: `recommend`

Kreiramo aplikaciju za praćenje unosa u polje za pretraživanje. Korisnik će moći upisati pojam u polje za pretraživanje, a aplikacija će dinamički filtrirati rezultate kako korisnik tipka.
- Implementirajte funkciju `showResults(searchTerm)` koja će filtrirati rezultate na temelju unesenog teksta
- Klikom na rezultat popunjava se input i rezultati se izbrišu

Zadan je sljedeći kôd:
```html
<style>
    #searchInput {
        width: 100%;
        margin-bottom: 20px;
    }
    #searchResults {
        border: 1px solid #ccc;
        border-radius: 4px;
        padding: 10px;
    }
    #searchResults div {
        margin-bottom: 5px;
        cursor: pointer;
        &:hover {
            background-color: #f0f0f0;
        }
    }
</style>

<div>
    <input type="text" id="searchInput" placeholder="Search...">
    <div id="searchResults"></div>
</div>
```
```javascript
const inputField = document.getElementById('searchInput');
const resultsContainer = document.getElementById('searchResults');

const data = [
    'JavaScript',
    'HTML',
    'CSS',
    'React',
    'Node.js', 
    'Express.js',
    'MongoDB',
    'Vue.js',
    'Angular',
    'TypeScript'
];

function showResults(searchTerm) {

}

//eventListener
```

✅Rezultat:

![alt text](screenshots/recommend.png)

>Rješenje:
```javascript
const inputField = document.getElementById('searchInput');
const resultsContainer = document.getElementById('searchResults');

const data = [
    'JavaScript',
    'HTML',
    'CSS',
    'React',
    'Node.js',
    'Express.js',
    'MongoDB',
    'Vue.js',
    'Angular',
    'TypeScript'
];

function showResults(searchTerm) {
    const filteredData = data.filter(item => item.toLowerCase().includes(searchTerm.toLowerCase()));

    resultsContainer.innerHTML = '';

    filteredData.forEach(item => {
        const resultItem = document.createElement('div');
        resultItem.textContent = item;
        resultItem.addEventListener("click", event => {
          inputField.value = event.target.textContent;
          resultsContainer.innerHTML = '';
        })
        resultsContainer.appendChild(resultItem);
    });
}

inputField.addEventListener('input', event => {
    const searchTerm = event.target.value;
    showResults(searchTerm);
});
```

# Samostalni zadatak za vježbu 8

**EduCoder šifra**: `kosarica`

Aplikacija omogućuje korisniku dodavanje proizvoda u košaricu, promjenu količine proizvoda te uklanjanje proizvoda iz košarice.

Sučelje aplikacije sastoji se od polja za unos naziva i cijene proizvoda te gumba za dodavanje proizvoda u košaricu. Također, prikazuje se lista proizvoda u košarici s informacijama o nazivu, količini, cijeni po komadu te ukupnoj cijeni za taj proizvod.

Kada korisnik unese naziv i cijenu proizvoda te klikne na gumb `Dodaj artikl`, proizvod se dodaje u košaricu. 
 - Ako proizvod nema ime, dugme se ne može kliknuti, zatamnjeno je/onemogućeno
 - Ako se proizvod s istim imenom već nalazi u košarici, količina se povećava za `1`
 - Ako je novi, dodaje se na listu
 - Cijena proizvoda ne može ići ispod `0`

Korisnik može mijenjati količinu proizvoda u košarici koristeći gumbe `+` i `-` pored svakog proizvoda. Također, postoji opcija za uklanjanje proizvoda iz košarice klikom na gumb `Ukloni`.

Nakon svake promjene u košarici, ukupna cijena se automatski ažurira kako bi korisnik imao uvid u trenutni trošak.

Jedan primjer implementacije:
- Napravi se konstruktor `Proizvod(naziv, kolicina, cijena)` koji ima atribute `naziv`, `kolicina`, `cijena` i metodu `ukupnaCijena()` koja vraća ukupnu cijenu proizvoda zaokruženu na dvije decimale.

- Napraviti se objekt `kosarica` koja sadrži 
    - atribut `proizvodi` - lista proizvoda
    - metodu `dodajProizvod(proizvod)` - dodaje proizvod u HTML i polje `proizvodi`
    - metodu `dodajFunkcionalnosti(naziv)` - dodaje funkcionalnosti (`eventListener`-i) proizvodu:
        - povećanje količine
        - smanjenje količine
        - brisanje proizvoda
    - metodu `azurirajUkupnuCijenu()` - koristeći `reduce` nad poljem računa ukupnu cijenu svih proizvoda zaokruženu na dvije decimale

Primjer:

![alt text](screenshots/kosarica.png)

CSS i HTML korišten na slici:
```html
<style>
    body {
        padding: 64px;
        font-family: Sans-Serif;
    }
    .main {
        display: flex;
        width: 100%;
        height: 100%;
        justify-content: center;
    }
    .card {
        overflow: hidden;
        width: 100%;
        padding: 32px;
        display: flex;
        flex-direction: column;
        background-color: rgb(205, 205, 205, 0.1);
        border-radius: 8px;
        color: #353535;  
        box-shadow: 0px 0px 3px rgba(0, 0, 0, 0.2);
    }
    input, button {
        transition: all 0.2s ease-in-out;
        padding: 8px 16px;
        background: rgba(255, 255, 255, 0.5);
        outline: none;
        border: 1px solid rgba(0, 0, 0, 0.1);  
        border-radius: 8px;
        &:hover {
            background: rgba(255, 255, 255, 1);
            border: 1px solid rgba(0, 0, 0, 0.25);
        }
        &:focus {
            background: rgba(255, 255, 255, 1);
            border: 1px solid rgba(0, 0, 0, 0.25);
        }
    }
    button {
        background-color: #a5d6a7;
        &:hover {
            background: #83c683;
            cursor: pointer;
        }
    }
    form {
        overflow-y: hidden;
        min-height: 48px;
        overflow-x: auto;
        padding: 0px 16px;
        display: flex;
        margin-top: 16px;
        gap: 8px;
        justify-content: space-between;
        align-items: center;
        font-size: 14px;
        font-weight: bold;
    }
    .content {
        padding: 16px 16px;
        height: 100%;
        display: flex;
        flex-direction: column;
        overflow-y: auto;
    }
    .flex {
        width: 100%;
        display: inline-grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
    }
    .item-list {
        overflow-y: auto;
        overflow-x: hidden;
        padding: none !important;
        border-radius: 8px;
        margin-top: 16px;
    }
    .item {
        background-color: rgba(169, 169, 169, 0.2);
        padding: 8px 16px;
        align-items: center
    }
    .item:nth-child(2n) {
        background-color: rgba(169, 169, 169, 0.1);
    }
    .item-kolicina {
        width: 64px;
        text-align: center;
        margin-left: 8px;
        margin-right: 4px;
    }
    .item-kolicina-button {
        padding: 0px 4px;
        font-size: 24;
    }
    .item-kolicina-button:hover {
        padding: 0px 4px;
        color: #1f87e8;
        cursor: pointer;
    }
    .item-ukloni {
        color: #d81b43;
        font-size: 14;
        &:hover {
            text-decoration: underline;
            cursor: pointer;
        }
    }
    #ukupno {
        font-weight: normal;
    }
    .disabled {
        opacity: 0.5;
        cursor: not-allowed !important;
    }
</style> 
<div class="main">
    <div class="card">
        
        <h1 class="text-4xl mb-4 font-bold">Košarica</h1>
        
        <hr />
        
        <form>
            <label for="naziv_proizvoda">Naziv proizvoda:</label>
            <input type="text" name="naziv_proizvoda" id="naziv_proizvoda" placeholder="Upiši naziv proizvoda..." />
            <label for="cijena_proizvoda">Cijena proizvoda:</label>
            <input type="number" value="1" min="0" name="cijena_proizvoda" id="cijena_proizvoda" placeholder="Upiši cijenu proizvoda..." />
            <button disabled class="whitespace-nowrap disabled" type="button" name="dodaj_button" id="dodaj_button">Dodaj artikl</button>
        </form>
        
        <hr /> 

        <div class="content">
            <div class="flex" style="font-size: 18; color: #787878;">
                <b> Naziv </b>
                <b> Količina </b>
                <b> Cijena </b>
                <b> Ukupno </b>
            </div>
            
            <div id="item_list" class="item-list">
                <div class="flex item" id="item_Jabuka"><b>        
                        Jabuka 
                    </b>
                    <div style="display: flex; align-items: center">
                        <b class="item-kolicina-button item-kolicina-minus" id="item_kolicina_minus_Jabuka">-</b>
                        <input name="kolicina" id="item_kolicina_Jabuka" class="item-kolicina" value="4" disabled="">
                        <b class="item-kolicina-button item-kolicina-plus" id="item_kolicina_plus_Jabuka">+</b>
                    </div>
                    <div>
                        0.25 €
                    </div>
                    <div class="flex">
                        <span id="item_ukupnaCijena_Jabuka">1.00</span> € 
                        <div class="item-ukloni" id="item_ukloni_Jabuka">
                        Ukloni
                        <div>
                    </div>
                </div>
            </div>
        </div>
        
        <hr /> 
        <form> 
            <div> UKUPNO: <span id="ukupno"></span> € </div>
        </form>
        
    </div>     
</div>
```