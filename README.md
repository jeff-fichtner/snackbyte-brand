# snackbyte brand

The brand's record and its authority. Values, rules, voice, and the reasoning
behind them.

**This repository is not code.** It has no build, no dependencies and no tests.
A value here is design data, not a string that belongs to a stylesheet — a
printer, a designer and a build all read the same number. `tokens.json` is that
data; [`GUIDE.md`](./GUIDE.md) is the same facts in prose, with the reasons.

## Who reads this

| Reader                    | Reads                                                     |
| ------------------------- | --------------------------------------------------------- |
| A person                  | `GUIDE.md`, or the live page at <https://snackbyte.io/style/> |
| An implementation         | `tokens.json`                                              |
| A designer or a printer   | `GUIDE.md`, and the exported artwork                        |

## How it is used

One implementation exists: **`snackbyte-brand-render`**, which reads this
repository at build time and compresses it into the forms code can consume —
CSS custom properties, TypeScript constants, the marks as SVG, a favicon set —
and publishes them as `@snackbyte/brand`. It holds no values of its own and
makes no decisions. If a change there needs a judgment call, the judgment
belonged here.

Other implementations may follow — a design-tool library, a CMYK print spec —
and read this repository the same way. None of them is the authority; this is.

Paper (letterhead, cards, a signature) uses the guide and the exported artwork
directly. It has no dependency on the npm package and never will.

## Changing a value

1. Change it here, with the reason, in both `tokens.json` and `GUIDE.md`.
2. Tag a version.
3. Bump the tag in `snackbyte-brand-render` and publish.

A value changed anywhere else is a bug that the next build will overwrite.
