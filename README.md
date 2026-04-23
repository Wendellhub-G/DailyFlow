# 🌊 DailyFlow - Minimalismo Cognitivo e Foco Diário

O **DailyFlow** é uma aplicação voltada para o gerenciamento de tarefas com foco na redução da carga cognitiva. Através de uma interface limpa e uma hierarquia de prioridades rígida, o sistema auxilia o usuário a focar apenas no que é essencial, eliminando distrações e organizando o encerramento do ciclo diário.

---

## 🔗 Links do Projeto
* **Documentação Completa:** [Docs](https://docs.google.com/document/d/1oY7eoWRsa-WV7VpNvzUEvwIRX4zUyUREqpoIYzAKJ-A/edit?usp=sharing)
* **Protótipo Interativo:** [Figma](https://www.figma.com/make/CtTk5ShQVF6ADDUKI9SG7I/DailyFlow---primeiro-prot%C3%B3tipo?fullscreen=1&t=fJmaFzj89iuXlIXJ-1&preview-route=%2Fregister)

---

## 🚀 Novas Implementações

* **Fluxo de Registro Multistep:** Cadastro organizado em etapas (Informações Básicas, Contato e Objetivos).
* **Sistema de Login Flexível:** Acesso via e-mail ou telefone.
* **Onboarding de Boas-vindas:** Tela de saudação personalizada para criação da primeira tarefa.
* **Perfil do Usuário:** Nova tela com dados cadastrais (Data de Nascimento, Sexo, Endereço opcional) e métricas de foco.
* **Estado Zero Realista:** O dashboard agora inicia totalmente limpo, exibindo apenas tarefas reais criadas pelo usuário.

---

## ⚙️ Funcionalidades Principais
* **Organização por Prioridade:** Classificação em Foco Principal, Secundário e Terciário.
* **Lógica de Ocultação:** Tarefas de menor prioridade ficam ocultas para evitar sobrecarga visual.
* **Rotina de Fechamento:** Modal interativo ao fim do dia para decidir o destino das tarefas pendentes.
* **Calendário Nativo:** Seletor de data de nascimento otimizado para facilitar o registro.

---

## 🗄️ Modelo de Dados Atualizado (DDL)
O banco de dados foi expandido para suportar os novos campos de perfil e o fluxo de autenticação:

```sql
-- Tabela de Usuários (Registro Completo)
CREATE TABLE usuarios (
    id_usuario SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    data_nascimento DATE NOT NULL,
    sexo VARCHAR(20), -- Masculino, Feminino
    email VARCHAR(100) UNIQUE NOT NULL,
    telefone VARCHAR(20) NOT NULL,
    senha_hash VARCHAR(255) NOT NULL,
    endereco VARCHAR(255), -- Campo Opcional
    objetivo_foco TEXT,
    data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Tabela de Tarefas
CREATE TABLE tarefas (
    id_tarefa SERIAL PRIMARY KEY,
    id_usuario INTEGER NOT NULL,
    titulo VARCHAR(150) NOT NULL,
    descricao TEXT,
    prioridade INTEGER CHECK (prioridade IN (1, 2, 3)), -- 1: Principal, 2: Secundária, 3: Terciária
    status VARCHAR(20) DEFAULT 'pendente', -- pendente, concluida, descartada, adiada
    data_agendada DATE NOT NULL,
    criado_em TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT fk_usuario FOREIGN KEY (id_usuario) REFERENCES usuarios(id_usuario) ON DELETE CASCADE
);
```

---

## 👥 Autores
* Ana Clara Alves
* Wendell Gabryel
* Karla Cristine
* Luiz Felipe
* Matheus Leal

