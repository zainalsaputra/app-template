# Contributing

Contributions are welcome through GitHub issues and pull requests.

## Development

Requirements:

- Helm 3.12 or newer.
- Git.
- Optional: chart-testing and Kind for integration tests.

Run the local checks:

```bash
helm lint --strict ./charts/app-template
helm template test ./charts/app-template

for values in examples/*-values.yaml; do
  helm template test ./charts/app-template -f "$values" >/dev/null
done
```

## Pull requests

- Keep changes focused.
- Add or update an example for new features.
- Add schema validation for new values.
- Document each new value in `values.yaml` and the chart README.
- Increment `Chart.yaml` version when behavior changes.
- Use Semantic Versioning for the chart API.
- Do not add cloud-, framework-, or GitOps-specific defaults to the core chart.

## Design rule

Prefer native Kubernetes object shapes for advanced fields. Add a convenience abstraction only when it reduces repeated configuration without hiding important Kubernetes behavior.

