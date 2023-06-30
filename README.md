# Astro Netlify Repro

GH Issue: https://github.com/withastro/astro/issues/7540

## Versions
Astro 2.7.2
Netlify 2.3.0

## Description
SSR routes systematically returns 404 on Netlify when a rest parameter is used at the root of the pages directory.

🚫 
```
src/
├─ pages/
│  ├─ [...page].astro (static works)
│  ├─ persons/[id].astro (ssr 404)
```
✅ 
```
src/
├─ pages/
│  ├─ [page].astro (static works)
│  ├─ persons/[id].astro (ssr works)
```

This problems appears above @astro/netlify 2.2.0, downgrading to said version fixes the issue. Astro version seems irrelevant.

## Step to reproduce

1. Deploy to Netlify
2. From homepage, navigate to any `/persons[id]` route.