# AGENTS.md — FocusBoard

## Instrução principal

Leia e siga integralmente a skill mestre `.agents/skills/squad/SKILL.md` como orquestradora desta implementação.

Use o fluxo completo do Squad para planejar, delegar, implementar, testar, revisar, documentar e validar o projeto. Leia e acione as skills especialistas indicadas pela orquestradora em cada fase.

Este documento já contém todas as decisões de kickoff aprovadas pelo usuário. Não interrompa a execução para confirmar stack, arquitetura, banco, escopo ou fluxo de Git. Registre essas decisões em `.squad/config.yaml`, crie `.squad/memory.md` e inicie a implementação.

Implemente somente o escopo descrito neste briefing. Não adicione funcionalidades além dele.

## Produto

Crie o **FocusBoard**, um gerenciador pessoal de tarefas executado localmente no navegador.

O sistema deve permitir organizar tarefas em projetos, acompanhar o andamento por quadro Kanban e consultar um resumo de produtividade.

## Decisões técnicas aprovadas

- Arquitetura: monólito modular em camadas.
- Backend: Python 3.12, FastAPI, Pydantic, SQLAlchemy e Alembic.
- Frontend: React, TypeScript, Vite e Tailwind CSS.
- Estado remoto: TanStack Query.
- Formulários: React Hook Form com validação por schema.
- Drag and drop: dnd-kit.
- Banco: PostgreSQL.
- Ambiente local: PostgreSQL nativo instalado no Windows.
- Testes backend: pytest.
- Testes frontend: Vitest e Testing Library.
- Teste de fluxo principal: Playwright.
- Idioma do código: inglês.
- Idioma da interface e documentação: português do Brasil.
- Git: GitHub Flow com Conventional Commits.

## Escopo funcional

### Projetos

Permitir:

- listar projetos;
- criar projeto com nome, descrição e cor;
- editar projeto;
- excluir projeto mediante confirmação;
- abrir o quadro de tarefas de um projeto.

### Tarefas

Cada tarefa deve possuir:

- título;
- descrição opcional;
- projeto;
- status;
- prioridade;
- data de vencimento opcional;
- data de criação;
- data de atualização.

Status disponíveis:

- backlog;
- a fazer;
- em andamento;
- concluída.

Prioridades disponíveis:

- baixa;
- média;
- alta;
- urgente.

Permitir:

- criar, visualizar, editar e excluir tarefas;
- mover tarefas entre as colunas por drag and drop;
- reordenar tarefas dentro da mesma coluna;
- persistir status e ordenação no banco;
- marcar e reabrir tarefas;
- pesquisar por título e descrição;
- filtrar por projeto, status, prioridade e vencimento.

### Dashboard

Exibir dados reais do banco:

- quantidade de projetos;
- tarefas abertas;
- tarefas concluídas;
- tarefas atrasadas;
- distribuição por status;
- próximas tarefas a vencer.

### Interface

Criar uma interface moderna, limpa e responsiva contendo:

- navegação lateral;
- dashboard inicial;
- página de projetos;
- quadro Kanban;
- modal ou painel lateral para edição de tarefa;
- estados de carregamento, vazio, sucesso e erro;
- confirmações para ações destrutivas;
- tema claro e escuro com preferência persistida no navegador;
- acessibilidade básica para teclado, foco e controles com ícones.

## Backend e API

Crie uma API REST versionada em `/api/v1` com documentação OpenAPI.

Organize o backend em módulos claros para configuração, banco, modelos, schemas, repositórios, serviços e rotas.

A lógica de negócio deve permanecer fora das rotas.

Implemente:

- validação de entrada;
- respostas e códigos HTTP consistentes;
- tratamento centralizado de erros;
- migrations;
- health check;
- CORS restrito ao frontend local;
- logs úteis;
- timestamps em UTC;
- paginação na listagem geral de tarefas;
- filtros processados pela API.

## Persistência

Modele corretamente projetos e tarefas, incluindo relacionamento, índices relevantes, restrições e exclusão consistente.

A ordenação do Kanban deve possuir representação persistente e determinística no banco.

Crie uma migration inicial e dados de demonstração por comando explícito de seed.

## Testes e validação

Crie testes suficientes para validar:

- CRUD de projetos;
- CRUD de tarefas;
- validações;
- filtros e pesquisa;
- movimentação e reordenação no Kanban;
- dashboard;
- estados principais da interface;
- integração do frontend com a API;
- fluxo completo de criar projeto, criar tarefa, mover tarefa, atualizar a página e confirmar a persistência.

Antes de concluir, execute e corrija:

- migrations em banco vazio;
- testes do backend;
- testes do frontend;
- teste Playwright principal;
- lint;
- typecheck;
- build de produção;
- prova de vida da API e do frontend conforme o procedimento da skill `squad`.

## Entrega

Entregue o projeto funcionando a partir da raiz do repositório, com:

- estrutura de backend e frontend;
- scripts simples para setup, desenvolvimento, testes e seed compatíveis com Windows;
- `.env.example` sem segredos;
- `.gitignore` adequado;
- README com instalação, execução, testes, migrations, seed, arquitetura e solução de problemas;
- documentação mantida pelo `squad-docs`;
- revisão final pelo `squad-code-review`;
- commits convencionais produzidos pelo fluxo do `squad-git`.

Ao finalizar, apresente um relatório objetivo com o que foi implementado, comandos de execução, verificações realmente executadas, resultados e limitações encontradas.

Comece agora lendo `.agents/skills/squad/SKILL.md`, registrando o plano em `.squad/memory.md` e executando o projeto até a validação final.
