# Model Tone Index (MTI)

A universal standard for defining, measuring, and communicating the behavioral "tone" of an AI model — modeled directly after the HSLA color system. The tone of any model is expressed as an 8-character hex code (e.g. `#38BDF8CC`).

> Originated September 2025, prototyped in Gemini Canvas.

## The Problem

The AI industry lacks a standardized, measurable way to describe AI behavior. Terms like "creative," "analytical," or "safe" are subjective and ambiguous. Two teams can mean wildly different things by "professional tone."

## The Solution

MTI encodes four orthogonal behavioral axes into a single hex string. It's a spec, not a vibe.

## Data Model (HSLA Mapping)

| Axis | HSLA Channel | Range | Meaning |
|---|---|---|---|
| **Archetype** | Hue (h) | 0° – 359° | Core functional behavior |
| **Persona** | Saturation (s) | 20% – 80% | Stylistic voice intensity |
| **Rigor** | Lightness (l) | 20% – 80% | Adherence to facts vs. creative liberty |
| **Verbosity** | Alpha (a) | 10% – 90% | Length and detail of output |

### Archetype Wheel

| Hue | Archetype |
|---|---|
| 0° | Creator |
| 45° | Entertainer |
| 90° | Analyst |
| 135° | Scholar |
| 180° | Tutor |
| 225° | Coder |
| 270° | Assistant |
| 315° | Strategist |

### Axis Bands

- **Persona**: Stoic (low) → Professional → Expressive (high)
- **Rigor**: Grounded (low) → Balanced → Unconstrained (high)
- **Verbosity**: Concise (low) → Balanced → Verbose (high)

## The App

`index.html` is a single-file, zero-build web app that:

1. Lets you adjust the four MTI axes with a hue wheel and three sliders.
2. Shows the live hex code and a generated tone name (e.g. "Grounded Professional Analyst").
3. Includes a gallery of preset official tones.
4. Integrates with the Gemini API for three tools:
   - **Test a Tone** — Gemini writes a sample paragraph in the selected tone.
   - **Describe a Tone** — describe the AI personality you want; Gemini maps it to MTI.
   - **Analyze Text** — paste AI output; Gemini reverse-engineers the MTI profile.

## Running It

No build step. Just open the file:

```bash
open index.html   # macOS
# or just double-click in Finder/Explorer
```

## Gemini API Key

The Gemini features will not work until you add your own API key. Open `index.html` and find:

```js
const apiKey = "YOUR_GEMINI_API_KEY_HERE";
```

Replace it with your key from https://aistudio.google.com/apikey.

**Do not commit your real key to a public repo.** For anything more than local tinkering, move the key out of the client and proxy through a backend.

## Roadmap

- Move the API key out of the client (server proxy or build-time injection).
- Publish an MTI JSON schema so other tools can consume tone codes.
- Build a benchmark: pair MTI codes with prompts and score model outputs against the spec.
- Expand the archetype wheel beyond the current 8 anchors.

## License

MIT. See `LICENSE`.
