# `to-romaji`

A very basic kana to modern Hepburn-like rōmaji converter.

e.g. converts "にんじゃりばんばん" to "ninjaribanban".

## Notes

- Handles repeated っ (e.g. "すっっっごくいい" → "suggggokuii",
  "あつっ" → "atsu'").
- Separates a final ん from a following vowel with a hyphen (e.g.
  かんいかきとめ → "kan-ikakitome").
  Maybe we should use an apostrophe instead?

- Does **not** produce macrons for long vowels (長音) since it's too hard to
  distinguish between cases like みずうみ which should be "mizuumi" and
  すうがく which should be "sūgaku".
- Does **not** distinguish between は becoming "ha" and "wa".
  We tried to do this by using
  [`@birchill/tiny-segmenter`](https://github.com/birchill/tiny-segmenter)
  to find 'は' particles but it turned up false positives on input like
  "おふろにはいる" (which it segments as "おふろ | に | は | いる").
- Does **not** convert half-width katakana.
  [`toNormalized`](https://github.com/birchill/normal-jp/?tab=readme-ov-file#tonormalized)
  from [`@birchill/normal-jp`](https://github.com/birchill/normal-jp/) can be
  used as a pre-processing step to handle half-width katakana.

## Installation

```
npm install @birchill/to-romaji
```

## Usage

```typescript
import { toRomaji } from '@birchill/to-romaji';

const romaji = toRomaji('にんじゃりばんばん');
// romaji = 'ninjaribanban'
```
