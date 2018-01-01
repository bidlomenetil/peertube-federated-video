# PeerTube federated video

ActivityPub video platform with a Node.js/Express backend, an Angular client, PostgreSQL persistence, and Redis-backed background processing.

This repository is a separately imported source snapshot of [PeerTube](https://github.com/Chocobozzz/PeerTube). Upstream contributors created the imported application; local work is recorded in the commits after the source import. See [Upstream source](UPSTREAM_SOURCE.md) for attribution.

## Read the history accurately

The local history starts with a source import on November 3, 2026. The parent year directory and the “Original project year” field do not establish a historical contribution date or a release tag. The imported upstream commit and release are not recorded in the available provenance file.

## Navigate the source

| Path | Responsibility |
| --- | --- |
| [server/](server/) | API, federation, persistence, and jobs |
| [client/](client/) | Angular application |
| [packages/](packages/) | Shared libraries and tests |
| [apps/](apps/) | CLI and runner applications |
| [support/](support/) | Deployment and API documentation |

## Prepare development

Read `AGENTS.md`, `package.json`, and `pnpm-workspace.yaml`. Use the pinned pnpm version with compatible Node.js. Configure PostgreSQL, Redis, and FFmpeg as described in the project guidance before starting the backend.

The commands below are existing project entry points, to run after their toolchain, dependency, and service prerequisites are ready:

```sh
pnpm run build:server
pnpm run build:tests
pnpm run lint
```

## Validation scope

The documentation change was checked for local link targets, manifest command references, and whitespace errors. Application builds, dependency installation, and service-backed test suites were not run for this documentation change. These instructions do not establish deployment readiness.

## Preserve upstream licensing

Missing upstream license notices were restored from the official repository. [License restoration](LICENSE_RESTORATION.md) records the retrieval revision, exact source URLs, and SHA-256 hashes. That revision does not identify the imported application snapshot. Read per-file and subtree notices as well as the root license before redistribution. This documentation does not change the license of imported code.

## Install and run locally

Prepare Node.js/pnpm, PostgreSQL, Redis, and FFmpeg as described in `AGENTS.md`. Install the locked workspaces:

```sh
pnpm install --frozen-lockfile
pnpm run dev
```

Review `config/default.yaml` and the development configuration before starting services. Configure database credentials, Redis, hostname/listeners, and media storage for the local instance. For backend-only work, use `pnpm run dev:server`; the full development script also launches the Angular client.

## Plan a deployment

Deployment assets are under `support/`. Build the server and client with `pnpm run build` before using `pnpm start`; `start:server` intentionally excludes the client. Configure a public HTTPS hostname, persistent media storage, database backups, mail, and reverse proxy settings before joining federation. The development credentials described in `AGENTS.md` are not production credentials.
