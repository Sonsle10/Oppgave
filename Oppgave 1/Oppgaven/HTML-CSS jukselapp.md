# Jukselapp HTML & CSS

Alt det viktigste på én side. Slå opp her først, spør etterpå.

---
## 1. Skjelettet

Skriv `!` i en tom `.html`-fil og trykk **Tab**.

Høyreklikk i fila → **Open with Live Server**. Siden oppdaterer seg når du lagrer.

---
## 2. HTML — innhold og struktur

| Tagg | Hva den gjør |
|---|---|
| `<h1>`–`<h6>` | Overskrifter. **Bare én `<h1>`** per side |
| `<p>` | Avsnitt |
| `<strong>` `<em>` | Viktig / uthevet |
| `<ul>` `<ol>` `<li>` | Punktliste / nummerert liste, `<li>` = ett punkt |
| `<a href="...">` | Lenke. `target="_blank"` = ny fane |
| `<img src="..." alt="...">` | Bilde. `alt` er **ikke valgfritt** |
| `<!-- ... -->` | Kommentar (vises ikke) |

### Boksene du bygger siden av

| Tagg | Hva den betyr |
|---|---|
| `<header>` | Toppen: tittel og meny |
| `<nav>` | Menyen med lenker |
| `<main>` | Hovedinnholdet — én per side |
| `<section>` | En avgrenset del av innholdet, med `id` |
| `<article>` | Noe som står på egne bein, f.eks. et kort |
| `<footer>` | Nederst: kreditering, årstall, kilder |
| `<div>` | **Tom boks uten betydning.** Brukes bare til å samle noe du vil styre med CSS — når ingen av taggene over passer |
| `<span>` | Samme som `<div>`, men for en bit tekst **inne i** et avsnitt |

En `<div>` ser ikke ut som noe og betyr ikke noe for Google eller skjermlesere. Den er et gripehåndtak for CSS.

Filstier: `bilder/katt.jpg` = mappa ved siden av fila. `../` = ett nivå opp.

---
## 3. CSS — utseende

Tre selektorer:

```css
p { }          /* alle <p> */
.klasse { }    /* alt med class="klasse"  — kan brukes mange ganger */
#id { }        /* det ene med id="id"     — bare én gang per side */
```

### Farger og tekst

```css
body {
	background-color: #ffffff;
	color: #222222;
	font-family: Arial, Helvetica, sans-serif;
	line-height: 1.6;
}
```

Hex: `#RRGGBB`. `1rem` = 16px. Kommentar: `/* slik */`
Ellers: `font-size`, `font-weight`, `text-align`

### Boksmodellen

**padding = luft innenfor ramma. margin = luft utenfor.**

```css
* { box-sizing: border-box; }   /* sett denne alltid, øverst */

.kort {
	padding: 20px;              /* 10px 20px = topp/bunn, venstre/høyre */
	border: 1px solid #dddddd;
	border-radius: 8px;
	margin-bottom: 16px;
}
```

### Plassering

```css
main {
	max-width: 800px;
	margin: 0 auto;         /* midtstiller — krever max-width */
}

nav a {
	display: inline-block;  /* nå virker padding opp/ned */
	padding: 8px 12px;
	text-decoration: none;  /* fjerner understreken */
}

nav a:hover { background-color: #eeeeee; }
```

### Flexbox

`display: flex` settes på **boksen rundt**, ikke på tingene som skal flyttes.

```css
header {
	display: flex;
	justify-content: space-between;  /* langs raden */
	align-items: center;             /* på tvers */
	gap: 16px;                       /* avstand mellom barna */
}

.kortrad { display: flex; flex-wrap: wrap; gap: 16px; }
.kortrad .kort { flex: 1 1 250px; }   /* voks, krymp, ønsker 250px */
```

`justify-content`: `flex-start`, `center`, `flex-end`, `space-between`
`flex-wrap: wrap` = bryt til ny linje i stedet for å klemme sammen.

### Responsivt

```css
img { max-width: 100%; height: auto; }

/* Nederst i fila! Det som står sist vinner. */
@media (max-width: 600px) {
	header, nav { flex-direction: column; gap: 12px; }
	h1 { font-size: 1.8rem; }
}
```

Test med **F12 → Ctrl+Shift+M**. Bruk `max-width` og `flex-wrap` i stedet for faste px-bredder.

### Flere sider, samme stil

Alle sidene peker på samme `style.css`. Endrer du fargen der, endres den overalt. Gi hver side sin egen `<title>`.

---
## 4. Står du fast?

| Symptom | Årsak |
|---|---|
| Siden ser helt rar ut | En tagg er ikke lukket |
| Bildet vises ikke | Feil filnavn eller sti — store/små bokstaver teller! |
| CSS-en gjør ingenting | Feil navn i `<link>`, eller `<link>` ligger ikke i `<head>` |
| Én CSS-regel virker ikke | Mangler `.` foran klassenavn, eller `;` etter linja |
| Flexbox flytter ingenting | `display: flex` står på feil element — det skal på boksen **rundt** |
| Ødelagt på mobil | Faste px-bredder, eller viewport-taggen mangler |

**Trykk F12 og se i Elements-fanen før du spør.**

---
## 5. Sjekkliste før levering

- [ ] `lang="no"` på `<html>`
- [ ] `<meta charset="UTF-8">` — ellers blir æ, ø og å ødelagt
- [ ] `<meta name="viewport">`
- [ ] En `<title>` som beskriver siden
- [ ] Nøyaktig én `<h1>`
- [ ] `alt`-tekst på alle bilder
- [ ] Alle lenker virker (prøv dem)
- [ ] Ser bra ut i device toolbar (**Ctrl+Shift+M**)
- [ ] Formatert med Prettier (**Shift+Alt+F**)
- [ ] Ingen feil på [validator.w3.org](https://validator.w3.org/#validate_by_input)
- [ ] Committet og pushet til GitHub
