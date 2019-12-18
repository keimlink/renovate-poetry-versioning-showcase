# Renovate Poetry Versioning Showcase

Showcase for a bug in Renovate's [Poetry versioning](https://github.com/renovatebot/renovate/blob/6684a95c6b/lib/versioning/poetry/readme.md).

Poetry versioning doesn't support pre-release versions because it's based on [npm versioning](https://github.com/renovatebot/renovate/blob/6684a95c6b/lib/versioning/npm/readme.md).

The reason seems to be that npm uses Semantic Versioning, which uses a different definition of a [pre-release version](https://semver.org/#spec-item-11) than [PEP 440](https://www.python.org/dev/peps/pep-0440/#pre-releases).

Example log output:

```json
{
  "depName": "coverage",
  "depType": "dev-dependencies",
  "currentValue": "5.0b1",
  "managerData": {
    "nestedVersion": true
  },
  "datasource": "pypi",
  "skipReason": "unknown-version",
  "updates": []
}
```

Since [coverage 5.0 has been released](https://pypi.org/project/coverage/#history) Renovate should propose an update.

See [renovatebot/renovate#5011](https://github.com/renovatebot/renovate/issues/5011) for more details.
