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

A brand change starts here and travels outward. Only the first step holds a
decision; the rest is mechanical.

**1. Here — decide it.** Change the value in `tokens.json` *and* the same fact in
`GUIDE.md`; they are two views of one thing and go stale separately. Say why in the
commit. Then tag:

```bash
git commit -am "why this changed"
git tag v1.2.0 && git push origin main --tags
```

Versioning is semantic: MAJOR if a value's meaning changes or a role disappears,
MINOR for a new role or a new block, PATCH for wording and reasons.

**2. `snackbyte-brand-render` — take it.** Bump the tag, rebuild, verify, commit the
output, tag:

```bash
npm pkg set devDependencies.snackbyte-brand="github:jeff-fichtner/snackbyte-brand#v1.2.0"
npm install && npm run build && npm run check:all
git commit -am "take guide v1.2.0" && git tag v1.1.0 && git push origin main --tags
```

`check:all` fails if `dist/` is stale or if any value stops matching the guide.

**3. Each consumer — install it.** In `snackbyte-site`, and in anything else that
consumes the package:

```bash
npm i github:jeff-fichtner/snackbyte-brand-render#v1.1.0
npm run check:all && npm run build
```

Then look at the built thing before handing it over.

**4. Record where it landed.** If the change reaches a surface, update the Rollout
table in `GUIDE.md`.

A value changed anywhere but step 1 is a bug: the next build overwrites it, or the
consumer's gate rejects it.
