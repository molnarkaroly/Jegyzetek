Oké, itt van egy részletes HTML magyarázat, a JavaScripteshez hasonló stílusban, Markdown formátumban, GitHub-ra optimalizálva.

```markdown
# Részletes HTML Jegyzetek Kezdőknek és Középhaladóknak

Ez a dokumentum célja, hogy átfogó képet adjon a HTML (HyperText Markup Language) alapjairól. A HTML a weboldalak alapvető szerkezeti nyelve. Minden kódrészlet magyarázattal és kommentekkel van ellátva a jobb érthetőség érdekében.

## 1. Bevezetés a HTML-be

### 1.1. Mi a HTML?
A HTML a **HyperText Markup Language** (Hiperszöveges Jelölőnyelv) rövidítése. Nem egy programozási nyelv (mint pl. a JavaScript), hanem egy **jelölőnyelv**. Arra szolgál, hogy **strukturálja a weboldalak tartalmát**. Meghatározza, hogy a különböző tartalmi elemek (szövegek, képek, linkek stb.) hogyan jelenjenek meg és milyen szerepet töltsenek be a dokumentumban.

A böngészők (pl. Chrome, Firefox, Safari) értelmezik a HTML kódot, és ennek alapján jelenítik meg a weboldalt a felhasználó számára.

### 1.2. HTML, CSS és JavaScript
Ez a három technológia alkotja a modern webfejlesztés alapját:
-   **HTML:** A tartalom **szerkezete** és jelentése (pl. ez egy címsor, ez egy bekezdés).
-   **CSS (Cascading Style Sheets):** A tartalom **megjelenése** és stílusa (pl. színek, betűtípusok, elrendezés).
-   **JavaScript (JS):** A weboldal **interaktivitása** és dinamikus viselkedése (pl. események kezelése, DOM manipuláció).

### 1.3. Egy Alapvető HTML Dokumentum Szerkezete
Minden HTML dokumentum egy alapvető szerkezettel rendelkezik:

```html
<!DOCTYPE html> <!-- Meghatározza a dokumentumtípust (HTML5 esetén ez a forma) -->
<html lang="hu"> <!-- A HTML dokumentum gyökereleme. A 'lang' attribútum a dokumentum nyelvét adja meg (itt magyar) -->

  <head>
    <!-- A <head> szekció meta-információkat tartalmaz a HTML dokumentumról,
         amelyek nem jelennek meg közvetlenül a böngészőablakban (kivéve a <title>). -->
    <meta charset="UTF-8"> <!-- Karakterkódolás beállítása (UTF-8 ajánlott a legtöbb nyelvhez) -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> <!-- Reszponzivitáshoz fontos: a nézetablak szélességét az eszköz szélességéhez igazítja, és a kezdeti nagyítási szintet 1.0-ra állítja -->
    <meta name="description" content="Ez egy példa HTML oldal leírása."> <!-- Keresőmotorok számára hasznos leírás -->
    <meta name="keywords" content="html, webfejlesztés, példa"> <!-- Kulcsszavak (kevésbé releváns ma már a SEO-ban) -->
    <title>Az Én Első Weboldalam</title> <!-- A böngésző fülén/címsorában megjelenő cím -->
    <link rel="stylesheet" href="stilusok.css"> <!-- Külső CSS fájl csatolása -->
    <!-- <style>
      /* Itt lehetne belső (embedded) CSS stílusokat is definiálni */
      /* body { background-color: lightblue; } */
    </style> -->
  </head>

  <body>
    <!-- A <body> szekció tartalmazza a weboldal látható tartalmát. -->
    <h1>Üdvözöllek a Weboldalamon!</h1> <!-- Főcímsor (általában egy <h1> van egy oldalon) -->
    <p>Ez az első bekezdésem ezen a csodálatos HTML oldalon.</p>

    <!-- <script src="app.js"></script> --> <!-- Külső JavaScript fájl csatolása (gyakran a <body> végére teszik a gyorsabb oldalmegjelenítés érdekében) -->
  </body>

</html>
```

## 2. HTML Elemek (Tags)

A HTML elemek a HTML nyelv építőkövei. Általában egy **nyitó tag**-ből (`<tagnev>`), **tartalom**-ból és egy **záró tag**-ből (`</tagnev>`) állnak.
Pl.: `<p>Ez egy bekezdés.</p>`

Néhány elem **üres** vagy **önzáró**, ami azt jelenti, hogy nincs tartalmuk és nincs szükségük külön záró tag-re. Ilyenkor a nyitó tag végén egy perjel (`/`) használható (HTML5-ben opcionális, de XHTML-ben kötelező volt).
Pl.: `<img src="kep.jpg" alt="Leíró szöveg">` vagy `<br>` (sortörés).

**Fontos:** A HTML tag-ek nevei általában kisbetűsek, bár a HTML maga nem kis- és nagybetű érzékeny a tag nevekre, a konvenció a kisbetűs írásmód.

### 2.1. A `<head>` Szekció Gyakori Elemei
Már láttunk néhányat az alap dokumentum szerkezetében:
-   `<title>`: Az oldal címe.
-   `<meta>`: Metaadatok (pl. karakterkódolás, viewport beállítások, leírás, kulcsszavak).
    -   `charset`: Karakterkódolás (pl. `UTF-8`).
    -   `name="viewport"`: Reszponzív tervezéshez.
    -   `name="description"`: Oldal leírása.
    -   `name="author"`: Szerző.
-   `<link>`: Külső erőforrások csatolása, leggyakrabban CSS fájlok (`rel="stylesheet"`).
    -   `rel`: A csatolt dokumentum és az aktuális dokumentum közötti kapcsolat típusa.
    -   `href`: Az erőforrás URL-je.
-   `<style>`: Beágyazott CSS stílusok definiálása.
-   `<script>`: JavaScript kód beágyazása vagy külső JavaScript fájl csatolása.

### 2.2. A `<body>` Szekció Gyakori Elemei

#### Szövegformázás
-   `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>`: Címsorok. A `<h1>` a legfontosabb, a `<h6>` a legkevésbé. Hierarchikusan érdemes használni őket.
    ```html
    <h1>Ez egy H1 címsor</h1>
    <h2>Ez egy H2 alcím</h2>
    <p>Ez egy bekezdés a H2 alcím alatt.</p>
    <h3>Ez egy H3 alcím</h3>
    ```
-   `<p>`: Bekezdés (Paragraph).
    ```html
    <p>Ez egy szöveges bekezdés. A böngésző általában térközt hagy a bekezdések között.</p>
    <p>Ez egy másik bekezdés.</p>
    ```
-   `<a>`: Horgony (Anchor), linkek létrehozására szolgál.
    -   `href` attribútum: A link cél URL-je.
    -   `target="_blank"`: Új böngészőfülön nyitja meg a linket.
    -   `title`: Extra információ a linkről (tooltipként jelenik meg).
    ```html
    <a href="https://www.example.com">Látogass el az Example.com-ra!</a>
    <br> <!-- Sortörés -->
    <a href="masik_oldal.html" target="_blank" title="Ez egy másik oldalra mutat">Másik oldal új fülön</a>
    <a href="#egy-resz-az-oldalon">Ugrás egy oldalrészhez (ID alapján)</a>
    ```
-   `<span>`: Általános inline tároló, önmagában nincs vizuális hatása, CSS-sel vagy JavaScripttel formázható/manipulálható egy szövegrészlet.
-   `<strong>` vagy `<b>`: Erős kiemelés / Félkövér szöveg. A `<strong>` szemantikailag fontosabb.
-   `<em>` vagy `<i>`: Hangsúlyos kiemelés / Dőlt szöveg. Az `<em>` szemantikailag fontosabb.
-   `<u>`: Aláhúzott szöveg (ritkán használatos, mert könnyen összetéveszthető linkekkel).
-   `<br>`: Sortörés (Line Break).
-   `<hr>`: Vízszintes elválasztó vonal (Horizontal Rule).
-   `<blockquote>`: Hosszabb idézetblokk.
    -   `cite` attribútum: Az idézet forrásának URL-je.
-   `<q>`: Rövid, inline idézet.
-   `<pre>`: Előformázott szöveg. Megőrzi a szóközöket és sortöréseket, általában monospace betűtípussal jelenik meg (kódblokkokhoz hasznos).
-   `<code>`: Kódrészlet inline megjelenítésére.
    ```html
    <p>Használd a <strong>fontos</strong> szót a kiemeléshez, és az <em>említésre méltó</em> szót a hangsúlyozáshoz.</p>
    <p>A HTML `<code>&lt;p&gt;</code>` tag egy bekezdést definiál.</p>
    <pre>
function hello() {
  console.log("Hello, world!");
}
    </pre>
    </blockquote>
    <p>Ahogy Shakespeare mondta: <q>Lenni vagy nem lenni, az itt a kérdés.</q></p>
    ```

#### Képek
-   `<img>`: Kép beillesztése. Önzáró elem.
    -   `src` (source) attribútum: A képfájl elérési útja (URL).
    -   `alt` (alternative text) attribútum: Alternatív szöveg a képhez. **Nagyon fontos** a képernyőolvasók (akadálymentesség) és a keresőmotorok (SEO) számára, valamint akkor jelenik meg, ha a kép nem töltődik be.
    -   `width` és `height`: Kép szélessége és magassága pixelben (CSS-ben jobb kezelni a reszponzivitás miatt).
    ```html
    <img src="kepek/logo.png" alt="Cégünk logója" width="150" height="50">
    <img src="https://via.placeholder.com/300x200" alt="Egy 300x200-as placeholder kép">
    ```

#### Listák
-   `<ul>`: Rendezettlen lista (Unordered List - általában pontozott).
-   `<ol>`: Rendezett lista (Ordered List - általában sorszámozott).
    -   `type` attribútum: Számozás típusa (`1`, `A`, `a`, `I`, `i`).
    -   `start` attribútum: Kezdő sorszám.
-   `<li>`: Listaelem (List Item) - `<ul>` és `<ol>` elemeken belül használatos.
-   `<dl>`: Definíciós lista (Definition List).
-   `<dt>`: Definíciós lista címe (Definition Term).
-   `<dd>`: Definíciós lista leírása (Definition Description).
    ```html
    <h2>Kedvenc Gyümölcseim (Rendezetlen)</h2>
    <ul>
      <li>Alma</li>
      <li>Banán</li>
      <li>Cseresznye</li>
    </ul>

    <h2>Teendők (Rendezett)</h2>
    <ol type="A" start="3"> <!-- C-vel kezdődik -->
      <li>Bevásárlás</li>
      <li>Edzés</li>
      <li>HTML tanulás</li>
    </ol>

    <h2>Szakkifejezések</h2>
    <dl>
      <dt>HTML</dt>
      <dd>HyperText Markup Language, a weboldalak szerkezeti nyelve.</dd>
      <dt>CSS</dt>
      <dd>Cascading Style Sheets, a weboldalak stílusának leírására szolgál.</dd>
    </dl>
    ```

#### Táblázatok
-   `<table>`: Táblázat definiálása.
-   `<caption>`: Táblázat felirata.
-   `<thead>`: Táblázat fejléc csoportja.
-   `<tbody>`: Táblázat törzs csoportja.
-   `<tfoot>`: Táblázat lábléc csoportja.
-   `<tr>`: Táblázat sor (Table Row).
-   `<th>`: Táblázat fejléc cella (Table Header cell). Általában félkövér és középre igazított.
    -   `scope` attribútum (`col` vagy `row`): Meghatározza, hogy a fejléc cella mely oszlopokra vagy sorokra vonatkozik (akadálymentesség).
-   `<td>`: Táblázat adat cella (Table Data cell).
    -   `colspan`: Cella kiterjesztése több oszlopra.
    -   `rowspan`: Cella kiterjesztése több sorra.
    ```html
    <table border="1"> <!-- A 'border' attribútum régebbi, CSS-sel jobb megoldani -->
      <caption>Havi Kiadások</caption>
      <thead>
        <tr>
          <th scope="col">Tétel</th>
          <th scope="col">Összeg (Ft)</th>
          <th scope="col">Kategória</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Lakbér</td>
          <td>150,000</td>
          <td>Lakhatás</td>
        </tr>
        <tr>
          <td>Élelmiszer</td>
          <td>80,000</td>
          <td>Élelmiszer</td>
        </tr>
        <tr>
          <td colspan="2">Összesen a két tétel:</td>
          <td>230,000</td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td colspan="3">Megjegyzés: Az összegek becsültek.</td>
        </tr>
      </tfoot>
    </table>
    ```

#### Űrlapok (Forms)
Űrlapok adatgyűjtésre szolgálnak a felhasználótól.
-   `<form>`: Űrlap definiálása.
    -   `action` attribútum: Az URL, ahová az űrlap adatai küldésre kerülnek feldolgozásra (pl. egy szerveroldali szkript).
    -   `method` attribútum: A HTTP metódus az adatok küldéséhez (`GET` vagy `POST`).
        -   `GET`: Az adatokat az URL-hez fűzi (látható, korlátozott méret). Keresésekhez, egyszerű adatlekérésekhez jó.
        -   `POST`: Az adatokat a HTTP kérés törzsében küldi (nem látható, nagyobb adatmennyiség is mehet). Érzékeny adatok, fájl feltöltés esetén ez használatos.
-   `<input>`: Különböző típusú beviteli mezők. Önzáró elem.
    -   `type` attribútum: A beviteli mező típusa. Gyakori típusok:
        -   `text`: Egysoros szövegbevitel.
        -   `password`: Jelszóbevitel (a karakterek elfedve jelennek meg).
        -   `email`: E-mail cím formátumú bevitel.
        -   `number`: Számbevitel (léptetőkkel).
        -   `date`: Dátumválasztó.
        -   `checkbox`: Jelölőnégyzet (több is kiválasztható egy csoportból).
        -   `radio`: Rádiógomb (egy csoportból csak egy választható ki - azonos `name` attribútummal kell rendelkezniük).
        -   `file`: Fájl kiválasztása feltöltéshez.
        -   `submit`: Elküldő gomb (beküldi az űrlapot).
        -   `reset`: Alaphelyzetbe állító gomb.
        -   `button`: Általános gomb (JavaScripttel vezérelhető).
        -   `hidden`: Rejtett beviteli mező (pl. technikai adatok küldéséhez).
    -   `name` attribútum: A beviteli mező neve, ez alapján azonosítja a szerver az adatot. **Nagyon fontos!**
    -   `id` attribútum: Egyedi azonosító az oldalon belül (pl. `<label>` csatolásához, CSS/JS manipulációhoz).
    -   `value` attribútum: A mező alapértelmezett értéke, vagy a checkbox/radio gomb értéke, ami elküldésre kerül.
    -   `placeholder`: Segítő szöveg, ami a mezőben jelenik meg, amíg a felhasználó nem ír bele semmit.
    -   `required`: Kötelezővé teszi a mező kitöltését.
    -   `checked`: Jelölőnégyzeteknél és rádiógomboknál előre kiválasztott állapotot jelez.
    -   `disabled`: Letiltja a mezőt.
-   `<label>`: Címke egy űrlapvezérlőhöz. Javítja az akadálymentességet.
    -   `for` attribútum: Az `input` elem `id`-jére hivatkozik, összekapcsolva a címkét a mezővel.
-   `<textarea>`: Többsoros szövegbeviteli mező.
    -   `rows` és `cols`: Sorok és oszlopok száma (méret).
-   `<select>`: Legördülő lista.
    -   `<option>`: Egy választható opció a `<select>` listában.
        -   `value`: Az opcióhoz tartozó érték, ami elküldésre kerül.
        -   `selected`: Előre kiválasztott opció.
    -   `<optgroup>`: Opciók csoportosítása a `<select>` listában.
        -   `label`: A csoport neve.
-   `<button>`: Gomb elem. Lehet `submit`, `reset` vagy `button` típusú. Rugalmasabb, mint az `<input type="button">`, mert tartalmazhat HTML-t.
-   `<fieldset>`: Űrlapvezérlők csoportosítása.
-   `<legend>`: Cím a `<fieldset>` számára.

    ```html
    <form action="/feldolgoz.php" method="POST">
      <fieldset>
        <legend>Személyes Adatok</legend>
        <div>
          <label for="nev">Név:</label>
          <input type="text" id="nev" name="felhasznalo_neve" placeholder="Pl. Gipsz Jakab" required>
        </div>
        <div>
          <label for="email">E-mail cím:</label>
          <input type="email" id="email" name="email_cim" required>
        </div>
        <div>
          <label for="jelszo">Jelszó:</label>
          <input type="password" id="jelszo" name="jelszo">
        </div>
      </fieldset>

      <fieldset>
        <legend>Érdeklődési Kör</legend>
        <p>Válassz egyet:</p>
        <div>
          <input type="radio" id="opcio1" name="erdeklodes" value="technologia" checked>
          <label for="opcio1">Technológia</label>
        </div>
        <div>
          <input type="radio" id="opcio2" name="erdeklodes" value="muveszet">
          <label for="opcio2">Művészet</label>
        </div>
        <p>Válassz többet is:</p>
        <div>
          <input type="checkbox" id="hobbi1" name="hobbi" value="olvasas">
          <label for="hobbi1">Olvasás</label>
        </div>
        <div>
          <input type="checkbox" id="hobbi2" name="hobbi" value="sport">
          <label for="hobbi2">Sport</label>
        </div>
      </fieldset>

      <div>
        <label for="orszag">Ország:</label>
        <select id="orszag" name="orszag">
          <optgroup label="Európa">
            <option value="hu" selected>Magyarország</option>
            <option value="de">Németország</option>
          </optgroup>
          <optgroup label="Amerika">
            <option value="us">USA</option>
            <option value="ca">Kanada</option>
          </optgroup>
        </select>
      </div>

      <div>
        <label for="uzenet">Üzenet:</label>
        <textarea id="uzenet" name="uzenet_szovege" rows="5" cols="30" placeholder="Írja ide az üzenetét..."></textarea>
      </div>
      
      <div>
        <label for="cv">Önéletrajz feltöltése:</label>
        <input type="file" id="cv" name="oneletrajz">
      </div>

      <div>
        <button type="submit">Űrlap Elküldése</button>
        <button type="reset">Űrlap Törlése</button>
        <input type="button" value="Egyedi Gomb" onclick="alert('Gomb megnyomva!')">
      </div>
    </form>
    ```

#### Szemantikus HTML5 Elemek
Ezek az elemek a tartalom jelentését (szemantikáját) írják le, segítve a keresőmotorokat, képernyőolvasókat és fejlesztőket a weboldal szerkezetének jobb megértésében.
-   `<header>`: Az oldal vagy egy szekció fejlécét tartalmazza (pl. logó, navigáció, cím).
-   `<nav>`: Navigációs linkek csoportja.
-   `<main>`: Az oldal fő, központi tartalma. Oldalanként csak egy `<main>` elemnek kellene lennie.
-   `<article>`: Önálló, önmagában értelmezhető tartalmi egység (pl. blogbejegyzés, fórum hozzászólás, hír).
-   `<section>`: Egy tematikus csoportosítás a tartalomban, általában címsorral.
-   `<aside>`: Oldalsáv, kevésbé fontos, kiegészítő tartalom (pl. kapcsolódó linkek, hirdetések).
-   `<footer>`: Az oldal vagy egy szekció láblécét tartalmazza (pl. szerzői jogi információk, kapcsolati adatok).
-   `<figure>` és `<figcaption>`: Képek, diagramok, kódblokkok stb. csoportosítása egy felirattal.
-   `<time>`: Dátum és/vagy idő megjelölésére.
    -   `datetime` attribútum: Géppel olvasható formátumban adja meg az időt/dátumot.

    ```html
    <body>
      <header>
        <img src="logo.png" alt="Logó">
        <nav>
          <ul>
            <li><a href="/">Főoldal</a></li>
            <li><a href="/rolunk">Rólunk</a></li>
            <li><a href="/kapcsolat">Kapcsolat</a></li>
          </ul>
        </nav>
      </header>

      <main>
        <article>
          <h2>Első Blogbejegyzésem</h2>
          <p>Ez itt a bejegyzés tartalma...</p>
          <figure>
            <img src="blog_kep.jpg" alt="Kép a bejegyzéshez">
            <figcaption>Fontos kép a cikkhez.</figcaption>
          </figure>
          <footer>
            <p>Publikálva: <time datetime="2023-10-27">2023. október 27.</time></p>
          </footer>
        </article>

        <section>
          <h2>Kapcsolódó Cikkek</h2>
          <!-- ... -->
        </section>
      </main>

      <aside>
        <h3>Hirdetések</h3>
        <!-- ... -->
      </aside>

      <footer>
        <p>&copy; 2023 Minden jog fenntartva. Készítette: Én.</p>
      </footer>
    </body>
    ```

#### Multimédia
-   `<audio>`: Hangfájlok beágyazása.
    -   `src`: Hangfájl URL-je.
    -   `controls`: Alapértelmezett vezérlők megjelenítése (lejátszás, hangerő stb.).
    -   `autoplay`: Automatikus lejátszás (böngészők gyakran korlátozzák).
    -   `loop`: Ismételt lejátszás.
    -   `<source>` elem: Több hangformátum megadása a böngészőkompatibilitás érdekében.
-   `<video>`: Videófájlok beágyazása.
    -   Attribútumai hasonlóak az `<audio>`-hoz (`src`, `controls`, `autoplay`, `loop`, `width`, `height`, `poster` - kezdőkép).
    -   `<source>` elem: Több videóformátum megadása.
    -   `<track>` elem: Feliratok, képaláírások hozzáadása (`.vtt` formátumban).

    ```html
    <h2>Hang Példa</h2>
    <audio controls>
      <source src="zene.mp3" type="audio/mpeg">
      <source src="zene.ogg" type="audio/ogg">
      A böngésződ nem támogatja az audio elemet.
    </audio>

    <h2>Videó Példa</h2>
    <video width="640" height="360" controls poster="video_kezdokep.jpg">
      <source src="film.mp4" type="video/mp4">
      <source src="film.webm" type="video/webm">
      <track label="Magyar" kind="subtitles" srclang="hu" src="felirat_hu.vtt" default>
      A böngésződ nem támogatja a videó elemet.
    </video>
    ```

#### Beágyazott Tartalom
-   `<iframe>`: Egy másik HTML dokumentum beágyazása az aktuális oldalba (pl. YouTube videó, Google Maps térkép).
    -   `src`: A beágyazandó oldal URL-je.
    -   `width`, `height`: A keret mérete.
    -   `frameborder`: Keret vastagsága (általában `0`).
    -   `allowfullscreen`: Teljes képernyős mód engedélyezése.
    -   `sandbox`: Biztonsági korlátozások beállítása a beágyazott tartalomra.

    ```html
    <h2>Google Térkép Beágyazva</h2>
    <iframe
      src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2695.1000000000004!2d19.040235!3d47.497912!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zSMWrdXRha3MgaGlkZSBhdCB0aGUgQ2hhaW4gQnJpZGdl!5e0!3m2!1shu!2shu!4v1618762113051!5m2!1shu!2shu"
      width="600"
      height="450"
      style="border:0;"
      allowfullscreen=""
      loading="lazy"
      title="Példa térkép">
    </iframe>
    ```

## 3. HTML Attribútumok

Az attribútumok extra információkat adnak a HTML elemekhez. Mindig a nyitó tag-ben helyezkednek el, és általában `név="érték"` párokként jelennek meg.

### 3.1. Globális Attribútumok
Ezek bármelyik HTML elemen használhatók:
-   `id`: Egyedi azonosító az elemen (oldalanként csak egyszer szerepelhet ugyanaz az ID). CSS szelektorokhoz, JavaScript DOM manipulációhoz, és oldal içi linkek (`<a href="#id-ertek">`) célpontjaként használatos.
-   `class`: Egy vagy több osztálynév (szóközzel elválasztva). CSS szelektorokhoz és JavaScript DOM manipulációhoz használatos. Egy osztálynevet több elemen is használhatunk.
-   `style`: Inline CSS stílusok definiálása (általában kerülendő, jobb külső vagy beágyazott CSS-t használni).
-   `title`: Extra információ az elemről (tooltipként jelenik meg egérmutató fölé mozgatásakor).
-   `lang`: Az elem tartalmának nyelve.
-   `tabindex`: Meghatározza az elem tabulálási sorrendjét.
-   `hidden`: Elrejti az elemet.
-   `data-*`: Egyéni adatattribútumok tárolására (pl. `data-felhasznalo-id="123"`). JavaScripttel könnyen elérhetők.

```html
<p id="bevezeto" class="fontos kiemelt-szoveg" title="Ez egy fontos bevezető bekezdés." data-version="1.2">
  Ez egy bekezdés globális attribútumokkal.
</p>
```

## 4. HTML Kommentek

A kommentek nem jelennek meg a böngészőben, de segítenek a fejlesztőknek megérteni a kódot vagy ideiglenesen kikommentelni részeket.
Szintaxis: `<!-- Ez itt egy komment -->`

```html
<!-- Ez egy egysoros komment -->

<!--
  Ez egy
  többsoros
  komment.
-->

<!-- <p>Ez a bekezdés ki van kommentelve, így nem jelenik meg.</p> -->
```

## 5. Blokk vs. Inline Elemek

A HTML elemek alapértelmezés szerint vagy **blokk** vagy **inline** szintűek.
-   **Blokk szintű elemek** (`<div>`, `<p>`, `<h1>`-`<h6>`, `<ul>`, `<li>`, `<table>`, `<form>` stb.):
    -   Mindig új sorban kezdődnek.
    -   A rendelkezésre álló teljes szélességet elfoglalják (ha nincs másképp CSS-sel beállítva).
    -   Tartalmazhatnak más blokk és inline elemeket.
    -   Megadható nekik `width`, `height`, `margin` (felső/alsó is), `padding`.
-   **Inline (soron belüli) elemek** (`<a>`, `<span>`, `<img>`, `<strong>`, `<em>`, `<input>`, `<code>` stb.):
    -   Nem kezdenek új sort.
    -   Csak annyi helyet foglalnak el, amennyi a tartalmukhoz szükséges.
    -   Általában csak más inline elemeket vagy szöveges tartalmat tartalmazhatnak.
    -   `width` és `height` nem alkalmazható rájuk közvetlenül. `margin` (csak bal/jobb) és `padding` korlátozottan működik.

A `display` CSS tulajdonsággal megváltoztatható egy elem alapértelmezett viselkedése (pl. `display: block;`, `display: inline;`, `display: inline-block;`, `display: flex;`, `display: grid;`).

## 6. HTML Entitások

Bizonyos karakterek speciális jelentéssel bírnak a HTML-ben (pl. `<` és `>`). Ha ezeket a karaktereket szövegként szeretnénk megjeleníteni, HTML entitásokat kell használnunk.

Gyakori entitások:
-   `&lt;`: `<` (less than)
-   `&gt;`: `>` (greater than)
-   `&amp;`: `&` (ampersand)
-   `&quot;`: `"` (double quote)
-   `&apos;`: `'` (single quote - nem mindig szükséges, de XML-ben igen)
-   `&nbsp;`: nem törhető szóköz (non-breaking space)
-   `&copy;`: `©` (copyright)
-   `&reg;`: `®` (registered trademark)
-   `&euro;`: `€` (euro)

```html
<p>A &lt;p&gt; tag egy bekezdést jelent a HTML-ben. Ez &amp; az &copy; fontos.</p>
<!-- Kimenet: A <p> tag egy bekezdést jelent a HTML-ben. Ez & az © fontos. -->
```

## 7. HTML Validáció

Fontos, hogy a HTML kódunk szintaktikailag helyes legyen. A valid HTML biztosítja a jobb böngészőkompatibilitást és csökkenti a váratlan megjelenítési hibák esélyét.
Használhatunk online validátorokat, mint pl. a W3C Markup Validation Service (validator.w3.org).

## 8. További Tanulnivalók és Jó Gyakorlatok

-   **Akadálymentesség (Accessibility - a11y):** Tervezz úgy weboldalakat, hogy mindenki számára használhatók legyenek, beleértve a fogyatékkal élőket is (pl. helyes `alt` szövegek, `<label>`-ek használata, billentyűzet-navigáció támogatása, ARIA attribútumok).
-   **SEO (Search Engine Optimization - Keresőoptimalizálás):** Szemantikus HTML, releváns `<title>` és `<meta description>`, jó címsorstruktúra használata segít a keresőmotoroknak megérteni és rangsorolni az oldaladat.
-   **Reszponzív Web Design:** Olyan weboldalak készítése, amelyek jól néznek ki és jól használhatók minden eszközön (asztali gép, tablet, mobil). Ez főleg CSS feladat, de a HTML szerkezet is hatással van rá (pl. `viewport` meta tag).
-   **CSS alapos ismerete:** A HTML a szerkezet, de a megjelenést a CSS adja.
-   **JavaScript alapos ismerete:** Az interaktivitáshoz és dinamikus tartalomhoz.
-   **HTML5 API-k:** Geolocation, Web Storage, Canvas, SVG stb.

Ez a jegyzet egy szilárd alapot nyújt a HTML világában való elinduláshoz. A legjobb módja a tanulásnak a gyakorlás: készíts saját weboldalakat, kísérletezz az elemekkel és attribútumokkal! Sok sikert!
```

**Hogyan használd GitHub-on (ismétlés):**

1.  Másold ki a fenti teljes kódrészletet (a ```markdown és a záró ``` jelekkel együtt).
2.  Menj a GitHub-on arra a helyre, ahova be szeretnéd illeszteni (pl. egy `README.md` fájl szerkesztési nézetébe, egy Issue kommentbe, egy Wiki oldal szerkesztőjébe).
3.  Illeszd be a másolt szöveget.
4.  GitHub automatikusan feldolgozza a Markdown-t, és szépen formázva, szintaxiskiemeléssel jeleníti meg a HTML kódrészleteket is.

Remélem, ez a részletes HTML magyarázat is hasznos lesz!