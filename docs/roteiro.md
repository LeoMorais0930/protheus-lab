# Roteiro de aprendizado

Cada etapa deve gerar uma evidência: uma anotação, um fonte, uma consulta ou um teste reproduzível. Os itens são planejamento, não funcionalidades já entregues.

## 1. Ambiente e arquitetura

- [ ] Entender o papel de cada serviço.
- [ ] Iniciar e parar o laboratório conscientemente.
- [ ] Encontrar logs e identificar falhas de conexão.
- [ ] Validar persistência e recuperação.

**Concluído quando:** conseguimos explicar o caminho da interface ao banco e retomar o ambiente sem perder os dados de teste.

## 2. Configurador e modelo de dados

- [ ] Explorar empresa, filial e compartilhamento.
- [ ] Consultar SX2, SX3, SIX e parâmetros.
- [ ] Entender menus, usuários e permissões.
- [ ] Relacionar uma tela com os dados que ela utiliza.

**Concluído quando:** conseguimos localizar um campo e explicar sua definição, armazenamento e contexto de filial.

## 3. Primeiro programa

- [ ] Configurar VS Code e TDS.
- [ ] Confirmar ambiente e autorização de compilação.
- [ ] Criar uma função que exiba uma mensagem.
- [ ] Compilar, executar e depurar com breakpoint.

**Concluído quando:** uma alteração no fonte produz o efeito esperado e conseguimos acompanhar sua execução.

## 4. Projeto prático: equipamentos de TI

Criar progressivamente um cadastro com patrimônio, descrição e situação.

- [ ] Definir tabela e campos pelo processo apropriado.
- [ ] Criar consulta e interface de cadastro.
- [ ] Validar obrigatoriedade e duplicidade.
- [ ] Testar permissões, contexto de filial e falhas de gravação.

**Concluído quando:** dados válidos persistem, entradas inválidas são rejeitadas e erros não deixam alterações parciais.

## 5. Rotinas padrão e customização

- [ ] Estudar cadastro de produtos e movimentos de estoque.
- [ ] Acompanhar pedidos e documentos em cenários fictícios.
- [ ] Conferir resultados com consultas SQL.
- [ ] Implementar uma extensão por ponto de entrada documentado.
- [ ] Explorar MVC e REST após dominar o fluxo básico.

Os códigos de rotinas e mecanismos disponíveis devem ser confirmados na release utilizada.

## Como avaliar código gerado com IA

Verificar o objetivo de negócio, entradas, empresa/filial, permissões, transações e comportamento em erro. Comparar resultado esperado com os dados reais do laboratório.

Não considerar a compilação como teste completo. Guardar os fontes e explicar as decisões importantes no histórico.

## SQL para investigação

Começar por SELECT e consultar o dicionário antes de supor nomes ou relacionamentos.

Em tabelas Protheus convencionais, observar o marcador de exclusão lógica D_E_L_E_T_ e o contexto de filial. Não adotar DELETE ou UPDATE direto como substitutos das rotinas de negócio.

Quando uma junção duplicar linhas, investigar chaves e cardinalidade. Usar TOP 1 sem critério não corrige automaticamente um relacionamento incorreto.
