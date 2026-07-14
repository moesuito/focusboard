# FocusBoard 🚀 — O Desafio de IAs (Local vs Nuvem)

Este repositório foi preparado para um desafio especial de desenvolvimento de software que será apresentado em um vídeo no canal do **YouTube**. O objetivo é testar e comparar as habilidades de três modelos de inteligência artificial na construção de uma aplicação completa (Full-stack) a partir de um briefing detalhado.

---

## 🏆 O Desafio

O propósito central deste projeto é avaliar a capacidade técnica de um **modelo de IA local rodando direto na máquina** contra os **modelos proprietários de nuvem mais poderosos do mercado**. 

Será avaliado como cada IA lida com arquitetura modular, integrações de banco de dados, persistência determinística no Kanban (drag and drop), testes automatizados e a entrega de uma experiência de usuário (UX) premium com tema claro/escuro.

### 🧠 Os Modelos em Teste:
1. **Gemini 3.5 Flash** (Nuvem - Google)
2. **GPT 5.6 Sol** (Nuvem - OpenAI)
3. **Ornish 1.0 35B** (Local - Rodando direto na máquina do usuário)

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
* **Banco de Dados**: PostgreSQL executado localmente via Docker Compose.
* **Qualidade e Testes**: 
  * Backend: pytest
  * Frontend: Vitest e Testing Library
  * Fluxo Principal (E2E): Playwright

---

## 📦 Como Executar a Base do Projeto

### Pré-requisitos
* Docker & Docker Compose
* Python 3.12+
* Node.js (v20+)

### 1. Banco de Dados
Suba o container do PostgreSQL em segundo plano:
```bash
docker-compose up -d
```

### 2. Backend
1. Entre na pasta `backend`, crie e ative seu ambiente virtual Python (`.venv`).
2. Instale as dependências: `pip install -r requirements.txt`.
3. Configure o `.env` com base no `.env.example`.
4. Execute as migrations: `alembic upgrade head`.
5. Inicie o servidor: `uvicorn app.main:app --reload`.

### 3. Frontend
1. Entre na pasta `frontend` e instale as dependências: `npm install`.
2. Inicie o servidor de desenvolvimento do Vite: `npm run dev`.

---

## 📝 Licença

Este projeto e seu código de comparação são licenciados sob a **Licença Apache 2.0**.
