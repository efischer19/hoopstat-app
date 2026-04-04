# hoopstat-app — Libraries

This directory contains shared libraries for **hoopstat-app**.

## Structure

Each subdirectory represents a reusable library:

```text
libs/
├── hoopstat-shared/
│   ├── README.md          # Library-specific documentation
│   ├── ...                # Library source code
│   └── tests/             # Library tests
└── ...
```

## Conventions

- Each library lives in its own subdirectory
- Every library must have a `README.md` documenting its public API, usage
  examples, and any dependencies
- Libraries should be independently testable
- Follow the [Development Philosophy](../meta/DEVELOPMENT_PHILOSOPHY.md) for
  code quality standards
- Keep libraries focused — one responsibility per library
