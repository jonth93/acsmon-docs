# Developer Libraries

Official open-source client libraries for the ACS Monitor REST API

Official client libraries for every major language, all open-source under MIT and free to ship inside commercial products. Pick the right one for your stack — each comes with installation instructions, a method reference, recipes (CMDB sync, PagerDuty bridge, CI/CD post-deploy verification, weekly uptime reports), and troubleshooting guidance in its README.

Documentation hub: [jonth93/acsmon-api](https://github.com/jonth93/acsmon-api)

Endpoint cheat sheet, authentication reference, and an **AI agent guide** (`AI.md`) you can paste into Claude / ChatGPT / Cursor / Copilot / Aider so they produce correct API client code in one read.

### Libraries

PHP
8.1+

acsmon-php-client

Lightweight PHP client built on Guzzle. PSR-4, generator-based pagination.

`composer require acsmon/api-client`
[jonth93/acsmon-php-client](https://github.com/jonth93/acsmon-php-client)

Laravel
10 / 11 / 12

acsmon-laravel-client

First-class Laravel package: facade, publishable config, queueable jobs, events. Pest test suite included.

`composer require acsmon/laravel-client`
[jonth93/acsmon-laravel-client](https://github.com/jonth93/acsmon-laravel-client)

Node.js
18+

acsmon-nodejs-client

Zero-dependency ES module using native `fetch`. TypeScript-friendly. Async iterator pagination.

`npm install acsmon-api-client`
[jonth93/acsmon-nodejs-client](https://github.com/jonth93/acsmon-nodejs-client)

Python
3.9+

acsmon-python-client

Thin wrapper around `requests`. Type-hinted, generator pagination. Great for scripts, Ansible playbooks, data pipelines.

`pip install acsmon-client`
[jonth93/acsmon-python-client](https://github.com/jonth93/acsmon-python-client)

bash + curl
cron / runbooks / quick automation

acsmon-bash

Copy-pasteable shell scripts and curl recipes for one-shot automation, cron jobs, runbooks, and ChatOps. Pure shell — no SDK to install.

[jonth93/acsmon-bash](https://github.com/jonth93/acsmon-bash)

### Common environment variables

Every library honours the same three environment variables, so you can swap clients without re-configuring:

export ACSMON_BASE_URL=https://monitoring.example.com

export ACSMON_EMAIL=api@example.com

export ACSMON_PASSWORD='your-strong-password'

# or, if you already have a long-lived token:

export ACSMON_TOKEN='1|abc...'

For long-running integrations, issue a dedicated API user from **Settings &rarr; Users** and store its token in your secrets manager.

### What you can build with these

- **PagerDuty / Opsgenie / Splunk On-Call bridges** — turn alert events into incidents in your existing on-call tool.

- **CMDB / asset-database sync** — keep your CMDB in step with the devices ACS Monitor is actually polling.

- **Custom dashboards** — pull live status into Grafana, Power BI, or a bespoke status page.

- **Scheduled reports** — generate weekly uptime summaries from `/monitors/{id}/uptime` and email them to stakeholders.

- **Self-service tooling** — give support teams a "trigger a re-poll" button or chatbot command without UI access.

- **CI/CD verification** — after deploying an app, hit `/monitors/{id}/check` to confirm it's healthy.

### Licensing

Every client library is **MIT-licensed** and free to use, modify, and ship inside your own commercial products without restriction. The licensed piece is ACS Monitor itself — see [acsmon.com](https://acsmon.com/) for tiers and pricing.

### Reporting issues / contributing

Each library has its own GitHub issue tracker. Bug reports, feature requests, and pull requests welcome. For commercial support on the ACS Monitor application itself, contact us via [angliacomputersolutions.business](https://angliacomputersolutions.business/).
