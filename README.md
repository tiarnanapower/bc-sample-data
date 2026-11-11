# bc-sample-data

Sample data for the SE Power Manager's **Sample Catalog**. The app only reads this repo, so samples change only when someone with access commits here.

```
catalog.json                         index of every sample
samples/<name>/sample.json           name, description, tags, languages and the version list
samples/<name>/<version>/            one folder per version, never edited once published
  manifest.json                      what the version contains
  catalog.json                       categories, brands and a light summary of each product
  catalog/products-0001.json         full products, 100 per file
  <section>.json                     shipping, tax, pricing, storefront, checkout, inventory, b2b
  i18n/<locale>.json                 translations
images/<sha256>.<ext>                product pictures, shared by every sample
```

## Adding a sample or a new version

From the `se-power-manager` project, with the source store set in `.env.local`:

```bash
pnpm samples:capture --name "Outdoor Retailer" --out ../bc-sample-data --notes "What changed"
cd ../bc-sample-data && git add -A && git commit -m "Add outdoor-retailer v2" && git push
```

Capturing the same name again adds the next version (`v2`, `v3`…) beside the old ones. Only demo-safe data belongs here.
