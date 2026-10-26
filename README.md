# Product packs for design-critic — template

Start here to connect your own products to [design-critic](https://github.com/gorelikroman/design-critic-core),
the design critic for Claude Code. This repository becomes your team's private marketplace of
**product packs**: one small plugin per product, carrying that product's layer — where its
design system lives, its voice, which component when, its patterns, hard rules and decisions
log. The critic itself stays generic; your products stay in your repository.

No special design-system format is needed. The layer points to your design library, tokens
and components where they already are.

## 1. Make your copy

Press **Use this template** on GitHub, create a **private** repository (for example
`my-product-packs`), and clone it.

## 2. Install the critic

```bash
claude plugin marketplace add gorelikroman/design-critic-core
claude plugin install design-critic@design-critic-core
```

## 3. Add your product

Open Claude Code in your copy and run:

```
/design-critic:new-product <Your product>
```

The critic asks for the product's names, owners, design library link, token source and 10–20
shipped screens, writes the pack into `plugins/design-critic-<your-product>/`, fills the layer
from those sources and from a review of the screens, and hands it to the product owner.

Then delete the example: `plugins/design-critic-example/` and its entry in
`.claude-plugin/marketplace.json`. Rename the marketplace (`"name"` in that file) to your
repository's name.

## 4. Publish and install

Push your copy. Everyone who works on the product:

```bash
claude plugin marketplace add <your-org>/<your-repo>
claude plugin install design-critic-<your-product>@<your-marketplace-name>
```

Name the product in a request — "review the checkout in <Your product>" — and the critic
loads its pack; the first line of every answer says which product is active.

## What a pack looks like

`plugins/design-critic-example/` is a blank pack:

```
plugins/design-critic-example/
  .claude-plugin/plugin.json             name, version
  skills/product-layer/SKILL.md          the product's names: how the critic finds the pack
  skills/product-layer/product.md        the layer: sources, voice, components, patterns, hard rules, motion
  skills/product-layer/design-decisions.md   the decisions log, grown by reviews
```

Updating a pack: commit, bump `version` in its `plugin.json`, and teammates run
`claude plugin update design-critic-<your-product>@<your-marketplace-name>`.
