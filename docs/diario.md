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
