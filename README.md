# project-boost-php

[![Latest Version on Packagist](https://img.shields.io/packagist/v/sandermuller/project-boost-php.svg?style=flat-square)](https://packagist.org/packages/sandermuller/project-boost-php)
[![GitHub Tests Action Status](https://img.shields.io/github/actions/workflow/status/sandermuller/project-boost-php/run-tests.yml?branch=main&label=tests&style=flat-square)](https://github.com/sandermuller/project-boost-php/actions/workflows/run-tests.yml)
[![Total Downloads](https://img.shields.io/packagist/dt/sandermuller/project-boost-php.svg?style=flat-square)](https://packagist.org/packages/sandermuller/project-boost-php)
[![License](https://img.shields.io/packagist/l/sandermuller/project-boost-php.svg?style=flat-square)](LICENSE)
[![Laravel Boost](https://badge.laravel.cloud/boost-badge.svg?style=flat-square)](https://github.com/laravel/boost)

AI agent skills for PHP application developers — **any framework, or none**. Two
framework-agnostic skills plus a `foundation` guideline that frames the codebase
as an application rather than a package. It rides the
[`sandermuller/boost-core`](https://github.com/sandermuller/boost-core) sync
engine and ships no code of its own.

**Documentation: <https://sandermuller.github.io/boost-core/packages/project-boost-php/>**

![overview image](overview.png)

> [`laravel/boost`](https://github.com/laravel/boost) is Laravel-only. This
> package covers Symfony, plain-PHP, and framework-agnostic applications.
> Building a Laravel app? Install
> [`sandermuller/project-boost-laravel`](https://github.com/sandermuller/project-boost-laravel)
> instead — it coexists with `laravel/boost` rather than replacing it. Not sure
> which member fits? The
> [picker](https://sandermuller.github.io/boost-core/guide/which-package) decides
> it in two questions.

## What you get

**Two skills** — universally applicable PHP practices, not tied to any
architecture.

| Skill | Triggers when |
|---|---|
| `dependency-injection` | Constructor injection, container hygiene, avoiding service locators |
| `legacy-coexistence` | Adding modern PHP (typed properties, readonly, enums) to a 7.x codebase incrementally |

**One guideline** — `foundation`. Framework-agnostic application-developer
framing: what an application codebase is, how its edges form its real contract,
and how to work in it. Always shipped, no tag required.

> Want architecture-specific guidance (DDD layering, repositories, domain
> modeling)? Those shipped through 0.x but were dropped at 1.0 to keep the
> default framework-agnostic. Copy any you want into your own
> `.ai/skills/<name>/SKILL.md` (host copies shadow vendor skills), or exclude a
> shipped skill with
> `->withExcludedSkills(['sandermuller/project-boost-php:<name>'])`.

## Install

```bash
composer require --dev sandermuller/project-boost-php
vendor/bin/boost install   # pick agents and allowlist vendors; writes boost.php
vendor/bin/boost sync      # fan the skills + guideline out
```

PHP 8.3+. Pulls in `sandermuller/boost-core` transitively.

Minimal `boost.php`:

```php
use SanderMuller\BoostCore\Config\BoostConfig;
use SanderMuller\BoostCore\Enums\Agent;

return BoostConfig::configure()
    ->withAgents([Agent::CLAUDE_CODE, Agent::CURSOR, Agent::CODEX])
    ->withAllowedVendors(['sandermuller/project-boost-php']);
```

`withAllowedVendors()` is explicit on purpose: an installed dependency's skills
sync only when its package name is listed.

## Documentation

| Topic | Page |
|---|---|
| What this package ships, and how it compares to `laravel/boost` | [Overview](https://sandermuller.github.io/boost-core/packages/project-boost-php/) |
| Install and first run | [Install](https://sandermuller.github.io/boost-core/packages/project-boost-php/install) |
| `boost.php`, skill sources, coexistence, auto-sync | [Configuration](https://sandermuller.github.io/boost-core/packages/project-boost-php/configuration) |
| Tags, skill dependencies, remote skills, conventions, file ownership | [Guide](https://sandermuller.github.io/boost-core/guide/what-is-boost) |
| Every command and exit code | [CLI reference](https://sandermuller.github.io/boost-core/reference/cli) |

The semver-protected surface is in [`PUBLIC_API.md`](PUBLIC_API.md).

## Testing

```bash
composer test
```

Pest suite — sanity tests on the shipped skill and guideline set: skills parse
with a `name` matching the filename and a non-empty `description`; guidelines are
frontmatter-free and open with a Markdown heading.

## License

MIT. See [LICENSE](LICENSE).
