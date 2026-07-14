# FocusBoard 🚀

O **FocusBoard** é um projeto experimental criado para comparar a capacidade de diferentes modelos de inteligência artificial em uma tarefa completa de desenvolvimento de software.

Todos os modelos recebem o mesmo briefing, o mesmo conjunto de instruções e o mesmo harness de agentes. A partir disso, cada um deve planejar, implementar, testar e finalizar o projeto de forma autônoma.

## Sobre o projeto

O FocusBoard é um gerenciador local de projetos e tarefas, executado diretamente no navegador.

A aplicação permite:

- Criar, editar e excluir projetos;
- Organizar tarefas em um quadro Kanban;
- Arrastar tarefas entre colunas;
- Definir prioridade, prazo e tags;
- Pesquisar e filtrar tarefas;
- Acompanhar estatísticas em um dashboard;
- Alternar entre tema claro e escuro;
- Manter todos os dados salvos localmente.

## Stack definida

### Backend

- Python 3.12
- FastAPI
- SQLAlchemy
- Pydantic
- Alembic
- SQLite
- Pytest

### Frontend

- React
- TypeScript
- Vite
- Tailwind CSS
- TanStack Query
- dnd-kit
- Vitest
- Testing Library

## Execução

O projeto foi pensado para rodar nativamente no Windows, sem Docker e sem Electron.

O backend é executado localmente, o frontend abre no navegador e os dados ficam persistidos em um banco SQLite no próprio computador.

## Objetivo do desafio

O objetivo não é apenas verificar qual modelo gera a interface mais bonita, mas avaliar a capacidade de cada um em:

- Interpretar um briefing;
- Planejar a arquitetura;
- Integrar frontend, backend e banco de dados;
- Implementar funcionalidades completas;
- Criar testes;
- Corrigir os próprios erros;
- Manter consistência durante uma tarefa longa;
- Entregar um projeto realmente executável.

## Harness

O projeto utiliza o **Squad**, um harness de agentes responsável por organizar o trabalho em etapas de planejamento, implementação, revisão, testes e validação.

As instruções completas do desafio ficam no arquivo [`AGENTS.md`](./AGENTS.md).

## Licença

Este projeto está licenciado sob a [Licença Apache 2.0](./LICENSE).
