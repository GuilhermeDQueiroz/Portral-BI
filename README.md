# 📊 Portal BI

Uma interface web moderna, responsiva e segura desenvolvida para servir como portal de acesso a painéis analíticos corporativos (Power BI). O projeto cria uma camada de autenticação antes de liberar a visualização dos dados consolidados, garantindo que apenas usuários autorizados tenham acesso ao dashboard logístico.

## ✨ Funcionalidades

- **Autenticação Segura:** Login validado em tempo real utilizando o Supabase Auth.
- **Injeção Dinâmica de Relatórios:** A URL do Power BI não fica exposta no código-fonte; ela é consumida diretamente de uma tabela segura do banco de dados após o login.
- **Interface Moderna (UI/UX):** Design limpo focado na experiência do usuário, construído com Tailwind CSS, incluindo feedback visual de carregamento (Loading Overlay).
- **Proteção de Rota:** Redirecionamento automático e limpeza de sessão ao sair (Logout) ou ao encontrar falhas de permissão.

## 🚀 Tecnologias Utilizadas

- **Frontend:** HTML5, Vanilla JavaScript, Tailwind CSS (via CDN)
- **Tipografia e Estilo:** Fonte M PLUS 1 (Google Fonts) e paleta de cores customizada (Brand Gold).
- **Backend as a Service (BaaS):** [Supabase](https://supabase.com/) (PostgreSQL + Auth)
- **Business Intelligence:** Microsoft Power BI (Publicação na Web / Iframe)

## 🛠️ Como configurar e rodar o projeto

### Pré-requisitos
Para testar o projeto localmente, você precisará de:
- Uma conta no [Supabase](https://supabase.com/).
- Um relatório do [Power BI](https://powerbi.microsoft.com/) publicado na web.
- Uma extensão de servidor local, como o **Live Server** (no VS Code).

### Passo 1: Configuração do Supabase
1. Crie um novo projeto no Supabase.
2. Vá em **Authentication** e habilite o provedor de E-mail. Crie um usuário de teste (ex: `usuario@empresa.com.br`).
3. Vá em **Table Editor** e crie uma nova tabela chamada `configuracoes`.
4. Adicione uma coluna chamada `powerbi_url` (tipo `text`).
5. Insira uma nova linha na tabela e cole o link do seu relatório do Power BI (o link gerado em *Arquivo > Inserir relatório > Publicar na Web*) na coluna `powerbi_url`.

### Passo 2: Configuração do Código
No arquivo `1Dash.html`, localize a seção de scripts do Supabase e insira as chaves do seu projeto:
```javascript
const supabaseUrl = 'SUA_URL_DO_SUPABASE_AQUI';
const supabaseKey = 'SUA_CHAVE_ANON_PUBLICA_AQUI';
