# React Motion Starter

Ein lokales Website-Grundgerüst mit **React**, **TypeScript**, **Vite** und **Motion for React** (ehemals Framer Motion). Kein Backend erforderlich.

## Starten

Voraussetzung: Node.js **22.12 oder neuer**.

```sh
npm install
npm run dev
```

Öffne die im Terminal angezeigte URL, standardmäßig `http://localhost:5173`.

```sh
npm run typecheck # TypeScript prüfen
npm run build     # TypeScript prüfen und Produktionsbuild in dist/ erzeugen
npm run preview   # Produktionsbuild lokal ansehen
```

Mit der mitgelieferten `package-lock.json` kannst du für reproduzierbare Installationen auch `npm ci` verwenden.

## Projektaufbau

```text
src/
├── main.tsx                      # React-Start und globale Motion-Konfiguration
├── App.tsx                       # Demo-Seite mit interaktiven Beispielen
├── styles.css                    # Farben, Layout und responsive Breakpoints
├── components/
│   ├── AnimatedButton.tsx         # Hover- und Tap-Animationen
│   └── Reveal.tsx                 # Einmaliges Einblenden beim Scrollen
└── lib/
    └── animations.ts             # Gemeinsame Transitions und Stagger-Varianten
```

## Eigene Inhalte animieren

```tsx
import { Reveal } from './components/Reveal'
import { AnimatedButton } from './components/AnimatedButton'

export function MySection() {
  return (
    <Reveal delay={0.1}>
      <h2>Deine nächste Idee</h2>
      <AnimatedButton onClick={() => console.log('Los geht’s')}>Los geht’s</AnimatedButton>
    </Reveal>
  )
}
```

Weitere Elemente animierst du mit `motion.div`, `motion.section` usw.:

```tsx
import { AnimatePresence, motion } from 'motion/react'

export function Notice({ visible }: { visible: boolean }) {
  return (
    <AnimatePresence>
      {visible && (
        <motion.div
          key="notice"
          initial={{ opacity: 0, y: 16 }}
          animate={{ opacity: 1, y: 0 }}
          exit={{ opacity: 0, y: -16 }}
        >
          Hallo, Animation!
        </motion.div>
      )}
    </AnimatePresence>
  )
}
```

`AnimatePresence` bleibt gemountet, während das darin enthaltene Element ein- und ausgeblendet wird. So kann Motion die Exit-Animation abspielen.

## Anpassen

- Inhalte und Beispielsektionen: `src/App.tsx`.
- Farben und Schriften: Variablen am Anfang von `src/styles.css`.
- Geschwindigkeit und Spring-Verhalten: `src/lib/animations.ts`.
- Titel, Sprache und Beschreibung: `index.html`.

`MotionConfig reducedMotion="user"` respektiert die Systemeinstellung für reduzierte Bewegung. CSS deaktiviert zusätzlich sanftes Scrollen und CSS-Transitions bei dieser Einstellung.

Die Demo lädt DM Sans und Manrope über Google Fonts. Ohne Netzwerk werden lokale Ersatzschriften verwendet. Entferne die `@import`-Zeile in `src/styles.css`, wenn du keine externen Schriften laden möchtest.

## Dokumentation

- [React](https://react.dev/)
- [Motion for React](https://motion.dev/docs/react)
- [Vite](https://vite.dev/guide/)
# LearningGo
