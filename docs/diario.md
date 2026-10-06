# Diário do laboratório

## 2026-10-06 — Preparação

### Objetivo definido

Aprender Protheus desde a estrutura até o desenvolvimento de rotinas, com base fictícia e execução sob demanda.

### Decisões

- Usar Docker Desktop com WSL2.
- Manter desligada a VM manual criada inicialmente.
- Priorizar SQL Server para aproximar os exercícios do contexto profissional.
- Utilizar o projeto de Felipe Raposo como referência, com crédito explícito.
- Publicar documentação própria; manter dados e componentes proprietários fora deste repositório.

### Evidências

- Docker Engine respondeu ao comando de versão.
- A listagem de contêineres estava vazia na verificação inicial.
- README e Compose do projeto original apontam para Protheus 12.1.2310.
- docker compose config --quiet validou a sintaxe do Compose MSSQL.
- O Compose apresentou aviso de atributo version obsoleto.
- Ainda não foram executados os serviços do laboratório durante esta revisão.

### Próximos passos

1. Resolver a escolha da release: referência disponível 2310 versus sugestão inicial 2510.
2. Ajustar acesso local e persistência.
3. Validar imagens, recursos e compatibilidade no Docker Desktop.
4. Iniciar os serviços e verificar logs.
5. Alinhar o primeiro acesso com o responsável técnico.

## 2026-10-06 — Configuração PostgreSQL preparada

- Prioridade alterada para PostgreSQL, por escolha do usuário.
- Imagens inspecionadas: Protheus 2510, PostgreSQL 16, DBAccess 24.1.1.1 e License Server 3.7.0.
- Criado Compose próprio com digests fixados, senhas locais ignoradas pelo Git, limites de RAM e restart desativado.
- PostgreSQL publicado em 127.0.0.1:15432 devido ao conflito com a porta 5432 existente.
- Confirmadas as novas variáveis PROTHEUS_* e a porta interna 1234 do WebApp.
- Ajustado core ulimit para a exigência das builds TOTVS; nenhum ajuste global de kernel ou modo privilegiado foi necessário para iniciar os processos.
- Confirmados healthcheck do banco, encoding/collation, SELECT 1 por ODBC e conectividade TCP entre componentes.
- Recriado o AppServer com volume persistente. O arquivo custom.rpo ainda está vazio; compilação não foi testada. O AppServer altera sua própria configuração durante o funcionamento, portanto o checksum do INI não permaneceu idêntico.
- License Server permaneceu em execução, mas registrou erros de comunicação/liberação e falta de licenseserverinstall.ini. Funcionamento da Empresa 99 ainda não validado.
- Nenhum login no ERP foi feito. Os quatro serviços foram parados ao final para liberar memória.

Próxima etapa: revisar a pendência de licenciamento com o responsável técnico antes do primeiro acesso. Backup/restauração e desenvolvimento ADVPL continuam pendentes.
