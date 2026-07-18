# Downloadable Font Catalog

This directory hosts the downloadable font catalog for the eBook Reader app. The
app fetches [`fonts.json`](fonts.json) to list fonts users can download in-app.
Each catalog entry points at a `<slug>.zip` in this directory containing the font
file(s) plus that font's license text.

The catalog holds two kinds of font:

- **Latin reading faces** (`"languages": ["Latn"]`) — general-purpose reading
  typefaces. These ship as downloads rather than inside the app so the app
  binary stays small; the app's default reader font is the system font, so none
  of them is required for a usable first run.
- **Script coverage** — typefaces for writing systems the system fonts serve
  poorly (CJK, Arabic, Devanagari, Thai), tagged with their language.

The app additionally *bundles* OpenDyslexic and Atkinson Hyperlegible. Those two
are accessibility affordances and are deliberately **not** download-only — a
reader who needs them should never have to wait on a network to read
comfortably. They are not listed here.

## Manifest

`fonts.json` is versioned (`"version": 1`) and lists, per font: display name,
verified CoreText family name, language tag(s), zip/installed byte sizes, the
files inside the zip, license, upstream source, and upstream version.

## Packaging

Each `<slug>.zip` contains, flat (no subfolders):
- One or more font files (TTF/OTF, static or variable).
- `OFL.txt` — that font's SIL Open Font License text, copied verbatim from
  upstream.

## Fonts and Licenses

All fonts in this catalog are licensed under the
[SIL Open Font License 1.1](https://openfontlicense.org/) (OFL). The license
text bundled in each zip is the one shipped by the upstream project at the
version listed in `fonts.json`.

| Font | Language | Upstream |
|---|---|---|
| Literata | Latin (serif) | [google/fonts — ofl/literata](https://github.com/google/fonts/tree/main/ofl/literata) |
| Inter | Latin (sans) | [google/fonts — ofl/inter](https://github.com/google/fonts/tree/main/ofl/inter) |
| EB Garamond | Latin (serif) | [google/fonts — ofl/ebgaramond](https://github.com/google/fonts/tree/main/ofl/ebgaramond) |
| Merriweather | Latin (serif) | [google/fonts — ofl/merriweather](https://github.com/google/fonts/tree/main/ofl/merriweather) |
| Lora | Latin (serif) | [google/fonts — ofl/lora](https://github.com/google/fonts/tree/main/ofl/lora) |
| LXGW WenKai 霞鹜文楷 | Simplified Chinese (kai style) | [lxgw/LxgwWenKai](https://github.com/lxgw/LxgwWenKai) |
| Source Han Serif SC | Simplified Chinese | [adobe-fonts/source-han-serif](https://github.com/adobe-fonts/source-han-serif) |
| Source Han Serif TC | Traditional Chinese | [adobe-fonts/source-han-serif](https://github.com/adobe-fonts/source-han-serif) |
| Source Han Serif JP | Japanese | [adobe-fonts/source-han-serif](https://github.com/adobe-fonts/source-han-serif) |
| Source Han Serif KR | Korean | [adobe-fonts/source-han-serif](https://github.com/adobe-fonts/source-han-serif) |
| Amiri | Arabic | [google/fonts — ofl/amiri](https://github.com/google/fonts/tree/main/ofl/amiri) (upstream: [aliftype/amiri](https://github.com/aliftype/amiri)) |
| Noto Serif Devanagari | Hindi | [google/fonts — ofl/notoserifdevanagari](https://github.com/google/fonts/tree/main/ofl/notoserifdevanagari) |
| Noto Serif Thai | Thai | [google/fonts — ofl/notoserifthai](https://github.com/google/fonts/tree/main/ofl/notoserifthai) |

The Latin packages ship upright + italic. Literata, Inter, EB Garamond and Lora
are variable fonts covering the full weight range in two files; Merriweather is
static and ships Regular/Italic/Bold/BoldItalic.

Source Han Serif and Amiri packages include both Regular and Bold weights
(bundled at no extra download cost from the same upstream release/repo). The
Noto Serif Devanagari and Noto Serif Thai packages ship the official variable
font, which covers the full weight range in a single file.
