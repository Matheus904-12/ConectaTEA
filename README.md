# 🧩 ConectaTEA - Plataforma de Apoio para Famílias

> Plataforma completa em Node.js/HTML/CSS/JS para apoiar famílias com filhos no espectro autista, oferecendo recursos educacionais, agendamento de consultas com especialistas, autenticação segura via OTP e gestão completa de perfis.

## ✨ Funcionalidades

### 🎯 Para Pais e Famílias
- ✅ **Cadastro e Login** com autenticação OTP via email
- ✅ **Agendamento de Consultas** com especialistas
- ✅ **Gestão de Perfil** (CRUD completo)
- ✅ **Recursos Educacionais** para apoio
- ✅ **Atividades Terapêuticas** personalizadas
- ✅ **Dashboard** com histórico de consultas

### 👨‍⚕️ Para Especialistas
- ✅ **Dashboard Profissional** completo e elegante
- ✅ **Gerenciamento de Pacientes** com prontuários digitais
- ✅ **Agenda Integrada** com calendário visual
- ✅ **Google Meet** integrado para consultas online
- ✅ **Chat em tempo real** com pacientes
- ✅ **Sistema de Reuniões** com histórico
- ✅ **Estatísticas e Métricas** do consultório

### 🛠️ Tecnologias
- **Backend**: Node.js + Express
- **Database Dev**: SQLite (automático, zero config)
- **Database Prod**: PostgreSQL (Supabase, grátis)
- **Autenticação**: JWT + OTP via email (Nodemailer)
- **Real-time**: Socket.IO (chat)
- **Segurança**: bcryptjs, prepared statements
- **Frontend**: HTML5, CSS3, JavaScript ES6+, Font Awesome 6.4.0
- **Deploy**: Vercel (frontend + serverless backend)

## 🚀 Como Rodar Localmente

### Requisitos
- **Node.js** 18+ e npm 9+
- **Git**
- **Conta Gmail** para envio de emails OTP

### Instalação

1. **Clone o repositório**
```bash
git clone https://github.com/Conecta-TEA/ConectaTEA.git
cd ConectaTEA
```

2. **Instalar dependências**
```bash
cd backend
npm install
```

3. **Configurar variáveis de ambiente**

Crie o arquivo `backend/.env`:
```env
EMAIL_USER=seu_email@gmail.com
EMAIL_PASS=sua_senha_app_gmail
JWT_SECRET=seu_segredo_jwt_aqui
SESSION_SECRET=seu_segredo_sessao_aqui
```

**⚠️ Gmail App Password**: 
1. Acesse: https://myaccount.google.com/security
2. Ative: Verificação em 2 etapas
3. Gere App Password em: https://myaccount.google.com/apppasswords
4. Use os 16 dígitos em `EMAIL_PASS`

4. **Iniciar servidor**
```bash
npm start
```

O banco SQLite será criado automaticamente em `backend/conectatea.db`

5. **Abrir frontend**
```bash
# Instale Live Server no VS Code
# Clique com botão direito em index.html
# "Open with Live Server"
# Acesse: http://localhost:5500
```

### Acesso de demonstração

Não mantenha credenciais padrão em documentação pública nem reutilize senhas de demonstração em produção. Para testar localmente, crie uma conta de desenvolvimento ou use o mecanismo de seed do ambiente local; antes de publicar, confirme que nenhuma conta administrativa padrão continua ativa.

## 📁 Estrutura do Projeto

```
ConectaTEA/
├── backend/
│   ├── config/
│   │   ├── database-sqlite.js      # SQLite (desenvolvimento)
│   │   ├── database-postgres.js    # PostgreSQL (produção)
│   │   └── db-selector.js          # Seletor automático
│   ├── routes/
│   │   ├── auth-simple.js          # Autenticação + OTP
│   │   ├── especialista.js         # API Dashboard Especialista
│   │   ├── usuarios.js             # Gerenciamento usuários
│   │   ├── chat.js                 # Chat em tempo real
│   │   └── mensagens.js            # Sistema de mensagens
│   ├── .env                        # Variáveis ambiente (criar)
│   ├── server.js                   # Servidor Express + Socket.IO
│   └── package.json
├── css/
│   ├── style.css                   # Estilos globais
│   ├── painel-especialista.css     # Dashboard especialista
│   └── ...
├── js/
│   ├── config.js                   # Configuração ambiente
│   ├── painel-especialista.js      # Lógica dashboard
│   └── ...
├── index.html                      # Página inicial
├── painel-especialista.html        # Dashboard especialista
├── vercel.json                     # Config deploy Vercel
├── DEPLOY-15MIN.md                 # Guia rápido deploy
├── DEPLOY-VERCEL-GRATIS.md         # Guia completo deploy
├── CHECKLIST-DEPLOY.md             # Checklist deploy
└── README.md                       # Este arquivo
```

## 🎨 Design

O projeto possui um **design elegante e premium** com:
- 🎨 Paleta sofisticada (Azul marinho #1e3a8a + Dourado #B8956F)
- ✨ Animações suaves e transições elegantes
- 📱 100% responsivo (mobile-first)
- ♿ Acessível (WCAG 2.1)
- 🌙 Interface limpa e profissional
- 💎 Cards com glassmorphism
- 🎯 UX otimizada para especialistas

## 🔐 Segurança

- ✅ **Autenticação OTP** via email (sem senha no login)
- ✅ **Senhas criptografadas** com bcryptjs (10 salt rounds)
- ✅ **Tokens JWT** com expiração de 7 dias
- ✅ **Códigos OTP** de uso único (10 minutos de validade)
- ✅ **Prepared statements** (proteção SQL injection)
- ✅ **Validação de sessão** em todas as requisições
- ✅ **Auditoria completa** de ações no banco
- ✅ **CORS configurado** para domínios permitidos

## 🗄️ Banco de Dados

O projeto usa **dual-database** (automático):
- **Desenvolvimento**: SQLite (zero config, arquivo local)
- **Produção**: PostgreSQL (Supabase, 500MB grátis)

O sistema detecta automaticamente qual usar baseado na variável `DATABASE_URL`.

### Tabelas Principais
- **usuarios**: Pacientes, especialistas e admins
- **otp_codes**: Códigos de verificação (6 dígitos)
- **especialista_pacientes**: Relação especialista-paciente
- **reunioes**: Agendamentos + Google Meet
- **prontuarios**: Prontuários digitais
- **mensagens**: Chat em tempo real
- **sessoes**: Tokens JWT ativos

Veja SQL completo em: `DEPLOY-VERCEL-GRATIS.md`

## 📧 Sistema de Emails

Envio automático de emails HTML estilizados para:

### OTP de Cadastro
```
Assunto: "Bem-vindo ao ConectaTEA - Verifique seu Email"
Conteúdo: Código de 6 dígitos (válido por 10 min)
```

### OTP de Login
```
Assunto: "Seu Código de Acesso - ConectaTEA"
Conteúdo: Código de 6 dígitos (válido por 10 min)
```

Todos com design elegante matching da plataforma.

## 🔌 API Endpoints

### Autenticação
- `POST /api/auth/cadastrar` - Criar nova conta
- `POST /api/auth/verificar-email` - Verificar código de cadastro
- `POST /api/auth/login/solicitar-otp` - Solicitar código de login
- `POST /api/auth/login/verificar-otp` - Fazer login com OTP
- `POST /api/auth/reenviar-otp` - Reenviar código
- `POST /api/auth/logout` - Fazer logout (protegido)

### Usuários
- `GET /api/usuarios` - Listar usuários (admin)
- `GET /api/usuarios/:id` - Buscar por ID
- `PUT /api/usuarios/:id` - Atualizar perfil
- `DELETE /api/usuarios/:id` - Deletar (admin)
- `POST /api/usuarios/alterar-senha` - Alterar senha

### Consultas
- `POST /api/consultas` - Agendar consulta
- `GET /api/consultas` - Listar minhas consultas
- `GET /api/consultas/:id` - Detalhes da consulta
- `PUT /api/consultas/:id` - Atualizar/reagendar
- `PUT /api/consultas/:id/cancelar` - Cancelar consulta
- `DELETE /api/consultas/:id` - Deletar (admin)

Documentação completa em `backend/README.md`

## � Deploy (100% GRÁTIS)

O projeto está configurado para deploy **totalmente gratuito** na Vercel + Supabase!

### ⚡ Opção 1: Deploy Rápido (15 minutos)
```bash
📖 Siga o guia: DEPLOY-15MIN.md
```

### 📚 Opção 2: Deploy Completo (com todos os detalhes)
```bash
📖 Siga o guia: DEPLOY-VERCEL-GRATIS.md
```

### ✅ Opção 3: Checklist Passo a Passo
```bash
📖 Siga o guia: CHECKLIST-DEPLOY.md
```

### 🛠️ Infraestrutura
- **Frontend**: Vercel (CDN global, SSL automático)
- **Backend**: Vercel Serverless Functions
- **Database**: Supabase PostgreSQL (500MB grátis)
- **CI/CD**: GitHub → Vercel (deploy automático)

### 💰 Limites Free Tier
- ✅ 100GB bandwidth/mês (Vercel)
- ✅ 500MB database (Supabase)
- ✅ 2GB bandwidth database/mês
- ✅ Deployments ilimitados
- ✅ SSL automático
- ✅ Suficiente para milhares de usuários!

**Custo total: R$ 0,00/mês** 🎯

## 👤 Usuário Admin Padrão

Criado automaticamente no banco:
- **Email**: admin@conectatea.com.br
- **Senha**: admin123
- **Tipo**: admin

⚠️ **IMPORTANTE**: Altere a senha após primeiro acesso!

## 🎯 Próximos Passos

### Curto Prazo (em desenvolvimento)
- [ ] Integrar páginas frontend com API backend
- [ ] CRUD de Especialistas (controller + rotas)
- [ ] CRUD de Recursos (controller + rotas)
- [ ] Upload de fotos de perfil (multer)
- [ ] Sistema de notificações por email
- [ ] Filtros e busca avançada

### Médio Prazo
- [ ] Dashboard com estatísticas (gráficos)
- [ ] Chat em tempo real (Socket.io)
- [ ] Sistema de avaliações de especialistas
- [ ] Calendário de disponibilidade
- [ ] Aplicativo PWA (Progressive Web App)
- [ ] Integração com Google Calendar

### Longo Prazo
- [ ] App mobile nativo (React Native / Flutter)
- [ ] IA para recomendações personalizadas
- [ ] Videochamadas integradas (WebRTC/Jitsi)
- [ ] Gamificação com badges e conquistas
- [ ] Multi-idioma (i18n)
- [ ] Marketplace de conteúdo premium

## 📄 Licença

Verifique o arquivo `LICENSE` para detalhes.

## 💙 Contribuindo

Contribuições são bem-vindas! Por favor:
1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

## 🆘 Suporte

- **Email**: suporte@conectatea.com.br (exemplo)
- **Issues**: [GitHub Issues](https://github.com/Conecta-TEA/ConectaTEA/issues)
- **Documentação**: Em construção

---

**Desenvolvido com 💙 para ajudar famílias**

## Segurança e configuração

Não versione arquivos de ambiente de produção nem senhas. Configure `DATABASE_URL`, `JWT_SECRET`, `SESSION_SECRET`, `EMAIL_USER`, `EMAIL_PASS` e demais variáveis diretamente no ambiente de hospedagem. Use um arquivo `.env` local ignorado pelo Git e consulte [`.env.example`](.env.example) para conhecer os nomes das variáveis. Se credenciais anteriores foram publicadas, rotacione-as no provedor: apagar um arquivo não limpa o histórico Git.
