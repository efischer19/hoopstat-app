# hoopstat-app

Frontend analytics dashboard for [hoopstat.haus](https://hoopstat.haus).

This repository is initialized from `static-js-app-blueprint` and contains the starter static frontend scaffolding for the Hoopstat app. The example `src/` files remain in place intentionally and will be replaced in follow-up feature work.

## Local development

```bash
pip install pre-commit
pre-commit install
./scripts/local-ci-check.sh
```

Open `src/index.html` directly in a browser for local preview.

## Deployment

- **Primary deploy path:** AWS S3 + CloudFront via `.github/workflows/deploy-aws.yml`
- **GitHub Pages workflow:** disabled for this repository

Configure these GitHub Actions repository variables before deploying:

- `AWS_ROLE_ARN`
- `AWS_REGION`
- `S3_BUCKET_NAME`
- `CLOUDFRONT_DISTRIBUTION_ID`

## Documentation

- Project docs source: `docs-src/`
- ADRs: `meta/adr/`
