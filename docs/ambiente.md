# Ambiente local: Protheus 2510 + PostgreSQL 16

## Estado verificado em 2026-10-06

O Compose da raiz inicia as quatro imagens fixadas por versão e digest. PostgreSQL passou no healthcheck; SELECT 1 funcionou via ODBC dentro do contêiner DBAccess com o usuário da aplicação. O banco usa WIN1252, collation C e ctype pt_BR.CP1252. As portas TCP dos serviços responderam. RPO padrão e arquivos de systemload estão presentes.

Nenhum login no ERP ou compilação ADVPL foi realizado. O License Server iniciou, mas registrou erros de comunicação/liberação e ausência de licenseserverinstall.ini. O acesso funcional à Empresa 99 e o licenciamento ainda precisam de validação com o responsável técnico.

## Versões

| Serviço | Imagem |
|---|---|
| Protheus | feliperaposo/protheus:p12.1.2510 |
| PostgreSQL | feliperaposo/protheus-postgresql:16 |
| DBAccess | feliperaposo/protheus-dbaccess:24.1.1.1 |
| License Server | feliperaposo/protheus-license:3.7.0 |

Créditos a [Felipe Raposo](../CREDITS.md). O checkout original tinha Compose da 2310; os arquivos internos das imagens novas foram inspecionados para elaborar esta configuração.

## Preparar em outra máquina

1. Instalar Docker Desktop com backend WSL2.
2. Copiar `.env.example` para `.env`.
3. Preencher duas senhas distintas, aleatórias e alfanuméricas. Os scripts das imagens interpolam valores em SQL e sed; esse formato evita caracteres problemáticos.
4. Executar `docker compose config --quiet`.
5. Executar `docker compose up -d` e conferir os logs.

O `.env` local é ignorado pelo Git. Não publique esse arquivo nem a saída completa de `docker compose config`, que inclui as senhas resolvidas. Alterar o `.env` após inicializar o banco não muda automaticamente as credenciais existentes.

## Acessos locais

| Uso | Endereço |
|---|---|
| WebApp, após orientação do primeiro acesso | http://localhost:8080 |
| TDS / AppServer | localhost:1234, ambiente P12 |
| Monitor do License Server | http://localhost:8081 |
| PostgreSQL | localhost:15432, banco e usuário protheus |

As portas publicadas usam 127.0.0.1. O DBAccess fica apenas na rede interna do Compose. A porta 15432 evita conflito com um banco já existente no computador de montagem.

Na imagem 2510, WebApp e AppServer compartilham a porta interna 1234. A porta 8080 externa aponta para ela. O WebApp do License Server 3.7.0 também usa 1234 internamente.

A senha SQL é PROTHEUS_PASSWORD no `.env`; ela não é uma senha de login do ERP. As imagens novas usam PROTHEUS_DB, PROTHEUS_USER e PROTHEUS_PASSWORD, não os nomes antigos DB_Name, DB_User e DB_Password.

## Recursos sob demanda

| Serviço | Limite de RAM |
|---|---|
| PostgreSQL | 768 MiB |
| License Server | 512 MiB |
| DBAccess | 256 MiB |
| AppServer | 3 GiB |

Total: 4,5 GiB de limites, sem contar Docker, kernel, caches e outros programas. Não são reservas fixas nem requisitos oficiais. A amostra inicial dos quatro contêineres sem usuários ficou próxima de 550 MiB; o consumo durante uso ainda não foi medido.

O Compose usa `restart: "no"`. A inicialização do Docker Desktop e os limites globais do WSL não foram alterados. Ao terminar, pare os serviços; Docker e WSL podem manter consumo próprio enquanto ativos.

As imagens TOTVS exigiram core ulimit ilimitado. Isso foi ajustado por contêiner, sem alterar fs.file-max global, habilitar modo privilegiado ou conceder /dev/mem. Eventuais core dumps podem ocupar disco e conter dados; não os publique.

## Operação cotidiana

Na pasta deste repositório:

```powershell
docker compose start
docker compose ps
docker compose logs --tail 50
docker compose stop
```

Use `docker compose up -d` na primeira criação ou depois de alterar o Compose; `start` só retoma contêineres existentes.

## Persistência

- postgres_data: banco em /var/lib/postgresql/data.
- protheus_files: árvore /protheus12, incluindo configurações, RPO e dados.
- license_files: árvore /protheus12 do License Server.

São volumes Docker, não a pasta ./data do guia inicial. Não execute `docker compose down -v` nem exclua os volumes: isso apaga os dados persistidos. Mantenha fontes no Git separadamente. Backup e restauração completos ainda não foram testados.

Como o volume completo do Protheus também contém binários, trocar a tag não atualiza automaticamente seus arquivos. Atualizações de release exigem procedimento específico.

## Primeiro acesso e REST

O AppServer extrai os pacotes antes de iniciar. A configuração remove JOBS=HTTPJOB para não executar o job REST de negócio antes do primeiro acesso orientado; portas REST não são publicadas.

Conversar com o responsável técnico antes do primeiro login. Confirmar Empresa 99, dicionários, menus e compilação. Serviços internos de monitoramento podem inicializar recursos do framework; isso não valida as rotinas do ERP.
