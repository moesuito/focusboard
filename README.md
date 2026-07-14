# FocusBoard 🚀 — O Desafio de IAs (Local vs Nuvem)

---

## 📂 O Projeto: FocusBoard

O **FocusBoard** é um gerenciador pessoal de tarefas executado localmente no navegador. A aplicação permite organizar fluxos de trabalho em múltiplos projetos, gerenciar tarefas por meio de um quadro Kanban dinâmico e acompanhar estatísticas de produtividade através de um Dashboard integrado.

### Requisitos Funcionais Definidos:

* **Projetos**: CRUD completo de projetos, permitindo customização de nomes, descrições e cores identificadoras.
* **Tarefas (Kanban)**: Criação, edição e exclusão de tarefas organizadas por status (*Backlog, A Fazer, Em Andamento, Concluída*) e prioridades (*Baixa, Média, Alta, Urgente*), com suporte a arrastar e soltar (Drag and Drop) persistido de forma determinística no banco.
* **Dashboard**: Painel dinâmico exibindo a quantidade de projetos ativos, tarefas abertas, concluídas, atrasadas, gráficos de distribuição e alerta de vencimentos próximos.
* **Interface**: Design limpo, moderno, responsivo, com navegação fluida, acessibilidade básica e suporte a Tema Claro e Tema Escuro persistido no navegador.

---

## 📐 Tecnologias & Arquitetura Definidas

Para garantir uma comparação justa, todos os modelos devem seguir a mesma stack tecnológica e a mesma estrutura arquitetural aprovada:

* **Arquitetura**: Monólito Modular estruturado em camadas no Backend (Models, Schemas, Repositories, Services e Rotas) com separação de conceitos.
* **Backend (API REST em `/api/v1`)**: Python 3.12, FastAPI, SQLAlchemy (ORM), Alembic (Migrations) e validação com Pydantic.
* **Frontend**: React (Vite), TypeScript, Tailwind CSS, TanStack Query (Estado Remoto) e `dnd-kit` (Kanban).
* **Banco de Dados**: SQLite (persistido em arquivo local).
* **Qualidade e Testes**: 
  * Backend: pytest
  * Frontend: Vitest e Testing Library
  * Fluxo Principal (E2E): Playwright

---

## 📝 Licença

Este projeto e seu código de comparação são licenciados sob a **Licença Apache 2.0**.
