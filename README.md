# Recommendation Engine — Mobile

> **Template copy.** This repository is one of the name-substituted React
> Native CLI template copies in `bookchaowalit-mobile`. The canonical template
> is [`bookchaowalit-mobile/portfolio-projects-showcase-mobile`](https://github.com/bookchaowalit-mobile/portfolio-projects-showcase-mobile);
> fix template-level problems there first. Consolidation/archive of the copies
> is pending owner decision D5 (BD-033), see
> `repository-catalog/portfolio/MOBILE-CONSOLIDATION-2026-10.md` in solo-empire.
> There are no native `android/`/`ios/` projects; CI builds the Metro Android
> JS bundle.

React Native CLI (bare workflow) mobile app for **Recommendation Engine**.

Part of [Chaowalit Greepoke](https://bookchaowalit.com)'s 101 Portfolio Projects.

## Tech Stack

- **Framework:** React Native 0.76 (bare CLI)
- **Language:** TypeScript
- **Navigation:** React Navigation v6
- **UI:** React Native Vector Icons

## Features

- **Ranking** tab ("Ranking Desk"): choose an intent (Learn / Make / Ship),
  optionally add keywords, and get the top 5 Bookchaowalit projects. Every
  score is explained (category weight × intent, +4 per matching keyword);
  open a project or dismiss it with "Not for me".
- **Catalog** tab: every project grouped by category with the editorial
  weights used for ranking.
- Honest by design: no ML model, embeddings or tracking — the same rules as
  the web frontend (`bookchaowalit-recommendation-engine-frontend`).

## Getting Started

```bash
npm ci
npm start
```

The native `android/` and `ios/` projects have not been generated yet, so
`npm run android` / `npm run ios` need that step first (see
`docs/UPGRADE-PLAN.md`).

## Validation

```bash
npm run validate      # eslint + tsc --noEmit + jest
mkdir -p dist && npm run bundle:android   # Metro bundle smoke check
```

Pure logic lives in `src/lib/` and is unit-tested with Jest (`__tests__/`).
CI (`.github/workflows/ci.yml`) calls the shared
`bookchaowalit/platform-ci-workflows` v1.1.1 jobs (pinned by SHA): `npm ci`,
lint, typecheck, Jest, the Android bundle, and the security scans. Reviewed
scanner exceptions are in `osv-scanner.toml` and `.trivyignore`.

## Related

- **Frontend:** [bookchaowalit-website/recommendation-engine-frontend](https://github.com/bookchaowalit-website/recommendation-engine-frontend)
- **Portfolio:** [bookchaowalit.com](https://bookchaowalit.com)

## License

MIT
