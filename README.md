# 💍 Planejamento de Casamento - MVP com Laravel

## 🎯 Objetivo

Criar uma aplicação web simples onde casais possam organizar e centralizar o planejamento do seu casamento, com foco em:

- Checklist de tarefas
- Ideias de músicas
- Inspirações visuais (imagens)

---

## 🚀 Tecnologias

- **Backend:** PHP 8+ com Laravel 10
- **Frontend:** Blade + Bootstrap 5
- **Banco de dados:** MySQL ou PostgreSQL
- **Upload de imagens:** Filesystem local (public/images) ou Cloudinary (futuramente)

---

## 🔐 Funcionalidades do MVP

### ✅ Autenticação
- Cadastro e login de usuários (Laravel Breeze)

### ✅ Planejamento do Casamento
- Criar um planejamento com data e tema
- Um usuário pode ter **1 planejamento ativo**

### ✅ Checklist
- Adicionar itens
- Marcar como concluído
- Remover itens

### ✅ Músicas
- Adicionar músicas com título, artista e link do Spotify (opcional)

### ✅ Galeria de Inspiração
- Upload de imagens com categoria (vestido, decoração, etc.)
- Listar imagens já enviadas

---

## 🗃️ Estrutura de Dados

### Tabela: `users`

| Campo      | Tipo    |
|------------|---------|
| id         | bigint  |
| name       | string  |
| email      | string  |
| password   | string  |
| timestamps | ✔       |

### Tabela: `wedding_plans`

| Campo         | Tipo    |
|---------------|---------|
| id            | bigint  |
| user_id       | FK      |
| wedding_date  | date    |
| theme         | string  |
| venue_type    | enum    |
| venue_idea    | text    |
| timestamps    | ✔       |

### Tabela: `checklist_items`

| Campo            | Tipo     |
|------------------|----------|
| id               | bigint   |
| wedding_plan_id  | FK       |
| item             | string   |
| completed        | boolean  |
| notes            | text     |
| timestamps       | ✔        |

### Tabela: `music_ideas`

| Campo            | Tipo     |
|------------------|----------|
| id               | bigint   |
| wedding_plan_id  | FK       |
| title            | string   |
| artist           | string   |
| spotify_link     | string   |
| notes            | text     |
| timestamps       | ✔        |

### Tabela: `style_references`

| Campo            | Tipo     |
|------------------|----------|
| id               | bigint   |
| wedding_plan_id  | FK       |
| image_path       | string   |
| category         | string   |
| notes            | text     |
| timestamps       | ✔        |

---

## 🛠️ Comandos Úteis

### Criar projeto
```bash
composer create-project laravel/laravel wedding-planner
```
## Instalar autenticação simples (Laravel Breeze)
```bash
composer require laravel/breeze --dev
php artisan breeze:install
npm install && npm run dev
php artisan migrate
```
## Criar models, migrations e controllers 
```
php artisan make:model WeddingPlan -mcr
php artisan make:model ChecklistItem -mcr
php artisan make:model MusicIdea -mcr
php artisan make:model StyleReference -mcr
```
## 🖼️ Upload de Imagens

- Usar Storage::put() para salvar imagens em public/images

- Alternativa futura: integração com Cloudinary

## 🌐 Rotas

```php
Route::middleware(['auth'])->group(function () {
    Route::resource('wedding-plans', WeddingPlanController::class);
    Route::resource('checklist', ChecklistItemController::class);
    Route::resource('musics', MusicIdeaController::class);
    Route::resource('gallery', StyleReferenceController::class);
});
```
## 📦 Deploy Recomendado
- Render.com (grátis e simples)

- Laravel Forge (produção, pago)

- Umbler / HostGator (PHP hosting simples)

- XAMPP ou Laragon (ambiente local)


## ✅ Pós-MVP (para considerar depois)

- Múltiplos planejamentos por usuário

- Colaboração de terceiros (convidados)

- Exportar PDF do planejamento

- IA para sugestões automáticas (músicas, imagens, tarefas)



