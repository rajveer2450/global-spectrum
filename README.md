# Global Spectrum website

One static page (`index.html`) with inline CSS and a few lines of JavaScript. No framework, no build step, no third-party requests. Hosted on GitHub Pages: every push to `main` republishes it.

## Still to add

Everything else on the page is filled in with real details.

- **GSTIN and Udyam numbers:** in `index.html`, find the commented-out `Registrations` block near the end of the contact section, put in the real numbers, and remove the `<!--` and `-->` around it.
- **Logo:** see below.
- **Domain:** when you buy one, add a file named `CNAME` containing just the domain (for example `globalspectrum.in`). At your domain registrar, point the domain at GitHub Pages ([GitHub's guide](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)). Then update the `canonical`, `og:url` and `url` addresses in the `<head>` of `index.html`.
- **Haulage estimate:** it assumes about 25 t per truck. Change `data-truck` on the `<form id="estimate">` tag, and the note under the result, if your trucks carry more or less.

## Founder photo

The founder photo is cropped to 4:5 and saved three ways: `assets/img/founder.avif`, `founder.webp` and `founder.jpg`. To change it, replace all three with the new photo at the same size (720 × 900 px).

## Logo

The header shows the name as text. The logo is a symbol only, so it goes beside the name. When it's ready, save it as `assets/logo.svg` (or `.png`) and replace this line in `index.html`:

```html
<a class="mark" href="#top">Global Spectrum</a>
```

with:

```html
<a class="mark" href="#top" style="display:inline-flex;align-items:center;gap:.6rem"><img src="assets/logo.svg" alt="" width="28" height="28">Global Spectrum</a>
```

Also replace `assets/favicon.svg` with the symbol, so it shows in the browser tab.

### Prompt for Gemini

Generate each of these separately. Image models handle one logo per image best.

> Design a logo symbol only, with no text, letters, initials or words anywhere in the image. It is for "Global Spectrum", an Indian company that mines minerals, transports them by road and rail, and buys and sells land and property.
>
> The symbol is a globe seen straight on: a perfect circle cut into four horizontal bands, like a spectrum and like layers of the earth. From top to bottom: machinery yellow (#F0B323), deep scrub green (#2F3D29), iron-ore red (#7A3B2E) and coal black (#1E1D1B). Separate the bands with thin white gaps, and make the bands slightly different heights. Around the globe, add one thin orbit ring in coal black, tilted about 20 degrees, passing behind the globe on one side and in front of it on the other, suggesting routes and movement. Bold, geometric and balanced.
>
> Style: flat vector, solid colours only. No gradients, shadows, 3D shading, glow or texture. No latitude or longitude grid lines, no continents, no rainbow colours. Crisp edges. It must stay clear and recognisable at 32 × 32 pixels. Centre it on a plain white background with generous empty space around it, square 1:1 canvas, high resolution.

Follow-up prompts in the same chat, if you like the result:

> Now give me the same symbol in one colour only, coal black (#1E1D1B) on white, keeping the white gaps between the bands. For stamps, letterheads and truck doors. Still no text.

> Now give me a version for dark backgrounds: the same symbol on a coal black (#1E1D1B) background, with the black band and the orbit ring changed to pale limestone grey (#E4E2DD). Still no text.

Gemini returns a raster image. For a sharp, small logo file, trace it to SVG (for example in Figma, Illustrator or an online vectoriser) or ask a designer to redraw it.

## Photographs

The mining, haulage and property photos are real photographs from Wikimedia Commons, used under their licences. The credit line in the footer must stay while they are on the site. Captions describe the place shown, because these are not Global Spectrum's own sites. When you have photos of your own pits, trucks and plots, swap them in (same file names in `assets/img/`, or update the `<picture>` tags) and remove the matching credits.

| Photo | Author | Licence |
|---|---|---|
| [Iron ore mine, Keonjhar](https://commons.wikimedia.org/wiki/File:One_of_the_iron_ore_mines_in_Keonjhar_district.jpg) | Bikashkumargiri1997 | CC BY-SA 4.0 |
| [Shovel and dumper, Amlohri](https://commons.wikimedia.org/wiki/File:Shovel_Dumper_combination.jpg) | Rosehubwiki, Kuber Patel | CC BY-SA 4.0 |
| [Dumpers at Gevra](https://commons.wikimedia.org/wiki/File:GEVRA_DUMPERS.jpg) | Meemoprasad | CC BY-SA 3.0 |
| [Loaded truck on an Indian highway](https://commons.wikimedia.org/wiki/File:Indian_truck-Full_loaded.JPG) | Diego Delso | CC BY-SA 4.0 |
| [Plots in Hyderabad](https://commons.wikimedia.org/wiki/File:Hyderabad_view_Plots.jpg) | ramkich4u | CC0 |
| [Land surveying](https://commons.wikimedia.org/wiki/File:Land_surveying.jpg) | Fotokannan | CC BY-SA 4.0 |

Each photo ships as AVIF with a WebP fallback at two or three widths. If you add your own, keep them under ~250 KB each.

## Forms

Both forms open the visitor's email app with the message already written. The enquiry form can also send the same text on WhatsApp. No server is needed.

To receive submissions without the visitor's email app, sign up for a form service such as Formspree, then replace `action="mailto:..."` and remove `enctype="text/plain"` and the `e.preventDefault()` submit handlers in the script.

## Haulage estimate

The estimate uses about 25 t per truck. Change `data-truck` on the `<form id="estimate">` tag, and the sentence under the result, to match your fleet.

## Publishing changes

Edit, then:

```
git add -A
git commit -m "Update contact details"
git push
```

GitHub Pages republishes in about a minute.
