# 📑 DailyFlow

O **DailyFlow** é uma proposta de aplicação voltada para gerenciamento de tarefas, priorização e foco no que realmente importa ao longo do dia.

## 📄 Documento de Requisitos
https://docs.google.com/document/d/1oY7eoWRsa-WV7VpNvzUEvwIRX4zUyUREqpoIYzAKJ-A/edit?usp=sharing

## ⚙️ Funcionalidades

* Organização por prioridade
* Foco em tarefas principais
* Rotina de fechamento diário
* Interface limpa e objetiva

## 🚀 Novas Implementações


### 🗄️ Modelo de Dados (DDL)
O banco de dados foi estruturado para garantir integridade e performance. Abaixo, a definição das tabelas principais:

```sql
-- Estrutura para Usuários e Tarefas
CREATE TABLE usuarios (
    id_usuario SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    senha_hash VARCHAR(255) NOT NULL
);

CREATE TABLE tarefas (
    id_tarefa SERIAL PRIMARY KEY,
    id_usuario INTEGER NOT NULL,
    titulo VARCHAR(150) NOT NULL,
    prioridade INTEGER CHECK (prioridade IN (1, 2, 3)), -- 1: Alta, 2: Média, 3: Baixa
    status VARCHAR(20) DEFAULT 'pendente',
    data_agendada DATE NOT NULL,
    CONSTRAINT fk_usuario FOREIGN KEY (id_usuario) REFERENCES usuarios(id_usuario)
);
```

## 👨‍💻 Autores

Ana Clara Alves,
Wendell Gabryel,
Karla Cristine,
Luiz Felipe,
Matheus Leal.
