<div align="center">

# Protheus Lab

**Do primeiro ambiente à criação de rotinas: um laboratório de aprendizado em Protheus.**

ADVPL · TLPP · SQL · Docker · WSL2

[Começar](docs/ambiente.md) · [Entender a arquitetura](docs/arquitetura.md) · [Roteiro de estudos](docs/roteiro.md) · [Créditos](CREDITS.md)

</div>

---

## Objetivo

Aprender Protheus do zero, entendendo tanto o funcionamento do ERP quanto a construção e alteração de rotinas: estrutura de dados, configurações, regras de negócio, programação, depuração e integrações.

A inteligência artificial entra como apoio à escrita e à investigação do código. Entender o contexto, revisar as decisões e verificar o comportamento continuam sendo parte do aprendizado.

Este repositório registra a jornada de **Leonardo Morais**, com exemplos e dados fictícios. É um laboratório educacional local.

## Estado atual

| Etapa | Situação |
|---|---|
| Docker Desktop e WSL2 | Instalados; Docker Engine respondeu à verificação |
| Projeto de referência | Clonado e inspecionado |
| Compose com SQL Server | Sintaxe validada; execução ainda não testada |
| Isolamento das portas e persistência | Ajustes pendentes |
| Primeiro acesso ao Protheus | Pendente de orientação do responsável pelo laboratório |
| Compilação e depuração ADVPL | Ainda não testadas |
| Rotinas próprias | Planejadas |

**Referência inspecionada:** Protheus **12.1.2310** com SQL Server **2022**. Uma release diferente exige nova conferência de compatibilidade; não basta trocar o nome de uma pasta.

## Tecnologias

| Tecnologia | Papel no laboratório |
|---|---|
| Protheus | ERP cujas rotinas e regras serão estudadas |
| ADVPL / TLPP | Linguagens para desenvolvimento e customização |
| SQL Server 2022 Developer | Banco escolhido no Compose de referência |
| PostgreSQL 15 | Alternativa disponível no projeto original |
| Docker Desktop + Compose | Gerenciamento dos serviços em contêineres |
| WSL2 | Ambiente Linux utilizado pelo Docker no Windows |
| AppServer | Execução das rotinas |
| DBAccess | Comunicação entre aplicação e banco |
| License Server | Serviço de licenciamento do ambiente |
| VS Code + TOTVS Developer Studio | Edição, compilação e depuração |
| Git / GitHub | Histórico de fontes e documentação |
| DBeaver ou HeidiSQL | Consulta aos dados durante os estudos |

Algumas ferramentas ainda serão configuradas. A tabela descreve a arquitetura pretendida, não uma instalação já concluída.

## Como navegar

- [Ambiente](docs/ambiente.md): preparação, pendências e operação cotidiana.
- [Arquitetura](docs/arquitetura.md): conceitos e caminho de uma operação.
- [Roteiro](docs/roteiro.md): etapas práticas com critérios de conclusão.
- [Diário](docs/diario.md): decisões e evidências da montagem.
- [Créditos](CREDITS.md): projeto de origem e limites de autoria.

## Projeto que tornou este laboratório possível

Créditos a **Felipe Raposo**, autor de [Ambiente Protheus 12 com PostgreSQL ou Microsoft SQL Server](https://bitbucket.org/felipe_raposo/docker-protheus-postgresql-microsoft-sql-server/), referência para a montagem com Docker.

Este repositório contém documentação própria e referências ao projeto original. Não redistribui seus arquivos de construção, imagens, binários ou RPOs da TOTVS. Veja [CREDITS.md](CREDITS.md).

## Escopo de uso

Somente dados fictícios e acesso local. As condições de uso dos produtos e das imagens de terceiros precisam ser verificadas com seus respectivos fornecedores. A Empresa Teste 99 não representa, por si só, autorização de redistribuição dos componentes.

Não há pipeline de publicação de imagens ou implantação automática neste repositório.
