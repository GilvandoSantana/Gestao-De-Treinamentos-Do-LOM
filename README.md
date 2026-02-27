# Guia de Deploy para o seu Site (Railway/Render)

Este guia detalha os passos para realizar o deploy do seu site, uma aplicação React com backend Node.js e banco de dados MySQL, em plataformas como Railway ou Render, garantindo que ele fique acessível de forma permanente.

## 1. Estrutura do Projeto

O projeto possui a seguinte estrutura principal:

- `client/`: Contém o código frontend (React).
- `server/`: Contém o código backend (Node.js/Express).
- `drizzle/`: Contém as configurações e migrações do Drizzle ORM para o MySQL.
- `package.json`: Define as dependências e scripts do projeto.
- `Dockerfile`: Configuração para containerizar a aplicação.
- `.env.example`: Exemplo das variáveis de ambiente necessárias.

## 2. Pré-requisitos

Antes de iniciar o deploy, certifique-se de ter:

- Uma conta nas plataformas **Railway** (recomendado) ou **Render**.
- Um repositório Git (GitHub, GitLab, Bitbucket) para o seu projeto.

## 3. Configuração do Banco de Dados MySQL

Seu site utiliza um banco de dados MySQL. Tanto a Railway quanto a Render oferecem serviços de banco de dados gerenciados. Siga os passos abaixo para configurar o seu:

### Na Railway:

1.  No seu projeto Railway, clique em `New` -> `Database` -> `MySQL`.
2.  Após a criação, a Railway fornecerá automaticamente uma variável de ambiente `DATABASE_URL` com a string de conexão. Você precisará usar essa URL.

### Na Render:

1.  No seu dashboard Render, clique em `New` -> `MySQL`.
2.  Configure o nome e a região do seu banco de dados.
3.  Após a criação, a Render fornecerá as credenciais (host, porta, usuário, senha, nome do banco). Você precisará construir a `DATABASE_URL` no formato `mysql://user:password@host:port/database`.

## 4. Variáveis de Ambiente (`.env`)

Seu projeto requer as seguintes variáveis de ambiente para funcionar corretamente. Crie um arquivo `.env` na raiz do seu projeto com base no `.env.example` e preencha com os valores apropriados:

```env
VITE_APP_ID=
JWT_SECRET=
DATABASE_URL="mysql://user:password@host:port/database" # Preencha com a URL do seu banco de dados
OAUTH_SERVER_URL=
OWNER_OPEN_ID=
BUILT_IN_FORGE_API_URL=
BUILT_IN_FORGE_API_KEY=
```

**Importante:**

- `DATABASE_URL`: Essencial para a conexão com o MySQL. Preencha com a string de conexão obtida da Railway ou Render.
- `JWT_SECRET`: Uma chave secreta para segurança. Gere uma string aleatória forte (ex: usando `openssl rand -base64 32`).
- As outras variáveis (`VITE_APP_ID`, `OAUTH_SERVER_URL`, `OWNER_OPEN_ID`, `BUILT_IN_FORGE_API_URL`, `BUILT_IN_FORGE_API_KEY`) podem ser deixadas em branco ou preenchidas conforme a necessidade da sua aplicação. Se o site não usar funcionalidades de OAuth ou Forge API, elas não serão críticas para o funcionamento básico.

## 5. Deploy na Railway (Recomendado)

A Railway é uma excelente opção para este tipo de projeto devido à sua facilidade de uso e integração com bancos de dados.

1.  **Crie um novo projeto:** No dashboard da Railway, clique em `New Project`.
2.  **Conecte seu repositório Git:** Escolha `Deploy from Git Repo` e conecte sua conta GitHub/GitLab/Bitbucket. Selecione o repositório do seu site.
3.  **Adicione o serviço do site:** A Railway detectará automaticamente o `Dockerfile` e o `package.json`. Ela tentará construir e rodar sua aplicação. Se não detectar automaticamente, você pode adicionar um novo serviço e escolher `Docker Image` ou `Node.js`.
4.  **Configure as variáveis de ambiente:** Vá para as configurações do seu serviço (Settings -> Variables) e adicione as variáveis do seu arquivo `.env` (exceto `DATABASE_URL`, que a Railway já deve ter configurado para o seu banco de dados MySQL).
5.  **Migrações do Banco de Dados:** Seu projeto usa Drizzle ORM. Você precisará rodar as migrações para criar as tabelas no seu banco de dados. Isso pode ser feito de algumas maneiras:
    - **Manual:** Conecte-se ao seu banco de dados MySQL (usando um cliente como DBeaver ou MySQL Workbench) e execute os arquivos SQL localizados em `drizzle/migrations/`.
    - **Script de Deploy:** Adicione um script de deploy na Railway que execute `pnpm db:push` (ou `npx drizzle-kit push:mysql`) após o build. Isso pode ser configurado em `Service Settings` -> `Lifecycle` -> `Deploy Command`.
6.  **Aguarde o Deploy:** A Railway fará o build da sua imagem Docker e iniciará o serviço. Você poderá acompanhar o progresso nos logs.
7.  **Acesse seu Site:** Uma vez que o deploy for concluído, a Railway fornecerá uma URL pública para o seu site.

## 6. Deploy na Render (Alternativa)

A Render também é uma ótima alternativa e segue um processo similar.

1.  **Crie um novo Web Service:** No dashboard da Render, clique em `New` -> `Web Service`.
2.  **Conecte seu repositório Git:** Conecte sua conta Git e selecione o repositório do seu site.
3.  **Configure o serviço:**
    - **Build Command:** `pnpm install && pnpm build`
    - **Start Command:** `pnpm start`
    - **Root Directory:** Se o seu `package.json` estiver na raiz, deixe em branco. Caso contrário, especifique o diretório (ex: `/home/ubuntu/site`).
4.  **Variáveis de Ambiente:** Vá para `Environment` e adicione as variáveis do seu arquivo `.env`, incluindo a `DATABASE_URL` que você construiu.
5.  **Migrações do Banco de Dados:** Similar à Railway, você precisará executar as migrações do Drizzle ORM. Você pode adicionar um comando de migração no `Start Command` ou executá-lo manualmente.
6.  **Aguarde o Deploy:** A Render fará o build e deploy da sua aplicação. Acompanhe os logs para verificar o status.
7.  **Acesse seu Site:** A Render fornecerá uma URL pública para o seu site após o deploy.

## 7. Próximos Passos

- **Testar:** Após o deploy, teste todas as funcionalidades do seu site para garantir que tudo está funcionando como esperado, especialmente as que dependem do banco de dados.
- **Monitoramento:** Configure o monitoramento na plataforma escolhida para acompanhar a saúde e o desempenho da sua aplicação.
- **Domínio Personalizado:** Se desejar, você pode configurar um domínio personalizado para o seu site nas configurações da Railway ou Render.

Com este guia, você terá seu site rodando de forma permanente e escalável!
