# hoopstat-app — Applications

This directory contains the applications for **hoopstat-app**.

## Structure

Each subdirectory represents a standalone application:

```text
apps/
├── hoopstat-web/
│   ├── README.md          # Application-specific documentation
│   ├── ...                # Application source code
│   └── tests/             # Application tests
└── ...
```

## Conventions

- Each application lives in its own subdirectory
- Every application must have a `README.md` explaining its purpose, setup, and
  usage
- Follow the [Development Philosophy](../meta/DEVELOPMENT_PHILOSOPHY.md) for
  code quality standards
- Include tests alongside the application code
