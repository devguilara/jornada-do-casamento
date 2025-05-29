# 💍 Planejamento de Casamento - MVP com Java 21 + Spring Boot

## 🌟 Objetivo

Criar uma aplicação web simples onde casais possam organizar e centralizar o planejamento do seu casamento, com foco em:

* Checklist de tarefas
* Ideias de músicas
* Inspirações visuais (imagens)

---

## 🚀 Tecnologias

* **Backend:** Java 21 + Spring Boot 3.x
* **Frontend:** Thymeleaf + Bootstrap 5
* **Banco de dados:** PostgreSQL
* **Upload de imagens:** Sistema de arquivos local (`/uploads/images`) ou Cloudinary (futuramente)

---

## 🔐 Funcionalidades do MVP

### ✅ Autenticação

* Cadastro e login de usuários
* Sessão autenticada com Spring Security

### ✅ Planejamento do Casamento

* Criar um planejamento com data e tema
* Um usuário pode ter **1 planejamento ativo**

### ✅ Checklist

* Adicionar itens
* Marcar como concluído
* Remover itens

### ✅ Músicas

* Adicionar músicas com título, artista e link do Spotify (opcional)

### ✅ Galeria de Inspiração

* Upload de imagens com categoria (vestido, decoração, etc.)
* Listar imagens já enviadas

---

## 🏣 Estrutura de Dados

### Entidade: `User`

* id
* name
* email
* password
* timestamps
* relacionamento: 1-1 com `WeddingPlan`

### Entidade: `WeddingPlan`

* id
* user\_id (FK)
* wedding\_date
* theme
* venue\_type (enum)
* venue\_idea
* timestamps
* relacionamentos:

  * 1-N com `ChecklistItem`
  * 1-N com `MusicIdea`
  * 1-N com `StyleReference`

### Entidade: `ChecklistItem`

* id
* wedding\_plan\_id (FK)
* item
* completed
* notes
* timestamps

### Entidade: `MusicIdea`

* id
* wedding\_plan\_id (FK)
* title
* artist
* spotify\_link
* notes
* timestamps

### Entidade: `StyleReference`

* id
* wedding\_plan\_id (FK)
* image\_path
* category
* notes
* timestamps

### Enum: `VenueType`

* INDOOR
* OUTDOOR
* DESTINATION

---

## 📂 Estrutura Inicial do Projeto

```
src/
├── main/
│   ├── java/com/seuprojeto/
│   │   ├── controller/
│   │   ├── entity/
│   │   ├── repository/
│   │   ├── service/
│   │   └── config/
│   └── resources/
│       ├── templates/
│       └── application.properties
```

---

## 🌐 Rotas Previstas

* `/login` e `/register` (autenticação)
* `/wedding-plans`
* `/checklist`
* `/musics`
* `/gallery`

Todas as rotas estarão protegidas por autenticação.

---

## 🖼️ Upload de Imagens

* Armazenamento local em `/uploads/images` (acessível publicamente)
* Planejamento futuro de uso do Cloudinary ou serviço similar para armazenar as imagens na nuvem

---

## ⚙️ Deploy Recomendado

* [Render.com](https://render.com) (simples e gratuito para MVP)
* Railway
* Fly.io
* Heroku (com buildpack customizado para Java 21)

---

## ✅ Pós-MVP (funcionalidades futuras)

* Suporte a múltiplos planejamentos por usuário
* Colaboração de terceiros (familiares, amigos, organizadores)
* Exportar planejamento como PDF
* Sugestões automáticas com IA (tarefas, músicas, imagens)
* Comentários nas inspirações e músicas
* Timeline visual do casamento
