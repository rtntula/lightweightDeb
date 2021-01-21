# apt

> [`<<`](index.md)

`list` (work-in-progress)
  list is somewhat similar to `dpkg-query --list` in that it can display a list of packages satisfying certain criteria.
  It supports glob(7) patterns for matching package names as well as options to list
  - installed (`--installed`),
  -  upgradeable (`--upgradeable`) or
  - all available (`--all-versions`) versions.

Example:

```
$ apt list --upgradable
```

Alt:

```
$ sudo apt upgrade --dry-run
```

