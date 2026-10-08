# Pixel Dissolve

A pixel dissolve from light into dark, from [miguelclavel.com](https://miguelclavel.com/?utm_source=github&utm_medium=pixel-dissolve).

<img src="assets/demo.gif" width="720" alt="A pixel dissolve from light into dark: a screen recording">

**[Try it live](https://miguelclavel.github.io/pixel-dissolve/)** · one file, `index.html`, no libraries, no build step.

The light half of my site breaks into squares and the dark half comes through underneath.

It's my favourite thing on the page and it took four tries.

The section under my hero runs in the opposite tone. Light page, dark section, and the reverse when you switch themes. Two tones meeting needs a handover or it just looks like a mistake. So I built the handover.

Here's how it works.

A solid sheet in the colour you're leaving covers the screen, over a grid of 24 pixel squares. Every square gets a threshold. Two thirds of it comes from its row, lowest at the bottom, so the sweep travels upward. The last third is random noise.

As you scroll, one number climbs from 0 to 1. Any square under that number gets repainted in the colour that's arriving.

That mix is the whole effect. All order and it's a window blind. All noise and it's television static. The blend reads like something coming apart.

Squares that just flipped, and only those, can fire in an accent colour first. That's the colour you see running along the leading edge.

Three things went wrong.

I drove it from the hero's scroll progress at first. It finished while the section it was uncovering was still 850 pixels below the fold, so the sheet came apart to reveal the same hero again.

It also needed its own scroll listener. The hero's animation loop stops once the hero leaves the screen, which is exactly when this still has work to do.

Then in dark mode the sheet flashed white. I was reading the page colours off the root element, but they're declared on a wrapper further in.

Change the one third to a half and watch it turn into static. That's the fun part.

## Use it on your site

Give the two sections their colours as a CSS variable (`--page`) and the ids `from` and `to`, then copy the `.wipe` canvas and the script from `index.html`. Tune `STEP` (square size) and `NOISE` (how random it is: one third reads like coming apart, a half turns into static). It stays off for people who prefer reduced motion.

## Or build your own from the prompt

Copy it as it is and paste it into Claude, or any AI coding tool.

```text
As the user scrolls from one section into the next, cover the screen with a canvas filled in the colour they are leaving, over a grid of 24 pixel squares. Give every square a threshold: two thirds from its row so the lowest rows open first, one third random. Turn scroll position into a value from 0 to 1 based on the section being uncovered, not the one being left. Repaint every square under that value in the arriving colour. Give squares that just flipped a small chance of painting an accent colour first. Read the colours from the themed wrapper, not the root, so it works in both themes.
```

More like this in [interaction-recipes](https://github.com/miguelclavel/interaction-recipes).

---

MIT licensed. Made by [Miguel Clavel](https://miguelclavel.com/?utm_source=github&utm_medium=pixel-dissolve) with Claude Code. If you build one of these, send it to me. I'd genuinely like to see it.
