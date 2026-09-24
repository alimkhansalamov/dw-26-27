# JavaScript herhaling

## Voorbereiding op TypeScript en React

In deze les herhaal je de JavaScript die je nodig hebt om met TypeScript en React aan de slag te gaan. Je werkt met functies, arrays, objecten, events en API-data.

Na deze les kun je:

* functies schrijven die gegevens ontvangen, verwerken en teruggeven;
* arrays doorzoeken, filteren en omzetten;
* objecten en arrays bijwerken zonder de oorspronkelijke gegevens te wijzigen;
* moderne JavaScript-syntax lezen en toepassen;
* gebruikersinteractie verwerken;
* code verdelen over modules;
* gegevens ophalen via een API en fouten afhandelen.

## Lesindeling

## Voorbereiding

Gebruik een code-editor, een browser en een lokale ontwikkelserver, bijvoorbeeld Live Server.

Maak deze bestanden aan:

```text
javascript-herhaling/
├── index.html
├── style.css
└── app.js
```

Begin met deze HTML:

```html
<!doctype html>
<html lang="nl">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>JavaScript herhaling</title>

    <link rel="stylesheet" href="./style.css" />
    <script type="module" src="./app.js"></script>
  </head>

  <body>
    <main>
      <h1>JavaScript herhaling</h1>
    </main>
  </body>
</html>
```

`type="module"` maakt het mogelijk om `import` en `export` te gebruiken. Een modulescript wordt standaard uitgevoerd nadat de HTML verwerkt is.

Open je pagina via de lokale server. Open ook de ontwikkelaarstools van je browser:

* **Console:** uitvoer van `console.log()` en JavaScriptfouten.
* **Network:** aanvragen naar bijvoorbeeld een API.
* **Elements:** de HTML-structuur en toegepaste CSS.

Voer losse oefeningen afzonderlijk uit in `app.js`. Vervang de vorige oefening of zet die in commentaar om dubbele variabelenamen te vermijden.

---

# 1. Startcheck


Voorspel eerst de uitvoer. Voer daarna de code uit en vergelijk.

### Vraag 1 — Getallen en tekst

```js
const price = "20";
const quantity = 2;

console.log(price + quantity);
console.log(Number(price) + quantity);
```

### Vraag 2 — Vergelijken

```js
console.log(5 === "5");
console.log(5 == "5");
```

### Vraag 3 — Een functie

```js
const double = (number) => {
  number * 2;
};

console.log(double(4));
```

### Vraag 4 — Arrays

```js
const numbers = [2, 4, 6];
const result = numbers.map((number) => number + 1);

console.log(result);
console.log(numbers);
```

### Vraag 5 — Objecten

```js
const user = {
  name: "Sara",
};

const otherUser = user;
otherUser.name = "Noor";

console.log(user.name);
```

---

# 2. HTML en CSS: de noodzakelijke basis


HTML beschrijft de structuur en betekenis van een pagina. CSS bepaalt de vormgeving. JavaScript voegt gedrag toe.

## 2.1 Gebruik het juiste HTML-element

Kies een element op basis van zijn functie.

| Doel                                            | Element                  |
| ----------------------------------------------- | ------------------------ |
| Hoofdinhoud                                     | `<main>`                 |
| Zelfstandig inhoudsblok, zoals een productkaart | `<article>`              |
| Titel                                           | `<h1>` tot en met `<h6>` |
| Navigeren naar een andere pagina                | `<a>`                    |
| Een actie uitvoeren                             | `<button>`               |
| Gegevens invoeren en versturen                  | `<form>`                 |
| Invoerveld beschrijven                          | `<label>`                |
| Een verzameling items tonen                     | `<ul>` en `<li>`         |

Gebruik voor een actie een echte knop:

```html
<button type="button">Voeg toe aan favorieten</button>
```

Een klikbare `<div>` heeft niet automatisch hetzelfde toetsenbordgedrag en dezelfde toegankelijkheid als een knop.

Geef knoppen in een formulier bewust een type:

```html
<button type="submit">Opslaan</button>
<button type="button">Annuleren</button>
```

Een `<button>` in een formulier is zonder expliciet type standaard een submitknop.

## 2.2 Formulieren en labels

```html
<form id="profile-form">
  <label for="username">Gebruikersnaam</label>

  <input
    id="username"
    name="username"
    type="text"
    autocomplete="username"
    required
  />

  <button type="submit">Opslaan</button>
</form>
```

* `for="username"` koppelt het label aan het element met `id="username"`.
* `name` bepaalt de veldnaam bij het verzamelen of versturen van formuliergegevens.
* `required` activeert ingebouwde browservalidatie.
* Een placeholder vervangt geen label.

## 2.3 `class` en `id`

Een `class` is herbruikbaar. Een `id` moet uniek zijn binnen de pagina.

```html
<article class="card" id="featured-product">
  <h2>Toetsenbord</h2>
</article>

<article class="card">
  <h2>Muis</h2>
</article>
```

```css
.card {
  padding: 1rem;
}

#featured-product {
  border: 2px solid royalblue;
}
```

Gebruik doorgaans classes voor vormgeving. Een `id` is handig voor bijvoorbeeld een labelkoppeling of het selecteren van één specifiek element.

## 2.4 Boxmodel en flexbox

Het boxmodel bestaat uit:

* **content:** de inhoud;
* **padding:** ruimte tussen inhoud en rand;
* **border:** de rand;
* **margin:** ruimte buiten het element.

```css
* {
  box-sizing: border-box;
}
```

Met `border-box` zijn padding en border inbegrepen in de ingestelde breedte en hoogte.

Flexbox helpt om elementen naast of onder elkaar te plaatsen:

```css
.product-list {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.card {
  flex: 1 1 220px;
  padding: 1rem;
  border: 1px solid #d1d5db;
  border-radius: 8px;
}
```

Hier mogen kaarten groeien, krimpen en naar een volgende rij gaan. Hun gewenste basisbreedte is `220px`.

## Oefening 1 — Verbeter een formulier

Onderstaande code stelt een inschrijfformulier voor.

```html
<div class="signup">
  <div>Inschrijven</div>
  <input type="text" placeholder="E-mailadres" />
  <div class="button">Versturen</div>
</div>
```

Pas de code aan:

1. Gebruik een formulier.
2. Gebruik een passende titel.
3. Voeg een gekoppeld label toe.
4. Gebruik het juiste inputtype en maak het veld verplicht.
5. Gebruik een submitknop.
6. Plaats de onderdelen onder elkaar met `12px` tussenruimte.
7. Geef het formulier een maximale breedte van `400px`.

---

# 3. Variabelen, voorwaarden en functies

## 3.1 `const` en `let`

Gebruik `const` wanneer je de variabele geen nieuwe waarde toekent. Gebruik `let` wanneer dat wel nodig is.

```js
const firstName = "Lina";
let score = 0;

score = score + 1;
```

Dit mag niet:

```js
const score = 0;
score = 1; // TypeError
```

`const` betekent niet dat de inhoud van een object of array onveranderlijk is:

```js
const user = {
  name: "Lina",
};

user.name = "Amir"; // Dit mag.
```

Je wijzigt hier de inhoud van het object. Je kent geen ander object toe aan `user`.

Gebruik in deze cursus geen `var`. `let` en `const` hebben block scope: ze zijn alleen beschikbaar binnen het blok waarin ze gedeclareerd zijn.

```js
if (true) {
  const message = "Hallo";
}

console.log(message); // ReferenceError
```

## 3.2 Datatypes en conversie

Veelgebruikte waarden:

```js
const name = "Sara";          // string
const age = 21;               // number
const isActive = true;        // boolean
const selectedProduct = null; // bewust geen geselecteerd product
let result;                  // undefined: nog geen waarde
```

Waarden uit gewone invoervelden zijn strings, ook wanneer het veld `type="number"` heeft.

```js
const inputValue = "12";
const quantity = Number(inputValue);

console.log(quantity + 1); // 13
```

Let op bij optellen:

```js
console.log("12" + 1); // "121"
console.log(12 + 1);   // 13
```

Een ongeldige conversie levert `NaN` op:

```js
const quantity = Number("abc");

console.log(Number.isNaN(quantity)); // true
```

Controleer lege invoer vóór je converteert:

```js
console.log(Number("")); // 0
```

Een leeg veld betekent dus niet automatisch dat de gebruiker bewust nul heeft ingevuld.

## 3.3 Vergelijken en voorwaarden

Gebruik standaard `===` en `!==`. Ze vergelijken zonder automatische typeconversie.

```js
console.log(5 === "5"); // false
console.log(5 !== "5"); // true
```

Een gewone voorwaarde:

```js
const stock = 4;

if (stock > 0) {
  console.log("Beschikbaar");
} else {
  console.log("Uitverkocht");
}
```

Logische operatoren:

```js
const canOrder = stock > 0 && isActive;
const needsAttention = stock === 0 || !isActive;
```

| Operator | Betekenis |   |    |
| -------- | --------- | - | -- |
| `&&`     | en        |   |    |
| `        |           | ` | of |
| `!`      | niet      |   |    |

Bij een korte keuze tussen twee waarden kun je een ternary gebruiken:

```js
const label = stock > 0 ? "Beschikbaar" : "Uitverkocht";
```

Gebruik gewone `if`-blokken wanneer de logica uitgebreider wordt.

## 3.4 Truthy en falsy

JavaScript kan waarden in een voorwaarde behandelen alsof ze `true` of `false` zijn.

Veelvoorkomende falsy waarden:

```js
false
0
""
null
undefined
NaN
```

Een lege array en een leeg object zijn **truthy**:

```js
if ([]) {
  console.log("Dit wordt uitgevoerd.");
}
```

Controleer daarom expliciet of een array items bevat:

```js
const products = [];

if (products.length > 0) {
  console.log("Er zijn producten.");
}
```

## 3.5 Functies: invoer, verwerking en uitvoer

Een functie kan parameters ontvangen en een resultaat teruggeven.

```js
function calculateTotal(price, quantity) {
  return price * quantity;
}

const total = calculateTotal(15, 3);

console.log(total); // 45
```

`return`:

1. geeft een waarde terug;
2. stopt de uitvoering van de functie.

`console.log()` toont een waarde in de console, maar vervangt geen `return`.

```js
function calculateTotal(price, quantity) {
  console.log(price * quantity);
}

const total = calculateTotal(15, 3);

console.log(total); // undefined
```

## 3.6 Arrow functions

Dezelfde functie als arrow function:

```js
const calculateTotal = (price, quantity) => {
  return price * quantity;
};
```

Bij één expressie kan het korter:

```js
const calculateTotal = (price, quantity) => price * quantity;
```

**Met accolades moet je zelf `return` schrijven als je een resultaat wilt teruggeven.**

```js
const double = (number) => {
  return number * 2;
};
```

```js
const double = (number) => number * 2;
```

Deze twee varianten geven hetzelfde resultaat.

## 3.7 Functies doorgeven

Een functie is ook een waarde. Je kunt een functie opslaan in een variabele of doorgeven aan een andere functie.

```js
const greet = () => {
  console.log("Hallo");
};

const action = greet;

action(); // "Hallo"
```

Het verschil:

```js
greet;   // De functie zelf.
greet(); // De functie nu uitvoeren.
```

Een functie die je doorgeeft zodat andere code ze kan uitvoeren, noemen we een **callback**. Je ziet dit zo meteen bij arrays en events.

## Oefening 2 — Bereken een bestelling

Schrijf de functie:

```js
calculateOrderTotal(price, quantity, isMember)
```

Regels:

* Bereken eerst `price * quantity`.
* Leden krijgen `10%` korting.
* Geef het resultaat terug met `return`.
* Je mag uitgaan van geldige numerieke invoer.

Controleer:

```js
console.log(calculateOrderTotal(20, 3, false)); // 60
console.log(calculateOrderTotal(20, 3, true));  // 54
```

Schrijf daarna:

```js
getStockLabel(stock)
```

Verwachte resultaten:

|             Invoer | Resultaat             |
| -----------------: | --------------------- |
|                `0` | `"Uitverkocht"`       |
| `1` tot en met `5` | `"Bijna uitverkocht"` |
|       Meer dan `5` | `"Beschikbaar"`       |

**Extra:** geef `"Ongeldige voorraad"` terug wanneer `stock` negatief is.

---

# 4. Arrays en objecten

In een frontendapplicatie werk je vaak met een array van objecten: producten, gebruikers, berichten of bestellingen.

## 4.1 Objecten

Een object groepeert gegevens die bij elkaar horen.

```js
const product = {
  id: 1,
  name: "Toetsenbord",
  price: 79,
  stock: 12,
};

console.log(product.name);  // "Toetsenbord"
console.log(product.price); // 79
```

Je kunt properties ook via vierkante haakjes lezen. Dit is handig wanneer de propertynaam in een variabele zit.

```js
const field = "price";

console.log(product[field]); // 79
```

Een ontbrekende property geeft `undefined`:

```js
console.log(product.description); // undefined
```

## 4.2 Arrays

Een array bevat een geordende verzameling waarden.

```js
const names = ["Sara", "Amir", "Noor"];

console.log(names[0]);     // "Sara"
console.log(names.length); // 3
```

Arrays beginnen bij index `0`.

Voor de volgende voorbeelden gebruiken we:

```js
const products = [
  { id: 1, name: "Toetsenbord", price: 79, stock: 12 },
  { id: 2, name: "Muis", price: 29, stock: 0 },
  { id: 3, name: "Monitor", price: 249, stock: 5 },
  { id: 4, name: "USB-kabel", price: 12, stock: 30 },
];
```

## 4.3 `map`: elk item omzetten

Gebruik `map` om een nieuwe array te maken waarin elk oorspronkelijk item wordt omgezet.

```js
const names = products.map((product) => product.name);

console.log(names);
// ["Toetsenbord", "Muis", "Monitor", "USB-kabel"]
```

De callback wordt voor elk product uitgevoerd. Wat de callback teruggeeft, komt in de nieuwe array.

```js
const pricesWithTax = products.map((product) => {
  return product.price * 1.21;
});
```

`map` levert evenveel items op als de oorspronkelijke array.

## 4.4 `filter`: meerdere items selecteren

Gebruik `filter` om alleen de items te behouden die aan een voorwaarde voldoen.

```js
const availableProducts = products.filter((product) => {
  return product.stock > 0;
});
```

De callback geeft een boolean terug:

* `true`: behoud het item;
* `false`: sla het item over.

Als geen enkel item voldoet, krijg je een lege array.

## 4.5 `find`: één item zoeken

Gebruik `find` wanneer je het eerste passende item wilt.

```js
const product = products.find((product) => product.id === 3);

console.log(product);
// { id: 3, name: "Monitor", price: 249, stock: 5 }
```

Als niets wordt gevonden, krijg je `undefined`.

```js
const product = products.find((product) => product.id === 99);

if (product === undefined) {
  console.log("Product niet gevonden.");
}
```

## 4.6 `some`: controleren of er een match is

Gebruik `some` wanneer je alleen een ja/nee-antwoord nodig hebt.

```js
const hasSoldOutProducts = products.some((product) => {
  return product.stock === 0;
});

console.log(hasSoldOutProducts); // true
```

## 4.7 `forEach`: iets uitvoeren voor elk item

Gebruik `forEach` wanneer je voor elk item een actie wilt uitvoeren.

```js
products.forEach((product) => {
  console.log(product.name);
});
```

`forEach` geeft geen nieuwe array terug. De teruggegeven waarde is `undefined`.

```js
const result = products.forEach((product) => product.name);

console.log(result); // undefined
```

Wil je een nieuwe array met namen? Gebruik dan `map`.

## 4.8 De juiste methode kiezen

| Je wilt…                           | Methode   | Resultaat           |
| ---------------------------------- | --------- | ------------------- |
| Elk item omzetten                  | `map`     | Nieuwe array        |
| Alle passende items selecteren     | `filter`  | Nieuwe array        |
| Het eerste passende item zoeken    | `find`    | Item of `undefined` |
| Weten of minstens één item voldoet | `some`    | Boolean             |
| Voor elk item een actie uitvoeren  | `forEach` | `undefined`         |

Je kunt methodes combineren:

```js
const availableNames = products
  .filter((product) => product.stock > 0)
  .map((product) => product.name);
```

Hou zo’n combinatie leesbaar. Gebruik tussenvariabelen wanneer meerdere stappen moeilijk te volgen worden.

## Oefening 3 — Verwerk de productlijst

Gebruik de array `products` uit dit hoofdstuk.

Maak:

1. `productNames`: een array met alleen de productnamen.
2. `availableProducts`: alle producten met voorraad.
3. `affordableProducts`: alle producten onder `€50`.
4. `selectedProduct`: het product met `id` gelijk aan `3`.
5. `hasSoldOutProducts`: een boolean die aangeeft of er een uitverkocht product is.
6. `availableLabels`: een array met teksten voor alle beschikbare producten.

Verwachte inhoud van `availableLabels`:

```js
[
  "Toetsenbord: €79",
  "Monitor: €249",
  "USB-kabel: €12",
]
```

Zoek ten slotte het product met `id` gelijk aan `99`. Toon `"Product niet gevonden"` als het niet bestaat.

**Extra:** schrijf `searchProducts(products, searchTerm)`. Geef alle producten terug waarvan de naam de zoektekst bevat. Maak de zoekopdracht hoofdletterongevoelig.

---

# 5. Moderne JavaScript en immutable updates

## 5.1 Template literals

Met backticks kun je waarden rechtstreeks in tekst opnemen:

```js
const name = "Sara";
const score = 16;

const message = `${name} behaalde ${score}/20.`;
```

Binnen `${...}` kan ook een expressie staan:

```js
const message = `Totaal: €${price * quantity}`;
```

## 5.2 Destructuring

Met destructuring haal je waarden uit een object:

```js
const product = {
  id: 1,
  name: "Toetsenbord",
  price: 79,
};

const { name, price } = product;

console.log(name);
console.log(price);
```

Je kunt een andere variabelenaam kiezen:

```js
const { name: productName } = product;
```

Je kunt ook een standaardwaarde gebruiken:

```js
const { stock = 0 } = product;
```

Die standaardwaarde wordt gebruikt wanneer de property ontbreekt of `undefined` is. Ze vervangt geen `null`.

Destructuring kan rechtstreeks in functieparameters:

```js
const getProductLabel = ({ name, price }) => {
  return `${name}: €${price}`;
};

console.log(getProductLabel(product));
```

Ook arrays ondersteunen destructuring:

```js
const coordinates = [50.8, 3.3];
const [latitude, longitude] = coordinates;
```

Bij arrays bepaalt de **positie** welke waarde je krijgt. Bij objecten bepaalt de **propertynaam** dat.

## 5.3 Spread bij objecten

De spread-syntax `...` kopieert properties naar een nieuw object:

```js
const product = {
  id: 1,
  name: "Toetsenbord",
  price: 79,
};

const updatedProduct = {
  ...product,
  price: 69,
};
```

`product.price` blijft `79`. `updatedProduct.price` is `69`.

De volgorde is belangrijk. Een latere property overschrijft een eerdere:

```js
const updatedProduct = {
  price: 69,
  ...product,
};

console.log(updatedProduct.price); // 79
```

## 5.4 Spread bij arrays

```js
const numbers = [1, 2, 3];

const extendedNumbers = [...numbers, 4];
```

De oorspronkelijke array blijft behouden:

```js
console.log(numbers);         // [1, 2, 3]
console.log(extendedNumbers); // [1, 2, 3, 4]
```

## 5.5 Referenties en mutatie

Twee variabelen kunnen naar hetzelfde object verwijzen:

```js
const original = {
  name: "Sara",
};

const copy = original;

copy.name = "Noor";

console.log(original.name); // "Noor"
```

`copy = original` maakt geen nieuw object.

Een **mutatie** wijzigt bestaande gegevens rechtstreeks:

```js
product.price = 69;
products.push(newProduct);
```

Bij een **immutable update** maak je een nieuwe versie:

```js
const updatedProduct = {
  ...product,
  price: 69,
};

const updatedProducts = [...products, newProduct];
```

Bij React gebruik je deze manier van werken voor state-updates.

### Toevoegen

```js
const updatedProducts = [
  ...products,
  { id: 5, name: "Webcam", price: 59, stock: 8 },
];
```

### Verwijderen

```js
const updatedProducts = products.filter((product) => {
  return product.id !== 2;
});
```

### Eén item aanpassen

```js
const updatedProducts = products.map((product) => {
  if (product.id === 3) {
    return {
      ...product,
      price: 229,
    };
  }

  return product;
});
```

We maken een nieuwe array en een nieuw object voor het aangepaste product. Ongewijzigde objecten mogen behouden blijven.

**Let op:** `map` maakt een nieuwe array, maar voorkomt niet dat je in de callback bestaande objecten wijzigt.

```js
// Vermijd dit wanneer je een immutable update wilt.
const updatedProducts = products.map((product) => {
  product.price = 0;
  return product;
});
```

### Spread maakt een ondiepe kopie

Geneste objecten worden niet automatisch gekopieerd:

```js
const user = {
  name: "Sara",
  address: {
    city: "Kortrijk",
  },
};
```

Om de stad zonder mutatie aan te passen, kopieer je beide niveaus:

```js
const updatedUser = {
  ...user,
  address: {
    ...user.address,
    city: "Gent",
  },
};
```

## 5.6 Optional chaining: `?.`

Soms is een tussenliggende waarde `null` of `undefined`.

```js
const user = {
  name: "Sara",
  address: null,
};
```

Dit veroorzaakt een fout:

```js
console.log(user.address.city);
```

Met optional chaining krijg je in dit geval `undefined`:

```js
console.log(user.address?.city);
```

Gebruik `?.` waar gegevens daadwerkelijk kunnen ontbreken. Het is geen vervanging voor het begrijpen van de datastructuur.

## 5.7 Nullish coalescing: `??`

Met `??` stel je een fallback in voor `null` en `undefined`:

```js
const city = user.address?.city ?? "Onbekend";
```

Het verschil met `||`:

```js
const stock = 0;

console.log(stock || 10); // 10
console.log(stock ?? 10); // 0
```

`||` gebruikt de fallback bij alle falsy waarden. `??` alleen bij `null` en `undefined`.

Dat verschil is belangrijk wanneer `0`, `false` of `""` geldige waarden zijn.

## Oefening 4 — Werk een winkelmandje bij

Gebruik:

```js
const cart = [
  { id: 1, name: "Toetsenbord", price: 79, quantity: 1 },
  { id: 2, name: "Muis", price: 29, quantity: 2 },
];

const customer = {
  name: "Sara",
  address: null,
};
```

Voer elke opdracht uit zonder de oorspronkelijke gegevens te wijzigen:

1. Maak `cartWithMonitor`: voeg een monitor toe met `id: 3`, `price: 249` en `quantity: 1`.
2. Maak `updatedCart`: verander in de oorspronkelijke `cart` de hoeveelheid van de muis naar `3`.
3. Maak `cartWithoutKeyboard`: verwijder het toetsenbord uit de oorspronkelijke `cart`.
4. Haal met destructuring de naam van `customer` op.
5. Lees de stad uit met optional chaining. Gebruik `"Nog niet opgegeven"` als fallback.
6. Controleer met `console.log(cart)` dat de oorspronkelijke array niet veranderd is.

**Extra:** schrijf een herbruikbare functie `updateQuantity(cart, productId, quantity)` die de bijgewerkte array teruggeeft.

---

# 6. Events en modules

## 6.1 Een element selecteren

```html
<button id="greet-button" type="button">Begroet</button>
<p id="message"></p>
```

```js
const button = document.querySelector("#greet-button");
const message = document.querySelector("#message");
```

`querySelector` geeft het eerste passende element terug, of `null` als er geen match is.

## 6.2 Een event listener toevoegen

```js
const handleClick = () => {
  message.textContent = "Hallo!";
};

button.addEventListener("click", handleClick);
```

Je geeft de functie door:

```js
button.addEventListener("click", handleClick);
```

Dit is iets anders dan:

```js
button.addEventListener("click", handleClick());
```

In het tweede geval voer je `handleClick` onmiddellijk uit en geef je het resultaat door.

Je kunt ook rechtstreeks een callback schrijven:

```js
button.addEventListener("click", () => {
  message.textContent = "Hallo!";
});
```

Gebruik `textContent` wanneer je tekst wilt tonen. Die tekst wordt dan niet als HTML geïnterpreteerd.

## 6.3 Een formulier verwerken

```html
<form id="name-form">
  <label for="name">Naam</label>
  <input id="name" name="name" type="text" required />

  <button type="submit">Begroet</button>
</form>

<p id="message" aria-live="polite"></p>
```

```js
const form = document.querySelector("#name-form");
const nameInput = document.querySelector("#name");
const message = document.querySelector("#message");

form.addEventListener("submit", (event) => {
  event.preventDefault();

  const name = nameInput.value.trim();

  if (name === "") {
    message.textContent = "Vul een naam in.";
    return;
  }

  message.textContent = `Hallo, ${name}!`;
});
```

* Het event-object bevat informatie over de gebeurtenis.
* `preventDefault()` voorkomt hier de standaard formulierverzending.
* `.value` leest de invoer.
* `.trim()` verwijdert witruimte aan het begin en einde.
* `aria-live="polite"` maakt wijzigingen in de melding aankondigbaar voor schermlezers.

Luister naar `submit` op het formulier. Zo werkt het ook wanneer de gebruiker met Enter indient.

## 6.4 Modules met `export` en `import`

Je kunt herbruikbare logica in een apart bestand plaatsen.

**`helpers.js`**

```js
export const createGreeting = (name) => {
  return `Hallo, ${name}!`;
};
```

**`app.js`**

```js
import { createGreeting } from "./helpers.js";

console.log(createGreeting("Sara"));
```

Bij deze named export komt de geïmporteerde naam overeen met de geëxporteerde naam.

Gebruik in browsermodules een relatief pad met de bestandsextensie:

```js
import { createGreeting } from "./helpers.js";
```

## Oefening 5 — Formulier met een module

Bouw een formulier met:

* een label en invoerveld voor een productnaam;
* een submitknop;
* een paragraaf voor feedback.

Maak in `helpers.js` de functie:

```js
createProductMessage(name)
```

Deze geeft bijvoorbeeld terug:

```text
Product "Monitor" is toegevoegd.
```

Importeer de functie in `app.js`.

Bij het indienen:

1. Voorkom de standaard formulierverzending.
2. Verwijder witruimte rond de invoer.
3. Toon `"Vul een productnaam in."` wanneer de invoer leeg is.
4. Toon anders de tekst van `createProductMessage`.
5. Maak het invoerveld na een geldige invoer leeg.

---

# 7. Asynchrone JavaScript en API’s

## 7.1 Waarom asynchroon?

Een aanvraag naar een server duurt tijd. JavaScript wacht niet automatisch op het resultaat voordat andere code verdergaat.

Een **Promise** vertegenwoordigt het toekomstige resultaat van een bewerking. Een Promise kan:

* nog bezig zijn: `pending`;
* succesvol afgerond zijn: `fulfilled`;
* mislukt zijn: `rejected`.

Met `async` en `await` kun je dergelijke bewerkingen leesbaar afhandelen.

## 7.2 `async` en `await`

`fetch` verstuurt een HTTP-aanvraag en geeft een Promise terug.

```js
const loadUsers = async () => {
  const response = await fetch(
    "https://jsonplaceholder.typicode.com/users"
  );

  const users = await response.json();

  console.log(users);
};
```

* `async` maakt van de functie een asynchrone functie.
* `await fetch(...)` wacht binnen die functie op de response.
* `await response.json()` leest en verwerkt de responsebody als JSON.

`await` blokkeert niet de volledige browser. Andere gebeurtenissen kunnen nog verwerkt worden terwijl de functie wacht.

Een `async`-functie geeft altijd een Promise terug:

```js
const getNumber = async () => {
  return 42;
};

console.log(getNumber()); // Een Promise.
```

Om de uiteindelijke waarde te gebruiken:

```js
const showNumber = async () => {
  const number = await getNumber();

  console.log(number); // 42
};

showNumber();
```

## 7.3 JSON

JSON is een tekstformaat voor gegevensuitwisseling.

```json
{
  "id": 1,
  "name": "Sara",
  "isActive": true
}
```

JSON lijkt op JavaScript-objectnotatie, maar is niet hetzelfde:

* propertynamen staan tussen dubbele aanhalingstekens;
* strings gebruiken dubbele aanhalingstekens;
* functies en commentaar zijn niet toegestaan.

`response.json()` verwerkt JSON-tekst tot een JavaScriptwaarde, bijvoorbeeld een object of een array.

## 7.4 HTTP-fouten controleren

`fetch` wijst de Promise niet automatisch af bij een HTTP-status zoals `404` of `500`.

Controleer daarom `response.ok`:

```js
const fetchUsers = async () => {
  const response = await fetch(
    "https://jsonplaceholder.typicode.com/users"
  );

  if (!response.ok) {
    throw new Error(`HTTP-fout: ${response.status}`);
  }

  return await response.json();
};
```

`response.ok` is `true` voor HTTP-statuscodes van `200` tot en met `299`.

Met `throw` veroorzaak je een fout die je met `catch` kunt afhandelen.

## 7.5 `try`, `catch` en `finally`

```js
const loadUsers = async () => {
  try {
    const users = await fetchUsers();

    console.log(users);
  } catch (error) {
    console.error("Gebruikers ophalen mislukt:", error);
  } finally {
    console.log("De aanvraag is afgehandeld.");
  }
};
```

| Blok      | Doel                                            |
| --------- | ----------------------------------------------- |
| `try`     | Voer code uit die kan mislukken                 |
| `catch`   | Handel een fout af                              |
| `finally` | Voer opruimcode uit, bij succes én bij een fout |

Een foutmelding in de console helpt de developer. De gebruiker heeft een zichtbare melding op de pagina nodig.

## 7.6 Laden, succes, leeg resultaat en fout

Bij het ophalen van data moet de interface rekening houden met vier situaties:

| Situatie                                            | Wat toon je?                         |
| --------------------------------------------------- | ------------------------------------ |
| De aanvraag loopt                                   | Een laadmelding                      |
| Er zijn resultaten                                  | De gegevens                          |
| De aanvraag is gelukt, maar er zijn geen resultaten | Een melding dat er niets gevonden is |
| De aanvraag mislukt                                 | Een begrijpelijke foutmelding        |

Een lege array is geen fout. De aanvraag kan geslaagd zijn zonder resultaten.

Voorbeeld:

```html
<button id="load-button" type="button">Laad gebruikers</button>
<p id="status" role="status"></p>
```

```js
const loadButton = document.querySelector("#load-button");
const status = document.querySelector("#status");

const loadUsers = async () => {
  loadButton.disabled = true;
  status.textContent = "Gebruikers laden...";

  try {
    const users = await fetchUsers();

    status.textContent =
      users.length === 0
        ? "Geen gebruikers gevonden."
        : `${users.length} gebruikers geladen.`;

    console.log(users);
  } catch (error) {
    status.textContent = "Laden mislukt. Probeer opnieuw.";
    console.error(error);
  } finally {
    loadButton.disabled = false;
  }
};

loadButton.addEventListener("click", loadUsers);
```

De knop wordt ook bij een fout opnieuw ingeschakeld.

## Oefening 6 — Haal gebruikers op

Gebruik:

```text
https://jsonplaceholder.typicode.com/users
```

Maak een knop en een statusmelding.

Bij een klik:

1. Toon `"Gebruikers laden..."`.
2. Schakel de knop tijdelijk uit.
3. Haal de gebruikers op.
4. Controleer `response.ok`.
5. Toon bij succes hoeveel gebruikers geladen zijn.
6. Toon met `map` een array van gebruikersnamen in de console.
7. Toon bij een lege array `"Geen gebruikers gevonden."`.
8. Toon bij een fout een melding op de pagina.
9. Schakel de knop altijd opnieuw in.

Test ook het foutscenario. Zet je browser via de Network-tab tijdelijk op **Offline** en klik opnieuw. Zet de verbinding daarna terug aan.

---

# 8. Geïntegreerde oefening — Doorzoek een gebruikerslijst

Bouw een kleine pagina waarop je gebruikers van een API kunt ophalen en op naam kunt filteren.

Je combineert:

* functies;
* arrays en objecten;
* destructuring;
* template literals;
* events;
* modules;
* `async`/`await`;
* foutafhandeling.

## 8.1 Bestanden

Gebruik:

```text
javascript-herhaling/
├── index.html
├── style.css
├── api.js
└── app.js
```

## 8.2 Startcode: HTML

Vervang je HTML door:

```html
<!doctype html>
<html lang="nl">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Gebruikers zoeken</title>

    <link rel="stylesheet" href="./style.css" />
    <script type="module" src="./app.js"></script>
  </head>

  <body>
    <main class="container">
      <h1>Gebruikers</h1>
      <p>Laad de gebruikers en zoek op naam.</p>

      <div class="toolbar">
        <button id="load-button" type="button">
          Laad gebruikers
        </button>

        <div class="search-field">
          <label for="search">Zoeken op naam</label>
          <input
            id="search"
            name="search"
            type="search"
            placeholder="Bijvoorbeeld: Leanne"
            disabled
          />
        </div>
      </div>

      <p id="status" role="status">
        Klik op de knop om gebruikers te laden.
      </p>

      <ul id="user-list" class="user-list"></ul>
    </main>
  </body>
</html>
```

## 8.3 Startcode: CSS

```css
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  line-height: 1.5;
  color: #1f2937;
  background: #f3f4f6;
}

.container {
  max-width: 900px;
  margin: 0 auto;
  padding: 32px 20px;
}

.toolbar {
  display: flex;
  flex-wrap: wrap;
  align-items: end;
  gap: 16px;
}

.search-field {
  display: flex;
  flex: 1 1 240px;
  flex-direction: column;
  gap: 6px;
}

input,
button {
  padding: 10px 12px;
  font: inherit;
  border: 1px solid #9ca3af;
  border-radius: 6px;
}

button {
  color: white;
  background: #1d4ed8;
  cursor: pointer;
}

button:disabled {
  opacity: 0.6;
  cursor: wait;
}

.user-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 16px;
  padding: 0;
  list-style: none;
}

.user-card {
  padding: 16px;
  background: white;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  overflow-wrap: anywhere;
}

.user-card h2 {
  margin-top: 0;
  font-size: 1.1rem;
}

.user-card p {
  margin-bottom: 0;
}
```

## 8.4 Startcode: API-module

**`api.js`**

```js
export const fetchUsers = async () => {
  // 1. Haal de gebruikers op.
  // 2. Controleer response.ok.
  // 3. Geef de verwerkte JSON-data terug.
};
```

## 8.5 Startcode: applicatie

De functie die één kaart maakt, is al voorzien. Focus op de gegevensverwerking.

**`app.js`**

```js
import { fetchUsers } from "./api.js";

const loadButton = document.querySelector("#load-button");
const searchInput = document.querySelector("#search");
const status = document.querySelector("#status");
const userList = document.querySelector("#user-list");

let users = [];

const createUserCard = (user) => {
  const { name, email } = user;
  const city = user.address?.city ?? "Onbekend";

  const item = document.createElement("li");
  item.className = "user-card";

  const heading = document.createElement("h2");
  heading.textContent = name;

  const emailText = document.createElement("p");
  emailText.textContent = email;

  const cityText = document.createElement("p");
  cityText.textContent = `Stad: ${city}`;

  item.append(heading, emailText, cityText);

  return item;
};

const renderUsers = (visibleUsers) => {
  // Maak met map voor elke gebruiker een kaart.
  // Vervang de inhoud van userList met deze kaarten.
  // Toon het aantal resultaten of een melding bij nul resultaten.
};

const applyFilter = () => {
  // Lees de zoektekst.
  // Filter de volledige users-array op naam.
  // Geef de gefilterde array door aan renderUsers.
};

const loadUsers = async () => {
  // Toon een laadstatus.
  // Schakel de knop en het zoekveld tijdelijk uit.
  // Wis vorige resultaten.
  // Haal de gebruikers op en bewaar ze in users.
  // Pas het huidige filter toe.
  // Handel fouten af.
  // Schakel de laadknop altijd opnieuw in.
};

loadButton.addEventListener("click", loadUsers);
searchInput.addEventListener("input", applyFilter);
```

## 8.6 Vereisten

### Gegevens ophalen

* Haal gebruikers op bij een klik op de knop.
* Bewaar de volledige opgehaalde array in `users`.
* Toon tijdens het laden een melding.
* Voorkom een tweede klik zolang de aanvraag loopt.
* Maak zoeken beschikbaar na een succesvolle aanvraag.

### Gegevens tonen

Toon per gebruiker:

* naam;
* e-mailadres;
* stad, met een fallback wanneer die ontbreekt.

Gebruik de voorziene functie `createUserCard`.

Je kunt de lijst vervangen met:

```js
userList.replaceChildren(...cards);
```

Hier verspreidt `...cards` de array over de argumenten van `replaceChildren`.

### Zoeken

* Filter terwijl de gebruiker typt.
* Zoek hoofdletterongevoelig.
* Negeer witruimte aan het begin en einde van de zoektekst.
* Toon alle gebruikers wanneer de zoektekst leeg is.
* Toon `"Geen gebruikers gevonden."` bij nul matches.

**Bewaar altijd de volledige lijst.** Als je `users` telkens overschrijft met de gefilterde resultaten, kun je de verdwenen gebruikers niet terugvinden wanneer de zoektekst verandert.

### Fouten

* Toon een begrijpelijke foutmelding.
* Laat bij een mislukte nieuwe aanvraag geen oude kaarten staan.
* Maak een nieuwe poging mogelijk.

## 8.7 Zelf controleren

Controleer deze situaties:

* De gebruikers verschijnen na een klik.
* Zoeken met hoofdletters geeft dezelfde matches als zoeken met kleine letters.
* Een onbestaande naam geeft een lege-resultaatmelding.
* Het leegmaken van de zoektekst toont alle gebruikers.
* Bij een netwerkfout verschijnt een foutmelding.
* Na de fout kun je opnieuw laden.

**Extra:** laat het zoekveld zowel op naam als op e-mailadres zoeken.

---

# 9. Eindcheck

Beantwoord zonder terug te kijken:

1. Wanneer gebruik je `let` in plaats van `const`?

2. Waarom geeft onderstaande functie `undefined` terug?

   ```js
   const add = (a, b) => {
     a + b;
   };
   ```

3. Welke methode gebruik je voor alle beschikbare producten? Welke voor één product met een bepaald ID?

4. Wat geeft `find` terug als er geen match is?

5. Waarom maakt `const copy = user` geen onafhankelijk object?

6. Schrijf een immutable update waarmee je `price` op `50` zet.

7. Wat is het verschil tussen `value || 10` en `value ?? 10`?

8. Waarom schrijf je `handleClick` en niet `handleClick()` als je een bestaande functie als event handler doorgeeft?

9. Waarom controleer je `response.ok`?

10. Welke vier situaties moet je interface bij het ophalen van data kunnen tonen?
