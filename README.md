# Global Spectrum website

One static page (`index.html`) with inline CSS and a few lines of JavaScript. No framework, no build step, no third-party requests. Hosted on GitHub Pages: every push to `main` republishes it.

## Fill these in before sharing the link

Open `index.html` and search for each item. Every spot is also marked with an `<!-- EDIT -->` comment.

| Search for | Replace with | Where it appears |
|---|---|---|
| `[+91 00000 00000]` and `+910000000000` | Main phone number (keep the `tel:` link format: `+91` followed by 10 digits) | Hero, founder facts, contact |
| `910000000000` | WhatsApp number (country code + number, no `+`) | WhatsApp link, `data-whatsapp` on the enquiry form |
| `hello@yourdomain.in` | Your email address | Email link and both forms (`action="mailto:..."`) |
| `[Founder Name]` | Founder's full name | Founder heading, photo alt text |
| `[year]`, `[YYYY]`, `[what you started with...]` | The founder's own story. Rewrite the two-paragraph note in their words | Founder section |
| `[City, State]`, `[States or districts]` | Where you're based and where you work | Founder facts |
| `[your region]`, `[your state]` | Region and state you operate in | Hero, page description, mining |
| `[00]`, `[siding name]` | Fleet size and rail siding | Haulage |
| `[areas you cover]` | Localities for plots | Property |
| `[Office address, line 1]`, `[City, State PIN]`, `[your+office+address]` | Office address, plus the same address in the Google Maps link | Contact |
| `[your-page]`, `[your-handle]` | LinkedIn, Instagram and Facebook URLs. Delete any you don't use | Contact |
| `[00AAAAA0000A0Z0]`, `[U00000XX0000PTC000000]`, `[Lease number, district]`, `[Registration number]` | GSTIN, CIN, mining lease, RERA agent registration. Delete any row that doesn't apply | Contact, "Registrations" |

Also confirm the sample content. It was written to show the design at full size and needs your check:

- **Minerals list:** iron ore, limestone, manganese ore, coal, sand and stone aggregate.
- **Mining description:** overburden removal, drilling and blasting, crushing, sampling.
- **Haulage details:** 16–40 t per trip, GPS on every truck, weighbridge slip, transit pass and e-way bill with every trip.
- **Property services:** industrial land, plots, buildings, leasing, title and registry.
- **Office hours:** Monday to Saturday, 9 am to 7 pm.

## Founder photo

Replace `assets/img/founder.jpg` with the real photo and keep the same file name. Use a portrait crop (4:5), about 1200 × 1500 px. Export it as JPEG at roughly 75–80% quality so it stays under ~200 KB and the site stays fast.

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
| [Silo rake loading, Amlohri](https://commons.wikimedia.org/wiki/File:Silo_rake_loading_at_NCL_Amlohri_Coal_Mine_at_Singrauli.jpg) | Rosehubwiki, Kuber Patel | CC BY-SA 4.0 |
| [Dumpers at Gevra](https://commons.wikimedia.org/wiki/File:GEVRA_DUMPERS.jpg) | Meemoprasad | CC BY-SA 3.0 |
| [Coal train in Dhanbad](https://commons.wikimedia.org/wiki/File:Coal_train_in_Dhanbad.jpg) | Smeet Chowdhury | CC BY 2.0 |
| [Plots in Hyderabad](https://commons.wikimedia.org/wiki/File:Hyderabad_view_Plots.jpg) | ramkich4u | CC0 |
| [Land surveying](https://commons.wikimedia.org/wiki/File:Land_surveying.jpg) | Fotokannan | CC BY-SA 4.0 |

Each photo ships as AVIF with a WebP fallback at two or three widths. If you add your own, keep them under ~250 KB each.

## Forms

Both forms open the visitor's email app with the message already written. The enquiry form can also send the same text on WhatsApp. No server is needed.

To receive submissions without the visitor's email app, sign up for a form service such as Formspree, then replace `action="mailto:..."` and remove `enctype="text/plain"` and the `e.preventDefault()` submit handlers in the script.

## Haulage estimate

The estimate uses 25 t per tipper and 3,800 t per rake. Change `data-tipper` and `data-rake` on the `<form id="estimate">` tag, and the sentence under the result, to match your fleet.

## Publishing changes

Edit, then:

```
git add -A
git commit -m "Update contact details"
git push
```

GitHub Pages republishes in about a minute.
