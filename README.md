# Projeto: Planejamento de Casamento

## Visão Geral

O projeto tem como objetivo fornecer uma plataforma onde noivos e noivas podem planejar seu casamento antes de contratar fornecedores como cerimonialistas e outros serviços. A ideia é criar um espaço onde eles possam registrar ideias, tomar decisões e organizar todos os detalhes do casamento, desde a escolha do tema até a seleção de músicas e decoração.

## Público-alvo

- **Noivas e noivos** que estão na fase de planejamento do casamento.
- **Casais em busca de ideias** e que ainda estão decidindo temas, cores e outros detalhes importantes do evento.

## Funcionalidades do MVP

1. **Cadastro de Usuário**: Permitir que noivos e noivas se registrem na plataforma.
2. **Planejamento do Casamento**:
   - Registro de dados como a data do casamento, tema, tipo de local (fechado, aberto ou ambos).
   - Escolha de cores para o evento (vestidos, decoração, etc.).
   - Adição de ideias e referências de estilo (como imagens).
   - Checklist de tarefas para o casamento.
3. **Músicas**: Permitir que os usuários adicionem músicas que desejam tocar no casamento, incluindo links para o Spotify.
4. **Galeria de Inspirações**: Um espaço onde os noivos podem pesquisar e salvar imagens e ideias para o evento.
5. **Armazenamento e Acompanhamento**: Os usuários podem ver e editar suas informações a qualquer momento.

---

## Stack Tecnológica Recomendado

- **Frontend**:
  - **React**: Biblioteca JavaScript para a construção da interface do usuário.
  - **Bootstrap / Material UI**: Frameworks para estilização rápida e responsiva.
- **Backend**:
  - **Node.js com Express**: Framework para criar a API RESTful.
  - **MongoDB**: Banco de dados NoSQL para armazenamento das informações.
- **Autenticação**:
  - **JWT (JSON Web Tokens)**: Para autenticação de usuários.
- **Armazenamento de Imagens**:
  - **Cloudinary** ou **Amazon S3**: Para armazenamento de imagens carregadas.
- **Hospedagem e Deploy**:
  - **Heroku** ou **Vercel**: Para deploy do backend e frontend.

---

## Roadmap para Versões Futuras

### Versão 1.0 - MVP
- Cadastro de usuários.
- Criação e edição de planos de casamento.
- Checklist básico.
- Galeria de ideias (imagens).
- Adicionar músicas à lista de preferidas.
- Armazenamento de dados no banco de dados.

### Versão 2.0 - Funcionalidades Avançadas
- Integração com o **Spotify** para facilitar a adição de músicas.
- Busca e filtro de imagens na galeria.
- Funcionalidade de notificação (e-mail ou push) para lembrar de tarefas e decisões importantes.

### Versão 3.0 - Expansão e Personalização
- Adicionar parceiros e fornecedores no planejamento (como cerimonialistas, fotógrafos, etc.).
- Compartilhamento de planos com amigos e familiares para feedback.
- Integração com **Google Calendar** para marcar datas importantes.

---

## Modelo de Dados (MVP)

### 🧑‍💼 Tabela: `Users`

| Campo         | Tipo / Descrição                          |
|---------------|-------------------------------------------|
| `id`          | UUID – Identificador único do usuário     |
| `name`        | String – Nome completo                    |
| `email`       | String – Email (único)                    |
| `password_hash` | String – Senha criptografada           |
| `created_at`  | Timestamp – Data de criação               |
| `updated_at`  | Timestamp – Última atualização            |

---

### 💍 Tabela: `WeddingPlans`

| Campo         | Tipo / Descrição                                                  |
|---------------|-------------------------------------------------------------------|
| `id`          | UUID – Identificador único do plano                              |
| `user_id`     | UUID – Chave estrangeira, referência a `Users(id)`               |
| `wedding_date`| Date – Data planejada do casamento                                |
| `theme`       | String – Tema do casamento                                        |
| `venue_type`  | Enum('indoor', 'outdoor', 'both') – Tipo de local (fechado, aberto, ambos) |
| `venue_idea`  | Text – Ideias gerais de local                                     |
| `created_at`  | Timestamp                                                         |
| `updated_at`  | Timestamp                                                         |

---

### ☑️ Tabela: `ChecklistItems`

| Campo            | Tipo / Descrição                                         |
|------------------|----------------------------------------------------------|
| `id`             | UUID – Identificador único                               |
| `wedding_plan_id`| UUID – Chave estrangeira para `WeddingPlans(id)`        |
| `item`           | String – Nome do item (ex: "Vestido", "Buffet", etc.)    |
| `completed`      | Boolean – Está concluído?                                |
| `notes`          | Text – Observações do item                               |
| `created_at`     | Timestamp                                                |

---

### 🎵 Tabela: `MusicIdeas`

| Campo            | Tipo / Descrição                                         |
|------------------|----------------------------------------------------------|
| `id`             | UUID – Identificador único                               |
| `wedding_plan_id`| UUID – Referência ao plano                               |
| `title`          | String – Nome da música                                  |
| `artist`         | String – Nome do artista                                 |
| `spotify_link`   | String – URL do Spotify (opcional)                       |
| `notes`          | Text – Observações adicionais                            |
| `created_at`     | Timestamp                                                |

---

### 🎨 Tabela: `StyleReferences`

| Campo            | Tipo / Descrição                                         |
|------------------|----------------------------------------------------------|
| `id`             | UUID – Identificador único                               |
| `wedding_plan_id`| UUID – Referência ao plano                               |
| `image_url`      | String – Caminho da imagem (upload ou link)              |
| `category`       | String – Ex: “Vestido”, “Decoração”, “Flores”, etc.     |
| `notes`          | Text – Anotações sobre o estilo                          |
| `created_at`     | Timestamp                                                |

---

## Wireframe Visual Básico

### 1. **Página Inicial**
- **Navbar** com opções de login e registro.
- **Botões de navegação** para "Criar novo planejamento", "Ver meus planos" e "Iniciar planejamento".
- **Área de destaque** para apresentar o propósito do aplicativo.

### 2. **Página de Planejamento**
- Formulários para:
  - Escolher a data do casamento.
  - Definir o tema e tipo de local.
  - Adicionar imagens inspiradoras.
  - Checklist de tarefas.

### 3. **Página de Músicas**
- Lista de músicas já escolhidas com a possibilidade de adicionar novas, incluindo link para Spotify.

### 4. **Página de Galeria**
- Exibição de imagens categorizadas (vestidos, decoração, etc.) com opção de salvar imagens no planejamento.

---

## Como Implementar

1. **Frontend**:
   - Utilizar **React** com **Material UI** ou **Bootstrap** para criar uma interface interativa e responsiva.
   - O **Context API** pode ser usado para gerenciar o estado global da aplicação (como dados do usuário e planejamento).
   - **Axios** para fazer as requisições HTTP para o backend.
   
2. **Backend**:
   - Criar uma **API RESTful** utilizando **Node.js com Express** para gerenciar a lógica de negócio e conectar ao banco de dados MongoDB.
   - Utilizar **JWT** para autenticação de usuários e garantir que apenas usuários autenticados possam acessar seus planos.
   
3. **Banco de Dados**:
   - Criar o esquema de dados no **MongoDB** com as tabelas e documentos conforme o modelo de dados descrito acima.

4. **Hospedagem**:
   - O **frontend** pode ser hospedado em plataformas como **Vercel** ou **Netlify**, enquanto o **backend** pode ser hospedado no **Heroku** ou **AWS**.

---

## Conclusão

Este é o planejamento completo para o projeto de **Planejamento de Casamento**. A ideia é criar uma plataforma intuitiva, simples e organizada onde os noivos possam estruturar todos os aspectos do casamento antes de contratar fornecedores, focando na personalização e controle do evento.
