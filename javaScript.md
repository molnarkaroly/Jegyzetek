Rendben, itt van egy még részletesebb JavaScript jegyzet, tele magyarázatokkal, kommentekkel, és logikusan csoportosítva, hogy a lehető leghasznosabb legyen.

```markdown
# Részletes JavaScript Jegyzetek Kezdőknek és Középhaladóknak

Ez a dokumentum célja, hogy átfogó képet adjon a JavaScript alapjairól és néhány haladóbb koncepciójáról. Minden kódrészlet magyarázattal és kommentekkel van ellátva a jobb érthetőség érdekében.

## 1. Bevezetés a JavaScriptbe

### 1.1. Mi a JavaScript?
A JavaScript (röviden JS) egy **magas szintű, dinamikus, interpretált (vagy just-in-time fordított) programozási nyelv**. Eredetileg a webböngészők kliensoldali szkriptnyelveként lett kifejlesztve, hogy interaktívvá tegye a weboldalakat. Mára azonban a Node.js futtatókörnyezetnek köszönhetően szerveroldalon, mobilalkalmazásokban (pl. React Native, Ionic), asztali alkalmazásokban (pl. Electron) és még sok más területen is használják.

### 1.2. Első JavaScript Kód
A `console.log()` egy beépített függvény, amellyel üzeneteket írhatunk ki a böngésző fejlesztői konzoljára vagy a Node.js termináljára. Ez rendkívül hasznos hibakereséshez és értékek ellenőrzéséhez.

```javascript
// Ez egy egysoros komment. A fordító/értelmező figyelmen kívül hagyja.
// A console.log() segítségével kiírunk egy üzenetet a konzolra.
console.log("Helló, JavaScript Világ!");

/*
Ez egy többsoros komment.
Több sort is felölelhet,
és szintén figyelmen kívül hagyja az értelmező.
*/
let uzenet = "Tanuljunk JavaScriptet!";
console.log(uzenet); // Kiírja a 'uzenet' változó tartalmát.
```

### 1.3. JavaScript Hozzáadása HTML-hez
JavaScript kód két fő módon ágyazható be egy HTML oldalba:

1.  **Beágyazott (Inline) szkript:** Közvetlenül a `<script>` tagek közé írva.
    ```html
    <!-- <script>
      alert("Helló a beágyazott szkriptből!");
    </script> -->
    ```
2.  **Külső szkriptfájl:** Egy `.js` kiterjesztésű fájlra hivatkozva. Ez a preferált módszer a kód szervezettsége és újrafelhasználhatósága miatt.
    ```html
    <!-- <script src="sajatkodom.js"></script> -->
    ```
    *Megjegyzés: A `defer` és `async` attribútumok befolyásolják a szkript betöltésének és végrehajtásának módját.*

## 2. Változók és Adattárolás

A változók "nevesített tárolók" az adatok számára.

### 2.1. Változók Deklarálása
JavaScriptben három kulcsszóval deklarálhatunk változókat:

-   `var`: Régebbi, függvény hatókörű (function scope) vagy globális hatókörű. Használata modern JavaScriptben általában kerülendő a `let` és `const` javára, a "hoisting" és a hatókör-kezelési furcsaságai miatt.
-   `let`: Blokk hatókörű (block scope - `{}`). Értéke újra hozzárendelhető.
-   `const`: Blokk hatókörű. Értéke a deklaráció után nem változtatható meg (konstans). Fontos: Objektumok és tömbök esetén maga a referencia konstans, de a belső tartalmuk (tulajdonságok, elemek) módosíthatók.

```javascript
// var használata (régebbi stílus, kerülendő)
var regiValtozo = "Én egy var vagyok.";
regiValtozo = "Új érték a var-nak."; // Működik

// let használata (modern, preferált, ha az érték változhat)
let kor = 30;
console.log("Eredeti kor:", kor); // Eredeti kor: 30
kor = 31; // Új értéket adhatunk neki
console.log("Új kor:", kor); // Új kor: 31

// const használata (modern, preferált, ha az érték nem változik)
const NEV = "Gábor";
console.log("Név:", NEV); // Név: Gábor
// NEV = "Péter"; // Hiba! TypeError: Assignment to constant variable.

const PI = 3.14159;
// PI = 3.14; // Ez is hibát okozna.

// Fontos megjegyzés const objektumokhoz és tömbökhöz:
const FELHASZNALO = {
  nev: "Anna",
  eletkor: 25
};
console.log("Felhasználó neve (eredeti):", FELHASZNALO.nev); // Anna
FELHASZNALO.eletkor = 26; // EZ MŰKÖDIK! Az objektum belső tulajdonságát módosítjuk.
console.log("Felhasználó életkora (módosított):", FELHASZNALO.eletkor); // 26
// FELHASZNALO = { ujTulajdonsag: "valami" }; // EZ HIBÁT OKOZNA! Új objektumot próbálunk hozzárendelni.

const SZAMOK = [1, 2, 3];
SZAMOK.push(4); // EZ MŰKÖDIK! A tömb tartalmát módosítjuk.
console.log("Számok:", SZAMOK); // [1, 2, 3, 4]
// SZAMOK = [5, 6]; // EZ HIBÁT OKOZNA! Új tömböt próbálunk hozzárendelni.
```

### 2.2. Elnevezési Konvenciók
-   Változónevek betűvel, aláhúzással (`_`) vagy dollárjellel (`$`) kezdődhetnek.
-   Kis- és nagybetű érzékenyek (`nev` és `Nev` két különböző változó).
-   Gyakori konvenció a `camelCase` (pl. `felhasznaloNeve`).
-   Konstansok esetén gyakori a `UPPER_SNAKE_CASE` (pl. `MAX_ERTEK`).

## 3. Adattípusok

A JavaScript dinamikusan típusos nyelv, ami azt jelenti, hogy a változók típusa futás közben dől el, és nem kell expliciten megadni a deklarációnál.

### 3.1. Primitív Adattípusok
Ezek megváltoztathatatlan (immutable) értékek.

1.  **String**: Szöveges adatok. Idézőjelek (`"`), aposztrófok (`'`) vagy backtick-ek (`` ` `` - template literals) közé zárva.
    ```javascript
    let keresztNev = "John";
    let vezetekNev = 'Doe';
    let teljesNev = `Teljes név: ${keresztNev} ${vezetekNev}`; // Template literal, változó beillesztéssel
    console.log(teljesNev); // Teljes név: John Doe
    ```
2.  **Number**: Számok, beleértve az egészeket és a lebegőpontos számokat.
    ```javascript
    let egeszSzam = 100;
    let lebegopontosSzam = 3.14;
    let specialisSzam1 = Infinity; // Végtelen
    let specialisSzam2 = -Infinity;
    let specialisSzam3 = NaN; // Not a Number (pl. 'szöveg' / 2 eredménye)
    console.log(0 / 0); // NaN
    console.log(typeof NaN); // "number" (furcsaság, de így van)
    ```
3.  **Boolean**: Logikai érték, ami `true` (igaz) vagy `false` (hamis) lehet.
    ```javascript
    let aktiv = true;
    let befejezett = false;
    console.log(10 > 5); // true
    ```
4.  **Null**: Egyetlen értéke van: `null`. Szándékosan "semmi" vagy "üres" értéket reprezentál.
    ```javascript
    let auto = null; // Az 'auto' változó expliciten üres.
    console.log(auto); // null
    console.log(typeof auto); // "object" (ez egy ismert JavaScript "bug", de a visszafelé kompatibilitás miatt nem javítják)
    ```
5.  **Undefined**: Egy változó, amelynek deklaráltak, de még nem adtak értéket, automatikusan `undefined` lesz. Illetve egy függvény, ami nem ad vissza explicit értéket, `undefined`-et ad vissza.
    ```javascript
    let megNemDefinialt;
    console.log(megNemDefinialt); // undefined
    console.log(typeof megNemDefinialt); // "undefined"
    ```
6.  **Symbol (ES6+)**: Egyedi és megváltoztathatatlan primitív érték, amit gyakran objektumtulajdonságok egyedi kulcsaként használnak.
    ```javascript
    const idSymbol = Symbol('egyediAzonosito');
    const masikIdSymbol = Symbol('egyediAzonosito');
    console.log(idSymbol === masikIdSymbol); // false, mert minden Symbol egyedi
    let obj = {};
    obj[idSymbol] = "Ez egy szimbólummal indexelt érték";
    console.log(obj[idSymbol]);
    ```
7.  **BigInt (ES2020+)**: Nagyon nagy egész számok ábrázolására szolgál, amelyek meghaladják a `Number` típus biztonságos egész tartományát. Egy `n` utótaggal jelöljük.
    ```javascript
    const nagySzam = 1234567890123456789012345678901234567890n;
    const masikNagySzam = BigInt(98765432109876543210);
    console.log(nagySzam + masikNagySzam);
    console.log(typeof nagySzam); // "bigint"
    ```

### 3.2. Komplex Adattípus
1.  **Object**: Kulcs-érték párok gyűjteménye. A JavaScriptben szinte minden objektum (a tömbök és függvények is speciális objektumok).
    ```javascript
    let szemely = {
      nev: "Kovács Béla", // 'nev' a kulcs (property), "Kovács Béla" az érték (value)
      eletkor: 42,
      foglalkozas: "Mérnök",
      udvozlet: function() { // metódus (függvény, ami egy objektum tulajdonsága)
        console.log("Helló, a nevem " + this.nev);
      }
    };
    console.log(szemely.nev); // "Kovács Béla" (pontos jelölés)
    console.log(szemely["eletkor"]); // 42 (szögletes zárójeles jelölés, hasznos dinamikus kulcsok esetén)
    szemely.udvozlet(); // "Helló, a nevem Kovács Béla"
    ```

### 3.3. `typeof` Operátor
Az adattípus ellenőrzésére használható.
```javascript
console.log(typeof "szöveg");      // "string"
console.log(typeof 10);            // "number"
console.log(typeof true);          // "boolean"
console.log(typeof undefined);     // "undefined"
console.log(typeof null);          // "object" (a már említett furcsaság)
console.log(typeof {a: 1});        // "object"
console.log(typeof [1, 2, 3]);     // "object" (a tömbök is objektumok)
console.log(typeof function(){});  // "function" (bár a függvények is objektumok, a typeof speciálisan kezeli őket)
console.log(typeof Symbol());      // "symbol"
console.log(typeof 100n);          // "bigint"
```

## 4. Operátorok

Az operátorok szimbólumok, amelyek műveleteket hajtanak végre értékeken (operandusokon).

### 4.1. Aritmetikai Operátorok
```javascript
let a = 10;
let b = 3;
console.log("Összeadás:", a + b);     // 13
console.log("Kivonás:", a - b);      // 7
console.log("Szorzás:", a * b);       // 30
console.log("Osztás:", a / b);        // 3.333...
console.log("Maradékos osztás (modulus):", a % b); // 1
console.log("Hatványozás (ES7+):", a ** b); // 1000 (10 a 3-on)

let szamlalo = 0;
szamlalo++; // Növelés eggyel (szamlalo = szamlalo + 1), postfix
console.log("Növelés után:", szamlalo); // 1
++szamlalo; // Növelés eggyel, prefix
console.log("Ismét növelés után:", szamlalo); // 2
szamlalo--; // Csökkentés eggyel (szamlalo = szamlalo - 1), postfix
console.log("Csökkentés után:", szamlalo); // 1
```

### 4.2. Értékadó Operátorok
```javascript
let x = 10;
x += 5; // x = x + 5;  -> x most 15
x -= 3; // x = x - 3;  -> x most 12
x *= 2; // x = x * 2;  -> x most 24
x /= 4; // x = x / 4;  -> x most 6
x %= 5; // x = x % 5;  -> x most 1
console.log("Értékadó operátorok után x:", x); // 1
```

### 4.3. Összehasonlító Operátorok
Eredményük mindig boolean (`true` vagy `false`).

```javascript
let ertek1 = 10;
let ertek2 = "10";
let ertek3 = 5;

console.log("== (laza egyenlőség):", ertek1 == ertek2);   // true (típuskonverziót végez) - **KERÜLENDŐ ÁLTALÁBAN**
console.log("=== (szigorú egyenlőség):", ertek1 === ertek2); // false (nem végez típuskonverziót, típust is ellenőriz) - **AJÁNLOTT**
console.log("=== (szigorú egyenlőség):", ertek1 === 10);    // true

console.log("!= (laza nem egyenlőség):", ertek1 != ertek2);  // false
console.log("!== (szigorú nem egyenlőség):", ertek1 !== ertek2); // true - **AJÁNLOTT**

console.log("> (nagyobb):", ertek1 > ertek3);            // true
console.log("< (kisebb):", ertek1 < ertek3);            // false
console.log(">= (nagyobb vagy egyenlő):", ertek1 >= 10);  // true
console.log("<= (kisebb vagy egyenlő):", ertek1 <= ertek3); // false
```

### 4.4. Logikai Operátorok
```javascript
let vanJogositvany = true;
let faradt = false;

// Logikai ÉS (&&): akkor true, ha mindkét operandus true
console.log("Vezethet (ÉS):", vanJogositvany && !faradt); // true

// Logikai VAGY (||): akkor true, ha legalább az egyik operandus true
let hetvege = true;
let napsutes = false;
console.log("Megyünk kirándulni (VAGY):", hetvege || napsutes); // true

// Logikai NEM (!): megfordítja a boolean értéket
console.log("Nem fáradt:", !faradt); // true
```
*Rövidzár kiértékelés (Short-circuit evaluation):*
*   `A && B`: Ha `A` hamis, `B` nem értékelődik ki.
*   `A || B`: Ha `A` igaz, `B` nem értékelődik ki.

### 4.5. Ternáris (Feltételes) Operátor
Egyetlen sorban írható `if-else` szerkezet.
`feltétel ? kifejezés_ha_igaz : kifejezés_ha_hamis`

```javascript
let eletkor = 17;
let statusz = (eletkor >= 18) ? "Felnőtt" : "Kiskorú";
console.log("Státusz:", statusz); // Kiskorú
```

## 5. Vezérlési Szerkezetek

Ezekkel irányíthatjuk a program futásának folyamatát.

### 5.1. Feltételes Utasítások

#### `if...else if...else`
```javascript
let ora = 14;

if (ora < 12) {
  console.log("Jó reggelt!");
} else if (ora < 18) {
  console.log("Jó napot!"); // Ez fog lefutni
} else {
  console.log("Jó estét!");
}
```

#### `switch`
Több lehetséges érték közül választ egy kódrészletet. Gyakran használják `if...else if...else` helyett, ha egyetlen változó több konkrét értékét vizsgáljuk.
```javascript
let napSorszama = new Date().getDay(); // Vasárnap = 0, Hétfő = 1, ...
let napNeve;

switch (napSorszama) {
  case 0:
    napNeve = "Vasárnap";
    break; // Fontos a break, különben a következő case is lefutna ("fall-through")
  case 1:
    napNeve = "Hétfő";
    break;
  case 2:
    napNeve = "Kedd";
    break;
  case 3:
    napNeve = "Szerda";
    break;
  case 4:
    napNeve = "Csütörtök";
    break;
  case 5:
    napNeve = "Péntek";
    break;
  case 6:
    napNeve = "Szombat";
    break;
  default: // Ha egyik case sem illeszkedik
    napNeve = "Ismeretlen nap";
}
console.log("Ma", napNeve, "van.");
```

### 5.2. Ciklusok (Loops)

Ismétlődő feladatok végrehajtására.

#### `for` ciklus
Akkor használjuk, ha tudjuk, hányszor szeretnénk ismételni.
`for (inicializálás; feltétel; léptetés)`
```javascript
console.log("For ciklus:");
for (let i = 0; i < 5; i++) { // i = 0, 1, 2, 3, 4
  console.log("Az i értéke:", i);
}
```

#### `while` ciklus
Akkor használjuk, ha a ciklus futásának száma egy feltételtől függ, és nem tudjuk előre, hányszor fog lefutni. A feltétel a ciklusmag előtt ellenőrződik.
```javascript
console.log("While ciklus:");
let szamlaloCiklus = 0;
while (szamlaloCiklus < 3) {
  console.log("Számláló (while):", szamlaloCiklus);
  szamlaloCiklus++;
}
```

#### `do...while` ciklus
Hasonló a `while`-hoz, de a ciklusmag legalább egyszer lefut, mert a feltétel a ciklusmag után ellenőrződik.
```javascript
console.log("Do...while ciklus:");
let k = 5;
do {
  console.log("k értéke (do...while):", k); // Ez lefut egyszer
  k++;
} while (k < 3); // A feltétel hamis (5 < 3), de a ciklusmag már lefutott
```

#### `for...in` ciklus
Objektumok tulajdonságain (kulcsain) iterál végig.
```javascript
console.log("For...in ciklus (objektum):");
const autoJellemzok = {
  marka: "Toyota",
  modell: "Corolla",
  evjarat: 2021
};
for (let kulcs in autoJellemzok) {
  console.log(`${kulcs}: ${autoJellemzok[kulcs]}`);
}
// Kimenet:
// marka: Toyota
// modell: Corolla
// evjarat: 2021

// Használható tömbök indexein is, de a for...of vagy forEach preferáltabb tömbökhöz
let gyumolcsokTomb = ["alma", "körte", "banán"];
console.log("For...in ciklus (tömb indexei):");
for (let index in gyumolcsokTomb) {
  console.log(`Index: ${index}, Érték: ${gyumolcsokTomb[index]}`);
}
```

#### `for...of` ciklus (ES6+)
Iterálható objektumok (pl. tömbök, stringek, Map, Set) értékein iterál végig.
```javascript
console.log("For...of ciklus (tömb értékei):");
const szinek = ["piros", "zöld", "kék"];
for (let szin of szinek) {
  console.log(szin);
}
// Kimenet: piros, zöld, kék

console.log("For...of ciklus (string karakterei):");
let udv = "Szia";
for (let karakter of udv) {
  console.log(karakter);
}
// Kimenet: S, z, i, a
```

#### `break` és `continue`
-   `break`: Azonnal megszakítja a ciklust.
-   `continue`: Az aktuális iterációt kihagyja, és a következővel folytatja a ciklust.

```javascript
console.log("Break és Continue példa:");
for (let i = 0; i < 10; i++) {
  if (i === 3) {
    continue; // Kihagyja a 3-as i értéket
  }
  if (i === 7) {
    break; // Megállítja a ciklust, amikor i = 7
  }
  console.log("Ciklusváltozó (break/continue):", i); // 0, 1, 2, 4, 5, 6
}
```

## 6. Függvények

A függvények újrafelhasználható kódrészletek, amelyek egy adott feladatot hajtanak végre. Segítenek a kód strukturálásában és a "Don't Repeat Yourself" (DRY) elv követésében.

### 6.1. Függvény Deklaráció (Function Declaration)
```javascript
// Függvény deklarálása 'udvozlet' néven, egy 'nev' paraméterrel
function udvozlet(nev) {
  console.log(`Helló, ${nev}! Üdv a függvényben!`);
}

// Függvény meghívása az 'Anna' argumentummal
udvozlet("Anna"); // Kimenet: Helló, Anna! Üdv a függvényben!
udvozlet("Péter"); // Kimenet: Helló, Péter! Üdv a függvényben!

// Függvény, ami értéket ad vissza (return)
function osszead(a, b) {
  return a + b; // Visszaadja 'a' és 'b' összegét
}

let eredmeny = osszead(5, 7);
console.log("5 + 7 =", eredmeny); // 5 + 7 = 12
```
*Hoisting:* A függvénydeklarációk "felhúzódnak" (hoisted) a hatókörük tetejére, ami azt jelenti, hogy meghívhatók a kódban való fizikai deklarációjuk előtt.

### 6.2. Függvénykifejezés (Function Expression)
Itt egy függvényt egy változóhoz rendelünk.
```javascript
const kivon = function(x, y) {
  return x - y;
}; // Figyelj a pontosvesszőre a kifejezés végén!

let kulonbseg = kivon(10, 4);
console.log("10 - 4 =", kulonbseg); // 10 - 4 = 6
```
*Hoisting:* A függvénykifejezések nem húzódnak fel. Csak a változó deklarációja (`kivon`) húzódik fel, de az értéke (`undefined`) lesz a hozzárendelésig. Ezért csak a hozzárendelés után hívható meg.

### 6.3. Nyílfüggvények (Arrow Functions - ES6+)
Rövidebb szintaxis függvénykifejezésekhez. Különösen hasznosak callback függvényeknél és ott, ahol a `this` kulcsszó viselkedése fontos.
```javascript
// Hagyományos függvénykifejezés
const szorozHagyomanyos = function(a, b) {
  return a * b;
};

// Nyílfüggvény
const szorozNyil = (a, b) => {
  return a * b;
};

// Még rövidebb nyílfüggvény (ha csak egy return utasítás van)
const szorozRovid = (a, b) => a * b;

// Nyílfüggvény egyetlen paraméterrel (zárójel elhagyható a paraméter körül)
const negyzet = x => x * x;

console.log("Szorzás (nyíl):", szorozNyil(3, 4)); // 12
console.log("Szorzás (rövid nyíl):", szorozRovid(5, 6)); // 30
console.log("Négyzet (egyparaméteres nyíl):", negyzet(7)); // 49

// Nincs saját 'this' kötése: A nyílfüggvények a befoglaló (lexikális) hatókör 'this' értékét öröklik.
// Ez eltér a hagyományos függvényektől, amelyeknek saját 'this' kötésük van, ami a hívás módjától függ.
```

### 6.4. Paraméterek és Argumentumok
-   **Paraméterek**: A függvénydefinícióban megadott változók nevei.
-   **Argumentumok**: A függvényhíváskor átadott konkrét értékek.

```javascript
function teljesNevKiir(keresztnev, vezeteknev = "Ismeretlen") { // 'vezeteknev' alapértelmezett paraméter (ES6+)
  console.log(`Teljes név: ${keresztnev} ${vezeteknev}`);
}

teljesNevKiir("Nagy", "Lajos"); // Teljes név: Nagy Lajos
teljesNevKiir("Kiss");         // Teljes név: Kiss Ismeretlen (az alapértelmezett értéket használja)
```

### 6.5. `return` Utasítás
Egy függvényből érték visszaadására szolgál. Ha nincs `return` utasítás, vagy `return;` van érték nélkül, a függvény `undefined`-et ad vissza.

## 7. Objektumok

Az objektumok kulcs-érték párok komplex gyűjteményei. A JavaScriptben szinte minden "dolog" egy objektum, vagy úgy viselkedik, mint egy objektum.

### 7.1. Objektum Literálok
Leggyakoribb módja az objektumok létrehozásának.
```javascript
const kutya = {
  nev: "Bodri", // 'nev' a kulcs (property), "Bodri" az érték
  fajta: "Puli",
  kor: 3,
  szinek: ["fekete", "fehér foltokkal"], // Tulajdonság értéke lehet tömb is
  ugat: function() { // Metódus: függvény, ami az objektum tulajdonsága
    console.log("Vau-vau!");
  },
  informacio() { // Rövidebb metódus szintaxis (ES6+)
    // 'this' kulcsszó az aktuális objektumra (kutya) hivatkozik
    console.log(`${this.nev} egy ${this.kor} éves ${this.fajta}.`);
  }
};

// Tulajdonságok elérése
console.log("A kutya neve:", kutya.nev); // Bodri (pontos jelölés)
console.log("A kutya fajtája:", kutya["fajta"]); // Puli (szögletes zárójeles jelölés)

// Metódusok hívása
kutya.ugat(); // Vau-vau!
kutya.informacio(); // Bodri egy 3 éves Puli.

// Új tulajdonság hozzáadása
kutya.kedvencEtel = "csont";
console.log("Kedvenc étel:", kutya.kedvencEtel); // csont

// Tulajdonság módosítása
kutya.kor = 4;
kutya.informacio(); // Bodri egy 4 éves Puli.

// Tulajdonság törlése
delete kutya.fajta;
console.log("Törölt fajta után:", kutya);
```

### 7.2. `this` Kulcsszó
A `this` értéke attól függ, hogyan hívják meg a függvényt (kontextus).
-   Objektum metódusában: `this` az objektumra mutat, amelyen a metódust hívták.
-   Egyszerű függvényhívásnál (nem metódusként): `this` `undefined` (strict módban) vagy a globális objektum (`window` böngészőben, `global` Node.js-ben) (nem strict módban).
-   Nyílfüggvényekben: `this` a befoglaló lexikális hatókör `this`-ét örökli. Nincs saját `this` kötése.
-   Eseménykezelőkben: `this` általában arra az elemre mutat, amely kiváltotta az eseményt.

## 8. Tömbök (Arrays)

A tömbök speciális típusú objektumok, amelyek rendezett elemek listáját tárolják. Az elemek bármilyen adattípusúak lehetnek, és egy tömbön belül keveredhetnek is.

### 8.1. Tömb Létrehozása
```javascript
// Tömb literál (leggyakoribb)
let gyumolcsok = ["alma", "banán", "cseresznye"];
let vegyesTomb = [1, "szöveg", true, null, { nev: "objektum" }];
let uresTomb = [];

// Tömb konstruktorral (ritkábban használt)
let szamok = new Array(1, 2, 3, 4, 5);
let eloreDefinialtHosszuTomb = new Array(10); // 10 elemű, üres (undefined) elemekkel teli tömb
```

### 8.2. Tömb Elemek Elérése és Módosítása
Az elemeket 0-tól kezdődő indexszel érhetjük el.
```javascript
console.log("Első gyümölcs:", gyumolcsok[0]); // alma
console.log("Második gyümölcs:", gyumolcsok[1]); // banán

gyumolcsok[1] = "körte"; // Második elem módosítása
console.log("Módosított gyümölcsök:", gyumolcsok); // ["alma", "körte", "cseresznye"]

gyumolcsok[3] = "narancs"; // Új elem hozzáadása egy adott indexre
console.log("Bővített gyümölcsök:", gyumolcsok); // ["alma", "körte", "cseresznye", "narancs"]
```

### 8.3. Tömb Tulajdonságok és Metódusok

#### `length` tulajdonság
Megadja a tömb elemeinek számát.
```javascript
console.log("Gyümölcsök száma:", gyumolcsok.length); // 4
```

#### Gyakori Tömb Metódusok
-   `push()`: Elem(ek) hozzáadása a tömb végéhez. Visszaadja az új hosszt.
    ```javascript
    gyumolcsok.push("eper", "málna");
    console.log("Push után:", gyumolcsok); // ["alma", "körte", "cseresznye", "narancs", "eper", "málna"]
    ```
-   `pop()`: Eltávolítja az utolsó elemet a tömbből és visszaadja azt.
    ```javascript
    let utolsoGyumolcs = gyumolcsok.pop();
    console.log("Pop után:", gyumolcsok); // ["alma", "körte", "cseresznye", "narancs", "eper"]
    console.log("Eltávolított gyümölcs:", utolsoGyumolcs); // málna
    ```
-   `shift()`: Eltávolítja az első elemet a tömbből és visszaadja azt. (Indexek eltolódnak!)
    ```javascript
    let elsoGyumolcs = gyumolcsok.shift();
    console.log("Shift után:", gyumolcsok); // ["körte", "cseresznye", "narancs", "eper"]
    console.log("Eltávolított első gyümölcs:", elsoGyumolcs); // alma
    ```
-   `unshift()`: Elem(ek) hozzáadása a tömb elejéhez. Visszaadja az új hosszt. (Indexek eltolódnak!)
    ```javascript
    gyumolcsok.unshift("szilva", "barack");
    console.log("Unshift után:", gyumolcsok); // ["szilva", "barack", "körte", "cseresznye", "narancs", "eper"]
    ```
-   `forEach(callbackFn)`: Végrehajt egy callback függvényt a tömb minden elemére. Nem ad vissza új tömböt.
    ```javascript
    console.log("forEach metódus:");
    gyumolcsok.forEach(function(gyumolcs, index, tomb) {
      console.log(`Index: ${index}, Gyümölcs: ${gyumolcs}`);
      // console.log(tomb); // Az eredeti tömböt is elérhetjük
    });
    ```
-   `map(callbackFn)`: Létrehoz egy új tömböt a callback függvény által visszaadott értékekből, amely minden elemen lefut.
    ```javascript
    let nagybetusGyumolcsok = gyumolcsok.map(function(gyumolcs) {
      return gyumolcs.toUpperCase();
    });
    console.log("Map (nagybetűs):", nagybetusGyumolcsok);
    // ["SZILVA", "BARACK", "KÖRTE", "CSERESZNYE", "NARANCS", "EPER"]
    ```
-   `filter(callbackFn)`: Létrehoz egy új tömböt azokkal az elemekkel, amelyekre a callback függvény `true`-t ad vissza.
    ```javascript
    let rovidNevuGyumolcsok = gyumolcsok.filter(gyumolcs => gyumolcs.length < 6); // Nyílfüggvénnyel
    console.log("Filter (rövid nevek):", rovidNevuGyumolcsok); // Pl. ["körte", "eper"] (a tömb aktuális tartalmától függően)
    ```
-   `reduce(callbackFn, initialValue)`: "Redukálja" a tömböt egyetlen értékké. A callback függvény egy `accumulator`-t és a `currentValue`-t kap.
    ```javascript
    let szamokLista = [1, 2, 3, 4, 5];
    let osszeg = szamokLista.reduce(function(akkumulator, aktualisErtek) {
      return akkumulator + aktualisErtek;
    }, 0); // 0 a kezdeti akkumulátor érték
    console.log("Reduce (összeg):", osszeg); // 15
    ```
-   `find(callbackFn)`: Visszaadja az első elemet a tömbben, amelyre a callback `true`-t ad. Ha nincs ilyen, `undefined`.
    ```javascript
    let elsoHosszuGyumolcs = gyumolcsok.find(gyumolcs => gyumolcs.length > 6);
    console.log("Find (első hosszú gyümölcs):", elsoHosszuGyumolcs); // Pl. "cseresznye"
    ```
-   `findIndex(callbackFn)`: Visszaadja az első elem indexét, amelyre a callback `true`-t ad. Ha nincs ilyen, `-1`.
    ```javascript
    let narancsIndexe = gyumolcsok.findIndex(gyumolcs => gyumolcs === "narancs");
    console.log("FindIndex (narancs indexe):", narancsIndexe);
    ```
-   `includes(ertek, startIndex)`: Ellenőrzi, hogy a tömb tartalmazza-e a megadott értéket. `true` vagy `false`.
    ```javascript
    console.log("Tartalmazza-e a 'körte'-t:", gyumolcsok.includes("körte")); // true
    console.log("Tartalmazza-e a 'mangó'-t:", gyumolcsok.includes("mangó")); // false
    ```
-   `slice(start, end)`: Visszaad egy új tömböt, ami az eredeti tömb egy részének másolata. Az eredeti tömb nem módosul. `end` index nincs benne.
    ```javascript
    let szelet = gyumolcsok.slice(1, 3); // A 1-es és 2-es indexű elemek
    console.log("Slice (szelet):", szelet); // Pl. ["barack", "körte"] (az aktuális tömbtartalomtól függ)
    console.log("Eredeti tömb slice után:", gyumolcsok); // Nem változott
    ```
-   `splice(start, deleteCount, ...itemsToAdd)`: Módosítja az eredeti tömböt elemek eltávolításával és/vagy hozzáadásával. Visszaadja az eltávolított elemek tömbjét.
    ```javascript
    let eltavolitottak = gyumolcsok.splice(2, 2, "kiwi", "ananász"); // A 2. indextől 2 elemet töröl, és beilleszti a "kiwi", "ananász"-t
    console.log("Splice után (módosított tömb):", gyumolcsok);
    console.log("Splice (eltávolított elemek):", eltavolitottak);
    ```
-   `join(separator)`: Összefűzi a tömb elemeit egy stringgé, a megadott elválasztóval. Alapértelmezett elválasztó a vessző (`,`).
    ```javascript
    let gyumolcsString = gyumolcsok.join(" - ");
    console.log("Join (stringgé alakítva):", gyumolcsString);
    ```

## 9. DOM Manipuláció (Csak Böngészői Környezetben)

A DOM (Document Object Model) a HTML dokumentum strukturált, objektum-orientált reprezentációja. JavaScripttel manipulálhatjuk a DOM-ot, hogy dinamikusan módosítsuk a weboldal tartalmát, szerkezetét és stílusát.

*Figyelem: Az alábbi példák feltételezik, hogy egy HTML fájl kontextusában futnak.*
```html
<!-- Példa HTML a DOM manipulációhoz:
<div id="kontener">
  <h1 id="foCim">Régi Címsor</h1>
  <p class="bekezdes">Ez az első bekezdés.</p>
  <p class="bekezdes">Ez a második bekezdés.</p>
</div>
<button id="ujElemGomb">Új elem hozzáadása</button>
-->
```

### 9.1. Elemek Kiválasztása
```javascript
// // --- HTML-ben futtatandó kód ---

// // Elem kiválasztása ID alapján (egyedi)
// const foCimElem = document.getElementById("foCim");
// if (foCimElem) {
//   console.log("Főcím elem:", foCimElem);
// }

// // Elemek kiválasztása osztálynév alapján (HTMLCollection-t ad vissza)
// const bekezdesElemek = document.getElementsByClassName("bekezdes");
// if (bekezdesElemek.length > 0) {
//   console.log("Bekezdés elemek:", bekezdesElemek);
//   console.log("Első bekezdés:", bekezdesElemek[0]);
// }

// // Elemek kiválasztása tag név alapján (HTMLCollection-t ad vissza)
// const pElemek = document.getElementsByTagName("p");
// if (pElemek.length > 0) {
//   console.log("Összes p elem:", pElemek);
// }

// // Elem kiválasztása CSS szelektorral (az első találatot adja vissza) - NAGYON HASZNOS
// const kontenerElem = document.querySelector("#kontener"); // ID szelektor
// const elsoBekezdes = document.querySelector(".bekezdes"); // Osztály szelektor (első)
// const masodikP = document.querySelector("p:nth-child(3)"); // Komplexebb szelektor
// if (kontenerElem) console.log("Konténer querySelectorral:", kontenerElem);

// // Elemek kiválasztása CSS szelektorral (NodeList-et ad vissza) - NAGYON HASZNOS
// const osszesBekezdesNodeList = document.querySelectorAll(".bekezdes");
// console.log("Bekezdések NodeList-je:", osszesBekezdesNodeList);
// // A NodeList-en használható a forEach (ellentétben a HTMLCollection-nel régebbi böngészőkben)
// osszesBekezdesNodeList.forEach(p => console.log(p.textContent));
```

### 9.2. Elemek Tartalmának és Attribútumainak Módosítása
```javascript
// // --- HTML-ben futtatandó kód ---

// if (foCimElem) {
//   // Szöveges tartalom módosítása
//   foCimElem.textContent = "Új, Dinamikus Címsor!";

//   // HTML tartalom módosítása (óvatosan, XSS veszély miatt, ha felhasználói inputból jön!)
//   // foCimElem.innerHTML = "<em>Dőlt Új Címsor</em>";
// }

// if (elsoBekezdes) {
//   // Attribútumok módosítása
//   elsoBekezdes.setAttribute("data-info", "Ez egy fontos bekezdés");
//   console.log("Data-info attribútum:", elsoBekezdes.getAttribute("data-info"));

//   // Osztályok kezelése
//   elsoBekezdes.classList.add("kiemelt");
//   elsoBekezdes.classList.remove("bekezdes"); // Ha el akarnánk távolítani
//   console.log("Van 'kiemelt' osztálya?", elsoBekezdes.classList.contains("kiemelt")); // true
//   elsoBekezdes.classList.toggle("masik-osztaly"); // Ha nincs, hozzáadja, ha van, elveszi
// }
```

### 9.3. Elemek Stílusának Módosítása
```javascript
// // --- HTML-ben futtatandó kód ---

// if (foCimElem) {
//   foCimElem.style.color = "blue";
//   foCimElem.style.backgroundColor = "lightyellow"; // camelCase a CSS kötőjeles tulajdonságok helyett
//   foCimElem.style.padding = "10px";
// }
// // Jobb gyakorlat osztályokat hozzáadni/eltávolítani a stílusozáshoz, mint direkt inline stílusokat módosítani.
```

### 9.4. Új Elemek Létrehozása és Hozzáadása
```javascript
// // --- HTML-ben futtatandó kód ---

// const ujElemGomb = document.getElementById("ujElemGomb");
// const kontenerDiv = document.getElementById("kontener");

// if (ujElemGomb && kontenerDiv) {
//   ujElemGomb.onclick = function() { // Egyszerűbb eseménykezelés (lásd később)
//     // 1. Új elem létrehozása
//     const ujListaElem = document.createElement("li");

//     // 2. Tartalom és attribútumok beállítása
//     ujListaElem.textContent = "Új listaelem " + (kontenerDiv.querySelectorAll("li").length + 1);
//     ujListaElem.classList.add("lista-elem-stilus");

//     // 3. Elem hozzáadása a DOM-hoz
//     // Ha még nincs ul elem, létrehozzuk
//     let lista = kontenerDiv.querySelector("ul");
//     if (!lista) {
//       lista = document.createElement("ul");
//       kontenerDiv.appendChild(lista); // Hozzáadja a konténer végére
//     }
//     lista.appendChild(ujListaElem); // Hozzáadja az új elemet a lista végére

//     // Egyéb hozzáadási módok:
//     // kontenerDiv.prepend(ujElem); // Hozzáadja a konténer elejére
//     // kontenerDiv.insertBefore(ujElem, letezoElem); // Hozzáadja egy létező elem elé
//   };
// }
```

### 9.5. Elemek Eltávolítása
```javascript
// // --- HTML-ben futtatandó kód ---

// if (elsoBekezdes && elsoBekezdes.parentNode) {
//   // elsoBekezdes.parentNode.removeChild(elsoBekezdes); // Régebbi módszer
//   // elsoBekezdes.remove(); // Modern, egyszerűbb módszer
// }
```

## 10. Eseménykezelés (Csak Böngészői Környezetben)

Az eseménykezelés lehetővé teszi, hogy JavaScript kódunk reagáljon a felhasználói interakciókra (pl. kattintás, egérmozgás, billentyűleütés) vagy a böngésző által kiváltott eseményekre (pl. oldal betöltődése, ablak átméretezése).

### 10.1. `addEventListener()`
Ez a preferált módszer eseményfigyelők csatolására egy elemhez.
```javascript
// // --- HTML-ben futtatandó kód ---
// // Tegyük fel, van egy <button id="myButton">Kattints Rám!</button> a HTML-ben.

// const gomb = document.getElementById("myButton"); // Vagy a korábbi 'ujElemGomb'

// if (gomb) {
//   gomb.addEventListener("click", function(event) {
//     // 'this' itt a 'gomb' elemre mutat (kivéve nyílfüggvény esetén!)
//     console.log("A gombra kattintottak!");
//     console.log("Esemény objektum:", event); // Az esemény részleteit tartalmazza
//     console.log("Esemény típusa:", event.type); // "click"
//     console.log("Célelem:", event.target); // A gomb maga

//     // event.preventDefault(); // Megakadályozza az esemény alapértelmezett viselkedését (pl. űrlap küldése)
//     // event.stopPropagation(); // Megállítja az esemény továbbterjedését a DOM fán (bubbling/capturing)
//   });

//   // Másik eseményfigyelő ugyanarra az eseményre
//   gomb.addEventListener("click", () => {
//     // Nyílfüggvénynél a 'this' a külső hatókör 'this'-e, nem a gomb!
//     alert("Második kattintás esemény!");
//   });

//   // Egérmozgás esemény
//   // document.body.addEventListener("mousemove", function(event) {
//   //   console.log(`Egér pozíció: X=${event.clientX}, Y=${event.clientY}`);
//   // });
// }
```
Gyakori eseménytípusok: `click`, `mouseover`, `mouseout`, `mousedown`, `mouseup`, `mousemove`, `keydown`, `keyup`, `keypress`, `focus`, `blur`, `submit` (űrlapoknál), `load` (pl. `window.addEventListener('load', ...)`), `DOMContentLoaded`.

## 11. Aszinkron JavaScript

A JavaScript alapvetően egyszálú, ami azt jelenti, hogy egyszerre csak egy dolgot tud csinálni. Az aszinkron programozás lehetővé teszi, hogy hosszan tartó műveletek (pl. hálózati kérések, fájl olvasás, időzítők) ne blokkolják a fő szálat, így a felhasználói felület reszponzív marad.

### 11.1. Callback Függvények (Visszahívások)
Egy függvény, amit argumentumként adunk át egy másik függvénynek, és az később, egy művelet befejeztével hívja meg.
```javascript
function adatLekeresCallback(url, sikerCallback, hibaCallback) {
  console.log(`Adatok lekérése innen: ${url}`);
  setTimeout(() => { // Szimulál egy hálózati késleltetést
    const siker = Math.random() > 0.3; // 70% eséllyel sikeres
    if (siker) {
      const adatok = { id: 1, tartalom: "Ez itt az adat!" };
      sikerCallback(adatok);
    } else {
      hibaCallback("Hiba történt az adatok lekérése közben.");
    }
  }, 1500); // 1.5 másodperc múlva fut le
}

// Callback függvények használata
// adatLekeresCallback(
//   "https://api.example.com/data",
//   function(data) { // Siker callback
//     console.log("Sikeres adatlekérés (callback):", data);
//     // Itt további műveletek jöhetnek, pl. másik aszinkron hívás...
//     // Ez vezethet a "Callback Hell" vagy "Pyramid of Doom" problémához
//   },
//   function(error) { // Hiba callback
//     console.error("Hiba (callback):", error);
//   }
// );
```
A mélyen egymásba ágyazott callbackek ("Callback Hell") nehezen olvashatóvá és karbantarthatóvá teszik a kódot.

### 11.2. Promises (Ígéretek - ES6+)
Egy `Promise` egy objektum, ami egy aszinkron művelet jövőbeli eredményét (vagy hibáját) reprezentálja.
Három állapota lehet:
-   `pending`: Kezdeti állapot, a művelet még nem fejeződött be.
-   `fulfilled` (vagy `resolved`): A művelet sikeresen befejeződött.
-   `rejected`: A művelet hibával fejeződött be.

```javascript
function adatLekeresPromise(url) {
  console.log(`Adatok lekérése (Promise) innen: ${url}`);
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const siker = Math.random() > 0.3;
      if (siker) {
        const adatok = { id: 2, tartalom: "Promise adatok!" };
        resolve(adatok); // Ígéret teljesítése az adatokkal
      } else {
        reject("Hiba történt az adatok lekérése közben (Promise)."); // Ígéret elutasítása a hibával
      }
    }, 1000);
  });
}

// Promise használata
// adatLekeresPromise("https://api.example.com/promise-data")
//   .then(function(data) { // Akkor fut le, ha a Promise 'fulfilled' (resolve hívódott)
//     console.log("Sikeres adatlekérés (Promise.then):", data);
//     // További Promise-okat lehet láncolni:
//     // return masikPromiseKeszitoFuggveny(data.id);
//   })
//   // .then(function(masikAdat) { ... })
//   .catch(function(error) { // Akkor fut le, ha a Promise 'rejected' (reject hívódott), vagy bármelyik korábbi .then-ben hiba történt
//     console.error("Hiba (Promise.catch):", error);
//   })
//   .finally(function() { // Mindig lefut, akár siker, akár hiba történt
//     console.log("Promise művelet befejeződött (finally).");
//   });
```

### 11.3. Async/Await (ES2017+)
Szintaktikai cukorka a Promise-ok kezelésére, ami olvashatóbbá és szinkron-szerűvé teszi az aszinkron kódot.
-   `async` kulcsszó egy függvény elé írva azt jelzi, hogy a függvény aszinkron, és implicit módon egy Promise-t ad vissza.
-   `await` kulcsszó egy `async` függvényen belül használható egy Promise elé írva. Megvárja, amíg a Promise teljesül (vagy elutasításra kerül), és visszaadja annak eredményét (vagy dobja a hibát).

```javascript
// Az 'adatLekeresPromise' függvényt használjuk az előző példából

async function adatFeldolgozas() {
  console.log("Async/Await: Adatfeldolgozás indul...");
  try {
    // Az 'await' megvárja, amíg az adatLekeresPromise() Promise teljesül
    const kapottAdatok = await adatLekeresPromise("https://api.example.com/async-data");
    // A kód itt csak akkor folytatódik, ha a Promise resolved
    console.log("Sikeres adatlekérés (async/await):", kapottAdatok);

    // Tegyük fel, van egy másik aszinkron művelet, ami az első eredményétől függ
    // const feldolgozottAdat = await masikAszinkronFuggveny(kapottAdatok.id);
    // console.log("Feldolgozott adat:", feldolgozottAdat);

    return "Feldolgozás sikeres!"; // Ez lesz a Promise resolve értéke, amit az async függvény visszaad
  } catch (hiba) {
    // Ha az adatLekeresPromise() reject-el, vagy bármelyik await-elt Promise hibát dob,
    // a catch blokk fogja elkapni.
    console.error("Hiba (async/await catch):", hiba);
    throw hiba; // Opcionálisan továbbdobhatjuk a hibát, hogy a hívó is kezelhesse
  } finally {
    console.log("Async/Await: Adatfeldolgozás befejeződött (finally).");
  }
}

// Az async függvény meghívása is Promise-t ad vissza
// adatFeldolgozas()
//   .then(uzenet => console.log("Async függvény eredménye:", uzenet))
//   .catch(err => console.error("Async függvényből jövő hiba:", err));

// Azonnal meghívott async függvény kifejezés (IIFE - Immediately Invoked Function Expression)
// (async () => {
//   await adatFeldolgozas();
//   console.log("Az IIFE async művelet is kész.");
// })();
```

## 12. ES6+ Modulok

A modulok lehetővé teszik a kód felosztását különálló fájlokra, amelyeket szükség szerint importálhatunk és exportálhatunk. Ez javítja a kód szervezettségét, karbantarthatóságát és újrafelhasználhatóságát.

### 12.1. Exportálás (`export`)
Egy modulból (fájlból) változókat, függvényeket, osztályokat tehetünk elérhetővé más modulok számára.

```javascript
// --- fajlnev: matematika.js ---

// Nevesített export (Named Export) - Több is lehet egy fájlban
// export const PI = 3.14159;

// export function osszead(a, b) {
//   return a + b;
// }

// export class Szamologep {
//   constructor() {
//     console.log("Számológép létrehozva.");
//   }
//   kivon(a, b) {
//     return a - b;
//   }
// }

// Alapértelmezett export (Default Export) - Csak egy lehet egy fájlban
// const ALAP_ERTEK = 100;
// export default ALAP_ERTEK;

// VAGY egy függvény/osztály is lehet default export
// export default function koszon() {
//    console.log("Helló a modulból!");
// }
```

### 12.2. Importálás (`import`)
Más modulok által exportált elemeket használhatunk.

```javascript
// --- fajlnev: main.js ---

// Nevesített importok (pontosan az exportált nevekkel, kapcsos zárójelben)
// import { PI, osszead, Szamologep } from './matematika.js'; // Fontos a ./ a relatív útvonalhoz

// console.log("PI értéke:", PI);
// console.log("2 + 3 =", osszead(2, 3));
// const gep = new Szamologep();
// console.log("10 - 4 =", gep.kivon(10, 4));

// Alias adása importáláskor
// import { osszead as add } from './matematika.js';
// console.log("5 + 5 (aliassal) =", add(5, 5));

// Minden nevesített export importálása egy objektumba
// import * as matekModul from './matematika.js';
// console.log("PI (objektumból):", matekModul.PI);
// console.log("7 + 8 (objektumból):", matekModul.osszead(7, 8));

// Alapértelmezett import (bármilyen nevet adhatunk neki, nincs szükség kapcsos zárójelre)
// import BarmiNevLehetAzAlaperteknek from './matematika.js'; // Ha az ALAP_ERTEK volt a default
// import koszontesFuggveny from './matematika.js'; // Ha a koszon() volt a default
// console.log("Alapértelmezett érték:", BarmiNevLehetAzAlaperteknek);
// koszontesFuggveny();

// Vegyes import (default és named együtt)
// Feltételezve, hogy a matematika.js-ben van default export ÉS named exportok is:
// import alap, { PI, osszead } from './matematika.js';
// console.log(alap);
// console.log(PI);
```

### 12.3. Modulok Használata Böngészőben
A HTML `<script>` tag-jéhez hozzá kell adni a `type="module"` attribútumot.
```html
<!-- <script type="module" src="main.js"></script> -->
```
*Megjegyzés: Modulok helyi fájlrendszerből (`file://` protokoll) való futtatása biztonsági korlátozásokba ütközhet (CORS policy). Fejlesztéshez érdemes egy egyszerű helyi webszervert használni (pl. Live Server VS Code-ban, vagy `npx http-server`).*

## 13. Hibakezelés (`try...catch...finally`)

Lehetővé teszi a futásidejű hibák (exceptions) elkapását és kezelését, hogy a program ne álljon le váratlanul.

```javascript
function osztas(a, b) {
  if (b === 0) {
    // Hiba objektum létrehozása és "dobása" (throwing)
    throw new Error("Nullával való osztás nem megengedett!");
  }
  return a / b;
}

try {
  // Olyan kód, ami hibát dobhat
  let eredmeny1 = osztas(10, 2);
  console.log("10 / 2 =", eredmeny1); // 5

  let eredmeny2 = osztas(5, 0); // Ez hibát fog dobni
  console.log("5 / 0 =", eredmeny2); // Ez a sor már nem fut le

} catch (error) {
  // Ez a blokk akkor fut le, ha a 'try' blokkban hiba történik
  console.error("Hiba történt a 'try' blokkban!");
  console.error("Hiba neve:", error.name);       // Pl. "Error"
  console.error("Hiba üzenete:", error.message); // "Nullával való osztás nem megengedett!"
  // console.error("Hiba stack trace:", error.stack); // Részletes hívási lánc
} finally {
  // Ez a blokk mindig lefut, akár történt hiba a 'try' blokkban, akár nem.
  // Hasznos erőforrások felszabadítására (pl. fájlok bezárása, hálózati kapcsolat bontása).
  console.log("A 'try...catch' blokk végrehajtása befejeződött.");
}

console.log("A program folytatódik a hibakezelés után.");
```

## 14. JSON (JavaScript Object Notation)

A JSON egy könnyűsúlyú adatcsere-formátum. Szintaxisa a JavaScript objektum literálokból származik, de annál szigorúbb (pl. kulcsoknak idézőjelben kell lenniük, kommentek nem megengedettek). Gyakran használják API-kban adatok küldésére és fogadására.

### 14.1. `JSON.stringify()`
JavaScript objektumot vagy értéket JSON stringgé alakít.
```javascript
const user = {
  id: 101,
  nev: "Teszt Elek",
  email: "teszt@example.com",
  aktiv: true,
  profilAdatok: {
    eletkor: 33,
    varos: "Budapest"
  },
  // A függvények és undefined értékek kimaradnak a JSON stringből
  getNev: function() { return this.nev; },
  utolsoBelepes: undefined
};

const jsonString = JSON.stringify(user, null, 2); // A 2-es paraméter a szép formázáshoz (behúzás)
console.log("JSON string:\n", jsonString);
/* Kimenet:
{
  "id": 101,
  "nev": "Teszt Elek",
  "email": "teszt@example.com",
  "aktiv": true,
  "profilAdatok": {
    "eletkor": 33,
    "varos": "Budapest"
  }
}
*/
```

### 14.2. `JSON.parse()`
JSON stringet JavaScript objektummá alakít.
```javascript
const jsonData = `{
  "termekNev": "Laptop",
  "ar": 250000,
  "elerheto": true,
  "specifikaciok": ["16GB RAM", "512GB SSD", "Intel i7"]
}`;

try {
  const termekObjektum = JSON.parse(jsonData);
  console.log("JavaScript objektum JSON stringből:", termekObjektum);
  console.log("Termék neve:", termekObjektum.termekNev); // Laptop
  console.log("Második specifikáció:", termekObjektum.specifikaciok[1]); // 512GB SSD
} catch (error) {
  console.error("Hiba a JSON parse közben:", error.message); // Ha a jsonData nem valid JSON
}
```

## 15. Fetch API (Hálózati Kérések)

A Fetch API egy modern, Promise-alapú interfész hálózati kérések (pl. adatok lekérése egy szerverről) végrehajtására. Ez a `XMLHttpRequest` (XHR) utódja.

```javascript
// // --- HTML-ben vagy Node.js-ben (node-fetch telepítése után) futtatandó kód ---
// // Böngészőben a fetch globálisan elérhető.
// // Node.js-ben: npm install node-fetch
// // majd: import fetch from 'node-fetch'; vagy const fetch = require('node-fetch');

// const apiUrl = "https://jsonplaceholder.typicode.com/todos/1"; // Egy ingyenes teszt API végpont

// console.log("Adatok lekérése Fetch API-val...");
// fetch(apiUrl)
//   .then(response => {
//     // A 'response' objektum a HTTP választ tartalmazza, nem közvetlenül az adatokat.
//     console.log("Válasz objektum:", response);
//     if (!response.ok) { // Ellenőrizzük, hogy a HTTP státuszkód sikeres-e (pl. 200-299)
//       throw new Error(`HTTP hiba! Státusz: ${response.status}`);
//     }
//     // A válasz testét JSON-ként kell feldolgozni (ez is egy Promise-t ad vissza)
//     return response.json();
//   })
//   .then(data => {
//     // Itt kapjuk meg a feldolgozott JSON adatokat JavaScript objektumként
//     console.log("Lekért adatok (JSON):", data);
//     console.log("Feladat címe:", data.title);
//   })
//   .catch(error => {
//     // Hálózati hibák vagy a fenti 'throw new Error' itt kerül elkapásra
//     console.error("Hiba történt a fetch során:", error);
//   });

// // POST kérés Fetch API-val (adatok küldése)
// async function ujTodoLetrehozasa(todoAdat) {
//   const postApiUrl = "https://jsonplaceholder.typicode.com/todos";
//   try {
//     const response = await fetch(postApiUrl, {
//       method: "POST", // HTTP metódus
//       headers: {
//         "Content-Type": "application/json" // Fontos a tartalom típusának megadása
//       },
//       body: JSON.stringify(todoAdat) // A küldendő adat JSON stringgé alakítva
//     });

//     if (!response.ok) {
//       throw new Error(`HTTP hiba POST kérésnél! Státusz: ${response.status}`);
//     }

//     const letrehozottTodo = await response.json();
//     console.log("Sikeresen létrehozott TODO (POST):", letrehozottTodo);
//     return letrehozottTodo;
//   } catch (error) {
//     console.error("Hiba történt a POST kérés során:", error);
//   }
// }

// // ujTodoLetrehozasa({
// //   userId: 1,
// //   title: "JavaScript tanulása Fetch API-val",
// //   completed: false
// // });
```

## További Fontos Koncepciók és Tanulnivalók

-   **ES6+ Szintaktikai Újdonságok:**
    -   **Destrukturálás (Destructuring Assignment):** Objektumokból és tömbökből értékek egyszerű kinyerése.
    -   **Spread (`...`) és Rest (`...`) Operátorok:** Tömbök és objektumok kibontása, vagy függvényparaméterek összegyűjtése.
    -   **Template Literals:** (Már említettük) Stringek egyszerűbb létrehozása változóbeillesztéssel és többsoros stringekkel.
    -   **Osztályok (Classes):** Szintaktikai cukorka a prototípus-alapú öröklődéshez, az objektum-orientált programozás megkönnyítésére.
    -   **Set és Map Adatszerkezetek:** Egyedi értékek gyűjteménye (Set) és kulcs-érték párok fejlettebb gyűjteménye (Map).
    -   **Strict Mode (`'use strict';`):** Szigorúbb hibakezelést és "biztonságosabb" JavaScriptet tesz lehetővé.
-   **Prototípusok és Öröklődés:** A JavaScript öröklődési mechanizmusának mélyebb megértése.
-   **Closure (Lezárás):** Egy függvény képessége, hogy "emlékezzen" a külső (befoglaló) hatókörének változóira, még azután is, hogy a külső függvény befejezte a futását.
-   **Reguláris Kifejezések (Regular Expressions):** Minták illesztése szövegekben.
-   **Web Storage (localStorage, sessionStorage):** Adatok tárolása a böngészőben.
-   **JavaScript Keretrendszerek és Könyvtárak:**
    -   **Kliensoldali (Frontend):** React, Angular, Vue.js, Svelte
    -   **Szerveroldali (Backend) Node.js-hez:** Express.js, NestJS, Koa
    -   **Segédkönyvtárak:** Lodash, Moment.js (vagy modernebb alternatívái, pl. date-fns, Day.js)
-   **Fejlesztői Eszközök (Browser DevTools):** Konzol, Debugger, Network monitor, Performance profiler.
-   **Verziókezelés (Git):** Elengedhetetlen a modern szoftverfejlesztésben.
-   **Csomagkezelők (npm, yarn):** Külső könyvtárak (csomagok) telepítésére és kezelésére.
-   **Build Eszközök és Transpilerek:** Webpack, Parcel, Rollup, Babel (modern JS kód régebbi böngészők által is érthetővé alakítása).
-   **Tesztelés:** Unit tesztek (Jest, Mocha, Jasmine), End-to-End tesztek (Cypress, Playwright).

Ez a jegyzet egy szilárd alapot nyújt a JavaScript világában való elinduláshoz és elmélyüléshez. A programozás, mint minden készség, gyakorlást igényel. Kísérletezz, írj saját projekteket, és ne félj hibázni – ez a tanulási folyamat része! Sok sikert!
```

**Hogyan használd GitHub-on (ismétlés):**

1.  Másold ki a fenti teljes kódrészletet (a ```markdown és a záró ``` jelekkel együtt).
2.  Menj a GitHub-on arra a helyre, ahova be szeretnéd illeszteni (pl. egy `README.md` fájl szerkesztési nézetébe, egy Issue kommentbe, egy Wiki oldal szerkesztőjébe).
3.  Illeszd be a másolt szöveget.
4.  GitHub automatikusan feldolgozza a Markdown-t, és szépen formázva, szintaxiskiemeléssel jeleníti meg a jegyzetet.

Ez a verzió sokkal több részletet, példát és magyarázatot tartalmaz, remélhetőleg lefedi az igényeidet!