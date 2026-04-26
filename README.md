# hoopstat-app

Frontend analytics dashboard for [hoopstat.haus](https://hoopstat.haus).

Browse NBA and WNBA player and team statistics from the latest data pipeline,
with interactive Chart.js visualizations and a pipeline health dashboard.

## Features

- **Data Browser**: Browse player and team statistics from the Gold data pipeline
- **Performance Charts**: Interactive trend charts for points, rebounds, assists, and more (ADR-036)
- **Pipeline Health Dashboard**: At-a-glance status for Bronze, Silver, and Gold pipeline layers
- **Mobile-Responsive**: Mobile-first CSS with responsive breakpoints
- **Accessible**: WCAG 2.1 AA compliant with semantic HTML and keyboard navigation
- **No Build Step**: Vanilla HTML/CSS/JavaScript per ADR-019

## Local development

```bash
pip install pre-commit
pre-commit install
./scripts/local-ci-check.sh
```

Serve locally with any static server:

```bash
cd src
python -m http.server 8080
```

Then open <http://localhost:8080> for the main dashboard or
<http://localhost:8080/health.html> for the pipeline health dashboard.

## Architecture

- **Frontend**: Vanilla HTML5, CSS3, ES6+ JavaScript (ADR-019)
- **Charting**: Chart.js v4 via CDN (ADR-036)
- **Data source**: Gold layer JSON artifacts served via CloudFront
- **Deployment**: AWS S3 + CloudFront

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
- Frontend conventions: `src/README.md`
