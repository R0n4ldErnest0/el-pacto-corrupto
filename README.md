# El Pacto Corrupto del Perú 🎮

[Español](#español) · [English](#english)

🔗 **Jugar / Play:** https://r0n4ldernest0.github.io/el-pacto-corrupto/

> **Resumen.** Un fan game de sátira política: un *ROM hack* de Pokémon Rojo en
> el que, en lugar de la Liga Pokémon, enfrentas a cinco de los políticos más
> cuestionados de la historia del Perú. Se juega directo en el navegador, en PC o
> celular, sin instalar nada. Nació en el contexto de las elecciones del 2026.
>
> **Summary.** A political-satire fan game: a Pokémon Red *ROM hack* where,
> instead of the Pokémon League, you battle five of the most controversial
> politicians in Peru's history. It runs straight in the browser, on PC or phone,
> with nothing to install. It was made in the context of Peru's 2026 elections.

---

## Español

### ¿De qué trata?
Al empezar una partida nueva pasas por la intro normal del juego (Profesor Oak,
nombre del personaje, tu cuarto). Al salir de casa, en vez de Pueblo Paleta,
entras directamente a **El Pacto Corrupto**. En el pasillo, cada NPC te entrega
un Pokémon y el testimonio del crimen del siguiente rival. Luego enfrentas uno
por uno, al estilo del Alto Mando, a:

| Rival | Tema |
|---|---|
| Alan García | Corrupción y deuda externa |
| Vladimiro Montesinos | Espionaje y narcotráfico |
| Alejandro Toledo | Sobornos y lavado de activos |
| Alberto Fujimori | Autoritarismo y crímenes de Estado |
| Keiko Fujimori | **Jefa final**: financiamiento ilegal (con la música del Campeón) |

Los seis Pokémon iniciales tienen niveles progresivos (de Charizard nv. 63 a
Snorlax nv. 68) para que las peleas estén balanceadas.

**Controles:** flechas para moverte, `Z` = A, `X` = B, `Enter` = Start. En el
celular aparece un gamepad táctil.

### ¿Cómo funciona técnicamente?
Este repositorio es el **sitio web** del juego, servido con GitHub Pages. El ROM
se compiló aparte a partir del desensamblaje de código abierto
[pret/pokered](https://github.com/pret/pokered) con [RGBDS](https://rgbds.gbdev.io/)
(mapas, diálogos, entrenadores y equipos modificados).

- **Página estática** (`index.html` + `style.css`), sin framework ni build.
- **Bilingüe ES/EN**: cada texto tiene sus atributos `data-es` y `data-en`, y el
  botón del menú los intercambia con un pequeño script.
- **Emulador en el navegador**: [EmulatorJS](https://emulatorjs.org/) con el core
  **mGBA** compilado a WebAssembly, alojado localmente en `lib/` (así no depende
  de un CDN). Se configura con:
  ```js
  EJS_player = '#game'; EJS_core = 'mgba';
  EJS_gameUrl = 'pokered_corrupt.gbc'; EJS_pathtodata = './lib/data/';
  EJS_language = 'es'; EJS_startOnLoaded = true;
  ```
- **Parche `.bps`**: la sección de descarga explica cómo aplicar el parche a una
  copia propia de Pokémon Red (USA/Europe) con
  [Floating IPS](https://github.com/Alcaro/Flips).

### Estructura
```
index.html            Página: contexto, sobre el juego, emulador, descarga, autor
style.css             Estilos (tema oscuro rojo/dorado)
pokered_corrupt.gbc   ROM de la demo que carga el emulador
lib/
  cores/              Cores mGBA en WebAssembly
  data/               Loader de EmulatorJS, gamepad táctil, shaders, traducciones
```

### Ejecutar localmente
El emulador necesita servirse por HTTP (no funciona abriendo el archivo con
`file://`):
```bash
python -m http.server 8000
# abre http://localhost:8000
```

### Aviso
Proyecto de fan y de sátira política **sin fines de lucro**, no afiliado a
Nintendo ni a Game Freak. Para el parche completo se requiere una copia legítima
de Pokémon Rojo.

---

## English

### What is it?
When you start a new game you go through the normal intro (Professor Oak,
naming your character, your bedroom). When you step outside, instead of Pallet
Town you go straight into **The Corrupt Pact**. In the hallway, each NPC hands
you a Pokémon plus testimony about the next rival's crimes. Then you face them
one by one, Elite Four-style:

| Rival | Theme |
|---|---|
| Alan García | Corruption and foreign debt |
| Vladimiro Montesinos | Espionage and drug trafficking |
| Alejandro Toledo | Bribery and money laundering |
| Alberto Fujimori | Authoritarianism and crimes of State |
| Keiko Fujimori | **Final boss**: illegal campaign financing (with the Champion theme) |

The six starter Pokémon have progressive levels (Charizard lv 63 up to Snorlax
lv 68) so the battles stay balanced.

**Controls:** arrow keys to move, `Z` = A, `X` = B, `Enter` = Start. A touch
gamepad shows up on phones.

### How does it work?
This repository is the game's **website**, served with GitHub Pages. The ROM
was built separately from the open-source [pret/pokered](https://github.com/pret/pokered)
disassembly with [RGBDS](https://rgbds.gbdev.io/), with modified maps, dialogue,
trainers and teams.

- **Static page** (`index.html` + `style.css`), with no framework and no build step.
- **Bilingual ES/EN**: every text carries `data-es` and `data-en` attributes, and
  the menu button swaps them with a small script.
- **In-browser emulator**: [EmulatorJS](https://emulatorjs.org/) running the
  **mGBA** core compiled to WebAssembly, hosted locally under `lib/` so it doesn't
  depend on a CDN. See the configuration snippet in the Spanish section above.
- **`.bps` patch**: the download section explains how to apply the patch to your
  own copy of Pokémon Red (USA/Europe) with [Floating IPS](https://github.com/Alcaro/Flips).

### Structure
```
index.html            Page: context, about, emulator, download, author
style.css             Styles (dark red/gold theme)
pokered_corrupt.gbc   Demo ROM loaded by the emulator
lib/
  cores/              mGBA WebAssembly cores
  data/               EmulatorJS loader, touch gamepad, shaders, translations
```

### Run locally
The emulator must be served over HTTP (opening the file via `file://` won't work):
```bash
python -m http.server 8000
# open http://localhost:8000
```

### Disclaimer
**Non-profit** fan project and political satire, not affiliated with Nintendo or
Game Freak. A legitimate copy of Pokémon Red is required for the full patch.

---

Hecho por / Made by **Ronald Ernesto** · [LinkedIn](https://www.linkedin.com/in/ronald-ernesto-soto-nicoll/)
