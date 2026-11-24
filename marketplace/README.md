# Marketplace listing images

One folder per app. Each has:

| File | Size | Use in the listing |
| --- | --- | --- |
| `highlight-1.png` … `highlight-3.png` | 1840 × 900 | Highlight screenshots |
| `highlight-1-cropped.png` … `highlight-3-cropped.png` | 580 × 330 | Cropped highlight screenshots |
| `captions.json` | — | Highlight title, summary and caption for each image |

The images are captured from the real app screens, running against the real app code with sample data (no real people or companies). To regenerate them after a UI change, run this in the factory repo:

```bash
npm run marketplace:images      # writes marketplace-assets/<slug>/...
```

Then copy the folders here.

App logos (144 × 144) and banners (1120 × 548) are not included; they need to be designed separately.
