# API REST - Sistema de Museus (JAX-RS)

Camada de serviços RESTful desenvolvida com **JAX-RS (Jersey)**. O objetivo desta API é permitir que sistemas externos (aplicativos móveis, totens, parceiros) integrem-se ao sistema de agendamento sem acoplamento com a interface visual.

## Regras de Negócio e Privacidade
* A API reutiliza a camada `DAO` e `Model` do sistema principal, garantindo consistência de dados.
* **Privacidade:** Dados sensíveis como **CPF** e **E-mail** são ocultados automaticamente nas respostas JSON (anotação `@JsonbTransient`), em conformidade com os requisitos de segurança.

## Endpoints Disponíveis

**Base URL:** `http://localhost:8080/JAX-RS/api`

### 1. Listar Museus
Retorna a lista de todos os museus disponíveis.
* **Método:** `GET`
* **URL:** `/museus`
* **Exemplo:** `GET /api/museus`

### 2. Buscar Agendamento Específico
Busca os detalhes de um agendamento pelo código de confirmação.
* **Método:** `GET`
* **URL:** `/agendamentos/{codigo}`
* **Exemplo:** `GET /api/agendamentos/ABC1234`

### 3. Listar Agendamentos (Com Filtros)
Permite buscar agendamentos de um museu específico em uma data específica.
* **Método:** `GET`
* **URL:** `/agendamentos?museu={id}&data={yyyy-mm-dd}`
* **Exemplo:** `GET /api/agendamentos?museu=1&data=2026-01-20`

### 4. Listar Pessoas do Agendamento
Retorna apenas a lista de visitantes vinculados a um código.
* **Método:** `GET`
* **URL:** `/agendamentos/{codigo}/pessoas`
* **Exemplo:** `GET /api/agendamentos/ABC1234/pessoas`

### 5. Cancelar Agendamento
Realiza o cancelamento (exclusão) do agendamento e libera as vagas.
* **Método:** `DELETE`
* **URL:** `/agendamentos/{codigo}`
* **Exemplo:** `DELETE /api/agendamentos/ABC1234`

## Tecnologias
* Jersey 3.1.5 (JAX-RS Implementation)
* Hibernate Core 6.4.4
* Jakarta JSON Binding
