# NomenLab — IUPAC Nomenclature Trainer

A randomised practice app for CBSE Class 12 Chemistry nomenclature: it draws a
skeletal structure, you name it, and it tells you exactly what's wrong when
you're wrong.

## How to open it

No install, no build step, no server needed.

1. Unzip this folder.
2. Double-click **`index.html`** (or right-click → Open with → your browser).

That's it — it runs entirely in the browser. An internet connection is only
used to load the Spectral/Inter/JetBrains Mono fonts from Google Fonts; if
you're offline it'll still work, just with your system's default fonts
instead.

Because it's a plain static site, you can also drag the whole folder onto
Netlify Drop, GitHub Pages, or any static host if you ever want a shareable
link instead of a local file.

## What's inside

```
index.html        entry point — open this
app.js            the whole app, pre-bundled (React + the code below, minified)
tailwind.css      pre-compiled styles (no Tailwind build step needed)
source/App.jsx    the original React source, for reference or editing
```

## What it covers

Four CBSE Class 12 organic chemistry chapters:

- **Haloalkanes & Haloarenes** — halogen prefixes, lowest-locant numbering, alphabetical tie-breaks
- **Alcohols, Phenols & Ethers** — the `-ol` suffix, the retained name "phenol", alkoxyalkane naming
- **Aldehydes, Ketones & Carboxylic Acids** — `-al`, `-one`, `-oic acid`, and why some locants get dropped
- **Amines** — primary/secondary/tertiary, and the `N-` prefix convention

Each chapter has three difficulty tiers (chain length and number of
substituents scale up), and every structure is generated fresh — the name is
built first, then the picture is drawn to match it, so the "correct answer"
is always well-defined.

**Learn** mode walks through the rules chapter by chapter with worked
examples and a couple of check-your-understanding questions built in.
**Practice** mode gives immediate, specific feedback on every wrong answer
(wrong chain length vs. wrong functional group vs. wrong locants vs. wrong
substituent vs. just alphabetical-order/punctuation — it tells you which).
**Test** mode holds all feedback until you finish, then shows a full
breakdown: score by chapter, a tally of which *kind* of mistake you made
most, and every question with your answer next to the correct one.

## Editing it

`source/App.jsx` is the real source — everything else in this folder is
generated from it. If you want to change something:

1. `npm install react react-dom lucide-react esbuild tailwindcss@3`
2. Edit `source/App.jsx`
3. Rebuild the JS: `npx esbuild source/App.jsx --bundle --jsx=automatic --minify --outfile=app.js` (after adding a small `main.jsx` that mounts `<App />` into `#root` — see the note at the top of `App.jsx` if you add one)
4. Rebuild the CSS: `npx tailwindcss -i <a tailwind input file with the @tailwind directives> -o tailwind.css --minify --content "./source/**/*.jsx"`

Everything — the random-molecule generator, the IUPAC name builder, the
skeletal-structure SVG renderer, the answer checker, and all four lessons —
lives in that one file, organised top to bottom in that order.

AI Disclosure

This project was developed with the assistance of AI tools, particularly Claude.

AI was used to help generate and structure parts of the application's code, UI, and implementation. I directed the project, defined the educational goal and requirements, tested the application, reviewed the generated code, and iterated on the result.

I am intentionally disclosing the use of AI because I believe it is important to distinguish between using AI as a development tool and claiming that all code was written manually.

The project is also an opportunity for me and other students to learn about nomenclature of organic compounds.
