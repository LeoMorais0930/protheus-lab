<div align="center">

# Protheus Lab

[Português](README.md) · [English](README.en.md)

**From environment setup to building routines: a hands-on Protheus learning lab.**

ADVPL · TLPP · SQL · Docker · WSL2

[Getting started](docs/ambiente.md) · [Architecture](docs/arquitetura.md) · [Learning roadmap](docs/roteiro.md) · [Credits](CREDITS.md)

</div>

---

## Goal

Learn Protheus from the ground up, covering both ERP behavior and the development of new and customized routines: data structures, configuration, business rules, programming, debugging, and integrations.

AI supports code writing and investigation. Understanding the context, reviewing decisions, and verifying behavior remain essential parts of the learning process.

This repository documents **Leonardo Morais's** learning journey using fictional examples and data. It is a local educational lab.

## Current status

| Milestone | Status |
|---|---|
| Docker Desktop and WSL2 | Installed; Docker Engine responded to verification |
| Reference project | Cloned and inspected |
| Protheus 2510 + PostgreSQL 16 Compose | Four services started; ODBC query verified |
| Local ports and persistence | Loopback bindings and volumes configured; backup not tested |
| First login and licensing | Pending guidance; License Server errors need investigation |
| ADVPL compilation and debugging | Not tested yet |
| Custom routines | Planned |

**Prepared environment:** Protheus **12.1.2510** with **PostgreSQL 16**. The original checkout contains a 2310 Compose configuration; this lab uses newer images inspected and pinned by digest. ERP login has not been validated.

## Technologies

| Technology | Role in the lab |
|---|---|
| Protheus | ERP whose routines and business rules we will study |
| ADVPL / TLPP | Languages for development and customization |
| SQL Server 2022 Developer | Original project alternative; not used in this lab |
| PostgreSQL 16 | Database selected and started in this lab |
| Docker Desktop + Compose | Container service management |
| WSL2 | Linux environment used by Docker on Windows |
| AppServer | Executes routines |
| DBAccess | Connects the application to the database |
| License Server | Environment licensing service |
| VS Code + TOTVS Developer Studio | Editing, compilation, and debugging |
| Git / GitHub | Source and documentation history |
| DBeaver or HeidiSQL | Data exploration during exercises |

Some tools still need configuration. This table describes the intended architecture, not a completed installation.

## Repository guide

The detailed guides below are currently written in Portuguese:

- [Environment](docs/ambiente.md): preparation, outstanding work, and daily operation.
- [Architecture](docs/arquitetura.md): concepts and the path of an operation through the system.
- [Learning roadmap](docs/roteiro.md): practical stages with completion criteria.
- [Journal](docs/diario.md): setup decisions and verification notes.
- [Credits](CREDITS.md): original project and authorship boundaries.

## The project behind this lab

Credit to **Felipe Raposo**, author of [Ambiente Protheus 12 com PostgreSQL ou Microsoft SQL Server](https://bitbucket.org/felipe_raposo/docker-protheus-postgresql-microsoft-sql-server/), the reference for the Docker environment setup.

This repository contains original documentation and references to that project. It includes an original Compose configuration referencing the author's images, without redistributing TOTVS binaries or RPOs. See [CREDITS.md](CREDITS.md).

## Scope of use

Fictional data and local access only. Product and third-party image terms must be checked with their respective providers. Test Company 99 does not, by itself, authorize component redistribution.

This repository has no image publishing or automatic deployment pipeline.
