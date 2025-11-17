# 🧠 Lunysse – Sistema de Agendamento Psicológico  
API desenvolvida com **FastAPI**, oferecendo autenticação, gerenciamento de usuários, pacientes e psicólogos, sistema completo de **agendamentos**, geração de **relatórios** e módulo avançado de **análise de risco (ML)**.

Banco utilizado: **`insideout.db`** (SQLite).

---

## 📌 Funcionalidades Principais

### 👥 Autenticação & Controle de Usuários
- Login via **JWT**
- Hash seguro com **bcrypt**
- Dois tipos de perfis:
  - `PSICOLOGO`
  - `PACIENTE`
- Controle de permissões baseado em função (RBAC)
- Acesso restrito a rotas sensíveis (relatórios, análises, pacotes clínicos)

---

## 🗂️ Estrutura do Projeto

/project
│── core/

│ └── database.py

│

│── models/

│ └── models.py

│

│── routers/

│ ├── auth.py


│ ├── patients.py

│ ├── psychologists.py

│ ├── appointments.py

│ ├── requests.py

│ ├── reports.py

│ └── ml_analysis.py

│

│── schemas/

│ └── schemas.py

│

│── services/

│ ├── auth_service.py

│ ├── report_service.py

│ └── ml_services.py

│

│── Utils.py

│── seed_data.py

│── test.py

│── requirements.txt

│── .env

│── insideout.db

└── main.py

---

## 📅 Agendamentos
- Psicólogos visualizam apenas **seus próprios pacientes e agendamentos**  
- Pacientes acessam apenas **suas consultas**
- Criação de consultas com:
  - Validação de conflito de horários
  - Controle de disponibilidade
  - Status automático (`AGENDADO`, `CONCLUIDO`)
- Atualização, cancelamento e listagem de horários
- Total integração com relatórios e análise de risco

---

## 📋 Solicitações
Área dedicada a pedidos de consulta:
- Criação de solicitações
- Aprovação e rejeição
- Status detalhado
- Registro do motivo e observações

---

## 📊 Relatórios Completos
Gerados automaticamente por psicólogo:
- Total de sessões
- Pacientes ativos
- Comparações mensais
- Frequência de comparecimento
- Status dos atendimentos
- Alertas de risco
- Dados utilizados para decisões clínicas

Disponível apenas para **psicólogos autenticados**.

---

## 🤖 Análises com Machine Learning
O módulo ML avalia risco baseado no comportamento do paciente:
- Classificação:
  - 🟥 **Alto risco**
  - 🟧 **Risco moderado**
  - 🟩 **Baixo risco**
- Análise geral dos pacientes do psicólogo
- Análise individual com score numérico
- Algoritmo leve usando **NumPy**

Acesso exclusivo **para psicólogos**.

---

## 🗂 Estrutura do Banco (`insideout.db`)
O arquivo SQLite inclui tabelas com relacionamentos completos:

### **Tabelas:**
- **users** — credenciais e tipo (psicólogo/paciente)
- **patients** — dados pessoais, idade e histórico
- **psychologists** — CRM, especialidade e vínculo
- **appointments** — agendamentos e status
- **requests** — solicitações de atendimento  
- **relatórios virtuais** — gerados dinamicamente

Banco carregado automaticamente pelo SQLAlchemy ao iniciar.

---

## 🛠 Tecnologias Utilizadas
- **FastAPI**
- **SQLAlchemy**
- **SQLite**
- **Pydantic**
- **JWT (python-jose)**
- **Passlib/Bcrypt**
- **Uvicorn**
- **NumPy**
- **dotenv**

---

## ▶️ Como Rodar o Projeto

📍 API: http://127.0.0.1:8000  
📍 Swagger (Documentação): http://127.0.0.1:8000/docs  

---

### 1️⃣ Instalar dependências
```bash```
pip install -r requirements.txt
uvicorn main:app --reload
🧪 Testes Automatizados

O arquivo test.py realiza testes integrados:

Login

Autenticação

Pacientes

Psicólogos

Agendamentos

Solicitações

Relatórios

Análise de risco (ML)

Executar testes:
python test.py
📑 Autor

Desenvolvido por Ana Paula Souza dos Santos Rosa
Projeto: Lunysse / Cuide+ — Sistema Clínico Inteligente
