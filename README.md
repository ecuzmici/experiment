# 🌱 seedsong

*a garden that sings*

**Play it now: https://ecuzmici.github.io/experiment/**

(also mirrored as a [Claude artifact](https://claude.ai/code/artifact/45ff353d-dc5b-4f7a-b42a-c1a96e833ede) —
but the GitHub Pages link above is the full experience, including shareable
garden URLs)

<p align="center">
  <img src="shots/golden-hour.png" width="45%" alt="Seedsong at golden hour — glowing flowers under a violet sky">
  <img src="shots/night.png" width="45%" alt="Seedsong at night — crescent moon, stars, and fireflies among the blooms">
</p>
<p align="center">
  <img src="shots/rain.png" width="45%" alt="Rain falling over the luminous garden">
  <img src="shots/aurora.png" width="45%" alt="An aurora night over the meadow">
</p>

## 🌍 The Commons

Tap the globe button (or open
[`#commons`](https://ecuzmici.github.io/experiment/#commons)) to step into
**the commons** — a single garden shared by everyone in the world. Every seed
planted there is planted for everyone; stand still for a minute and you may
watch a stranger's flower sprout in front of you. Tap it to see when a
wanderer left it there. The meadow keeps its five thousand newest seeds.

(Backed by a free Supabase table with insert-and-look-only row security — no
accounts, no names, just seeds.)

> **Note on the API key in `index.html`:** that is Supabase's *publishable*
> anon key, which is designed to ship in client-side code — every visitor's
> browser receives it either way. All safety lives in Postgres Row Level
> Security: the anon role can insert a seed (range-checked) and read seeds,
> nothing else. The service key is not in this repo. Supabase's security
> advisors report zero findings on this project.

## A living world

- **Weather.** Sometimes it rains. The sky hushes, the sun hides, rain
  patters into the soundscape, and every plant grows lush and fast — plants
  love rain. In a storm, distant thunder rolls under the music.
- **Pollinators & evolution.** Butterflies work the garden by day, pale moths
  by night, carrying pollen bloom to bloom. A seed that lands between two
  flowers becomes their **hybrid child** — mixed genes, small mutations — and
  its field-guide card shows the lineage. Pollinated plants occasionally cast
  seeds of their own: leave the garden alone and it gardens itself.
- **Aurora nights.** Some nights, if you're lucky, curtains of light.
- **Living harmony.** The drone underneath now breathes through a slow chord
  progression, so the flowers' notes form real harmony that never resolves
  quite the same way. At dawn, a songbird may land on your tallest flower and
  answer the garden.
- **Postcards.** The camera button presses the current moment into a
  1080×1350 postcard — stamped with your garden's generated name — and hands
  it to your phone's share sheet.

Touch the ground and a seed takes root. Every plant that grows is a
one-of-a-kind species — its shape, colors, bloom, and voice are all grown from
a single random number. Every bloom is an instrument: each plant is assigned
notes from the garden's own musical scale and chimes them into an endless,
ever-changing ambient song that never plays the same way twice.

Stay a while. The sun sets, the stars come out, fireflies drift between the
flowers, and sometimes a star falls.

## How to play

- **Tap the earth** — plant a seed and watch it grow into a new species.
- **Tap a flower** — open its field-guide card: a botanical name and a small
  secret, both generated just for it.
- **Tap the sky** — a seed rides the wind down and plants itself where it
  lands. At night, you may summon a shooting star.
- **♪ button** — mute or unmute the garden.
- **🌿 button** — start a completely new garden (new species, new hills, new
  musical key).
- **The URL is your garden.** The address bar quietly encodes everything
  you've planted — copy the link and send it to someone, and they'll walk
  through your exact garden.

Sound on. Headphones are even better — every flower sings from where it
stands (stereo position follows its place in the field).

## What's under the hood

One HTML file. No dependencies, no build step, no assets, no network calls.

- **Procedural botany** — four plant archetypes (lantern-stalks, chorus-bushes,
  weeping chimewillows, bellflowers) whose skeletons, leaves, and blooms are
  generated per-seed with a deterministic PRNG (mulberry32), so a shared
  garden regrows identically anywhere.
- **Generative music** — pure Web Audio synthesis: per-plant oscillator voices
  with envelopes, a lowpass filter, stereo panning, ping-pong-ish delay, and a
  convolution reverb whose impulse response is itself synthesized noise. Each
  garden picks a root note and a pentatonic scale, so every plant is always in
  key with its neighbors. A slow root-and-fifth pad and filtered-noise wind
  breathe underneath.
- **A living sky** — keyframed day/night cycle (~3 minutes per day), value-noise
  wind that bends every stem and blade of grass, twinkling stars, a rising and
  setting sun and moon, fireflies that seek out the blooms after dark.
- **Tiny poetry engine** — every species gets a Latin-ish binomial name and a
  one-line secret, generated from its seed.
- **State in the URL** — the whole garden serializes into the `#g=` fragment
  (and localStorage), so gardens are shareable and survive reloads.

## Run it yourself

```
python3 -m http.server 8000
# open http://localhost:8000
```

or just open `index.html` in a browser.

### Hosting

The live site is GitHub Pages, serving the `gh-pages` branch. To ship an
update, push the change here and run the "Publish to GitHub Pages" workflow
from the Actions tab (it mirrors this branch into `gh-pages`) — or simply
`git push origin HEAD:gh-pages`.

The whole app is the single `index.html`, so any static host works just as
well (`npx vercel deploy --prod`, Netlify Drop, Cloudflare Pages, …).

---

Grown by [Claude Code](https://claude.com/claude-code) in a sandbox where the
only instruction was *"create anything you want."*
