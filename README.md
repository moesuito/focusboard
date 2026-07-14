# FocusBoard

O **FocusBoard** é um gerenciador pessoal de tarefas executado localmente no navegador, projetado para ajudar você a organizar tarefas em projetos, acompanhar o andamento de fluxos de trabalho por meio de um quadro Kanban dinâmico e monitorar sua produtividade através de um painel de controle (Dashboard) completo.

---

## 🚀 Funcionalidades Principais

### 📂 Projetos
* **Gerenciamento Completo**: Crie, liste, edite e exclua projetos (com confirmação de segurança).
* **Personalização**: Defina nome, descrição e cores exclusivas para identificar facilmente cada projeto.
* **Foco**: Abra o quadro Kanban dedicado de qualquer projeto com um clique.

### 📋 Tarefas (Kanban)
* **Atributos Ricos**: Cada tarefa possui título, descrição opcional, projeto associado, prioridade, status, data de vencimento opcional, além de rastreamento de criação e atualização em UTC.
* **Prioridades**: Organize por urgência (Baixa, Média, Alta, Urgente).
* **Status do Fluxo**: Controle o ciclo de vida da tarefa pelos estados:
  * Backlog
  * A fazer
  * Em andamento
  * Concluída
* **Drag and Drop (Arrastar e Soltar)**: Movimentação fluida de tarefas entre colunas e reordenação interna utilizando `dnd-kit`.
* **Persistência Determinística**: A ordem exata e o status do Kanban são salvos diretamente no banco de dados.
* **Busca e Filtros Avançados**: Pesquise por termos no título ou descrição e filtre por projeto, status, prioridade ou data de vencimento.

### 📊 Dashboard de Produtividade
Acompanhe métricas reais agregadas do banco de dados:
* Total de projetos ativos.
* Quantidade de tarefas abertas e concluídas.
* Identificação de tarefas atrasadas.
* Gráfico de distribuição de tarefas por status.
* Lista de próximas tarefas prestes a vencer.

### 🎨 Interface Moderna & Responsiva
* Design premium, limpo, fluido e responsivo.
* Tema Claro (Light Mode) e Escuro (Dark Mode) persistidos no navegador.
* Painel lateral de navegação intuitivo.
* Janelas modais e painéis laterais de edição rápida.
* Suporte a acessibilidade básica via teclado, controle de foco e ícones intuitivos.

---

## 🛠️ Stack Tecnológica

### Backend (API REST Versionada em `/api/v1`)
* **Linguagem**: Python 3.12
* **Framework**: FastAPI (com documentação OpenAPI/Swagger automática)
* **ORM (Persistência)**: SQLAlchemy com migrations gerenciadas pelo Alembic
* **Validação**: Pydantic v2
* **Banco de Dados**: PostgreSQL
* **Testes**: pytest

### Frontend (SPA)
* **Linguagem**: TypeScript
* **Biblioteca**: React 18+ (Scaffoldado com Vite)
* **Estilização**: Tailwind CSS
* **Gerenciamento de Estado Remoto**: TanStack Query (React Query)
* **Formulários**: React Hook Form com validação integrada via schema
* **Arrastar e Soltar**: dnd-kit
* **Testes**: Vitest & React Testing Library

### Infraestrutura e Testes de Fluxo
* **Ambiente Local**: Docker & Docker Compose
* **Testes E2E (Fluxo Principal)**: Playwright

---

## 📐 Arquitetura

O backend do FocusBoard segue uma arquitetura de **Monólito Modular em Camadas**, estruturado da seguinte forma:

```
backend/
├── app/
│   ├── core/           # Configurações globais, segurança e logs
│   ├── database/       # Conexão, sessão e configurações do SQLAlchemy
│   ├── models/         # Modelos de dados do banco de dados (SQLAlchemy)
│   ├── schemas/        # Schemas de validação e serialização (Pydantic)
│   ├── repositories/   # Camada de persistência e acesso a dados (SQL/ORM)
│   ├── services/       # Regras de negócio da aplicação (fora das rotas)
│   └── api/            # Controladores e rotas divididos por versão (/v1)
```

O frontend é composto por componentes modulares e estruturado por páginas, separando a camada de chamadas de API (`services`) e gerenciamento de estado (`hooks`).

---

## 📦 Como Executar o Projeto Localmente

### Pré-requisitos
* **Docker & Docker Compose** instalados.
* **Python 3.12** e gerenciador de pacotes configurado.
* **Node.js** (versão 20 ou superior).

---

### Passo 1: Configurando o Banco de Dados (PostgreSQL via Docker)
Suba o container do PostgreSQL em segundo plano:
```bash
docker-compose up -d
```

---

### Passo 2: Configurando o Backend
1. Navegue até a pasta do backend:
   ```bash
   cd backend
   ```
2. Crie e ative um ambiente virtual Python:
   ```bash
   python -m venv .venv
   # No Windows (PowerShell):
   .venv\Scripts\Activate.ps1
   # No Linux/macOS:
   source .venv/bin/activate
   ```
3. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```
4. Crie o arquivo `.env` com base no arquivo de exemplo `.env.example`:
   ```bash
   cp .env.example .env
   ```
5. Execute as migrations para criar a estrutura das tabelas no banco de dados:
   ```bash
   alembic upgrade head
   ```
6. Opcionalmente, popule o banco de dados com dados fictícios de demonstração (seed):
   ```bash
   python seed.py
   ```
7. Inicie o servidor do backend:
   ```bash
   uvicorn app.main:app --reload
   ```
   A documentação da API estará disponível em `http://localhost:8000/docs`.

---

### Passo 3: Configurando o Frontend
1. Abra um novo terminal e navegue até a pasta do frontend:
   ```bash
   cd frontend
   ```
2. Instale as dependências com o npm:
   ```bash
   npm install
   ```
3. Crie o arquivo `.env` local caso necessário (apontando para a URL da API, ex: `VITE_API_URL=http://localhost:8000/api/v1`).
4. Inicie o servidor de desenvolvimento:
   ```bash
   npm run dev
   ```
5. Abra o navegador no endereço indicado (normalmente `http://localhost:5173`).

---

## 🧪 Como Executar os Testes

### Testes do Backend (pytest)
```bash
cd backend
pytest
```

### Testes do Frontend (Vitest)
```bash
cd frontend
npm run test
```

### Testes de Integração E2E (Playwright)
```bash
# Na raiz ou na pasta de testes E2E
npx playwright test
```

---

## 📝 Licença

Este projeto é licenciado sob a **Licença Apache 2.0**. Consulte o arquivo [LICENSE](LICENSE) para obter mais detalhes.
