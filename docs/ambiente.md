# Preparação e operação do laboratório

## Ponto de partida

Docker Desktop com contêineres Linux e backend WSL2. A máquina virtual manual criada anteriormente no Hyper-V não é necessária para este caminho e pode permanecer desligada.

O repositório de referência é o [projeto de Felipe Raposo](https://bitbucket.org/felipe_raposo/docker-protheus-postgresql-microsoft-sql-server/).

A inspeção foi feita no commit:

```text
716bd7919ce33541a40e97eb94042218b4815966
```

A opção examinada está em compose/p12.1.2310-mssql. Ela usa Protheus 12.1.2310 e SQL Server 2022 Developer.

## Verificações antes de iniciar

1. Confirmar a origem, disponibilidade e condições de uso das imagens e componentes.
2. Restringir todas as portas publicadas ao endereço 127.0.0.1.
3. Definir armazenamento persistente para banco, configurações e customizações necessárias.
4. Configurar recursos e inicialização manual, conforme o backend do Docker.
5. Validar o Compose e combinar as orientações para o primeiro acesso.

O Compose original também solicita /dev/mem e a capacidade sys_rawio. A necessidade e a compatibilidade desses acessos no Docker Desktop ainda precisam ser avaliadas; não adicionar modo privilegiado como solução automática.

**Ainda não há um Compose adaptado e validado para execução neste repositório.** Os comandos abaixo são referência para quando essa preparação estiver concluída.

## Entendendo portas

O mapeamento 127.0.0.1:8080:8080 significa: encaminhar a porta 8080 do próprio computador para a porta 8080 do contêiner.

No Compose original examinado:

| Serviço | Portas publicadas |
|---|---|
| SQL Server | 1433 |
| License Server | 8081 |
| DBAccess | 7890 |
| Protheus | 1234, 8080 e 9995 |

A função de cada endpoint deve ser conferida na configuração efetiva da imagem. A publicação de uma porta não comprova que exista um serviço saudável nela.

## Comandos do dia a dia

Execute na pasta do Compose preparado:

```powershell
# Confere a sintaxe sem iniciar serviços.
docker compose config --quiet

# Cria/inicia os serviços; pode baixar imagens.
docker compose up -d

# Mostra o estado dos serviços.
docker compose ps

# Acompanha os logs. Ctrl+C encerra a visualização.
docker compose logs -f

# Para mantendo os contêineres.
docker compose stop

# Retoma os contêineres existentes.
docker compose start
```

Não usar docker compose down como rotina até validar toda a persistência: ele remove contêineres, e arquivos não persistidos podem desaparecer.

## Dados e recuperação

O Compose examinado monta ./volume/data/mssql para os dados do SQL Server e ./volume/data/system_temp para a pasta temporária compartilhada.

Isso não comprova que todo o estado do Protheus esteja preservado. É necessário mapear RPO customizado, configurações e demais arquivos alterados antes de recriar serviços.

Fontes devem ficar sob controle de versão. Bancos e arquivos de execução não devem ser enviados ao GitHub. O procedimento de backup só será considerado pronto depois de um teste de restauração.

## Memória e encerramento

- Desativar a abertura automática do Docker Desktop se o laboratório for usado sob demanda.
- Parar os contêineres ao terminar e encerrar o Docker Desktop.
- Medir consumo antes de ajustar limites; não há consumo real do Protheus medido ainda.
- No WSL2, limites globais afetam outras distribuições também.
- Evitar encerrar todo o WSL indiscriminadamente quando outras tarefas estiverem em execução.

[Docker: backend WSL2](https://docs.docker.com/desktop/features/wsl/) · [Docker: economia de recursos](https://docs.docker.com/desktop/use-desktop/resource-saver/)

## Primeiro acesso

Seguir a orientação recebida para o laboratório: conversar com o responsável técnico antes de abrir o Protheus pela primeira vez. Confirmar criação da Empresa Teste 99, dicionários, menus e acesso para desenvolvimento.

A presença desses recursos na base inicial e a compilação via TDS ainda não foram verificadas.
