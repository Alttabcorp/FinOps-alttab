# 💰 FinOps API

> **Sistema de Organização Financeira Pessoal e Familiar**

Uma API robusta para gestão financeira que substitui planilhas Excel tradicionais, oferecendo controle manual inteligente com interface moderna e acessível.

## 📋 Sobre o Projeto

O **FinOps** é uma aplicação completa para organização financeira pessoal e familiar que digitaliza e moderniza o controle financeiro tradicional. O sistema funciona com **entrada manual de dados** e **indicações percentuais**, seguindo uma metodologia estruturada de gestão de recursos.

### 🎯 Problema Resolvido

- **Dificuldade** de usar planilhas Excel em dispositivos móveis
- **Necessidade** de colaboração financeira entre casais e grupos
- **Falta** de visualizações claras e automáticas dos dados
- **Demanda** por interface intuitiva sem complexidade excessiva
- **Independência** de conexões bancárias ou APIs externas

### 🔑 Diferenciais

- ✅ **Controle Total**: Entrada manual de dados, sem conexões bancárias
- ✅ **Múltiplos Modelos**: Suporte para diferentes tipos de organização financeira
- ✅ **Colaborativo**: Gestão compartilhada para casais e famílias
- ✅ **Metodologia Estruturada**: Fluxo lógico baseado em percentuais
- ✅ **Multi-plataforma**: Web e Mobile com sincronização

## 🚀 Funcionalidades Principais

### 💼 Modelos de Organização Suportados

#### 1. **Renda Conjunta** (Padrão)
- Casais que juntam todas as rendas
- Divisão 50/50 após todas as alocações
- Gestão unificada de recursos

#### 2. **Divisão Splitwise**
- Divisão justa de gastos compartilhados
- Cálculo automático de acertos mensais
- Histórico de quem deve o quê

#### 3. **Organização Individual**
- Para repúblicas e pessoas solteiras
- Cada pessoa responsável por suas contas
- Divisão apenas de gastos compartilhados

#### 4. **Contas Separadas + Fundo Comum**
- Autonomia financeira com despesas essenciais compartilhadas
- Contribuição fixa para fundo comum
- Privacidade total no restante

### 📊 Metodologia de Gestão Financeira

1. **Receitas**: Registro manual de todas as entradas mensais
2. **Gastos Fixos**: Dedução de despesas obrigatórias
3. **Custos Variáveis**: Alocação percentual automática
4. **Poupança**: Indicação percentual para reservas
5. **Investimentos**: Sugestões percentuais (sem acompanhamento automático)
6. **Gastos Livres**: Cálculo e divisão do saldo restante

### 🛠 Funcionalidades da API

- **Autenticação JWT** com refresh tokens
- **Gestão de Usuários e Grupos** (casais, famílias, repúblicas)
- **CRUD de Transações** (receitas e despesas)
- **Sistema de Categorias** hierárquico e personalizável
- **Cálculos Automáticos** baseados em metodologia percentual
- **Relatórios e Análises** financeiras
- **Sistema de Metas** e acompanhamento de objetivos
- **Backup e Sincronização** de dados
- **Suporte Multi-tenant** para diferentes organizações

## 🏗 Arquitetura

### Stack Tecnológico

#### Backend
```
- Runtime: Node.js 18+ com TypeScript
- Framework: Express.js
- ORM: Prisma
- Banco: PostgreSQL 14+
- Cache: Redis 6+
- Auth: JWT + bcrypt
- Validação: Zod
- Testes: Jest + Supertest
- Docs: Swagger/OpenAPI
```

#### Infraestrutura
```
- Containerização: Docker + Docker Compose
- Proxy: Nginx
- SSL: Let's Encrypt
- CI/CD: GitHub Actions
- Cloud: AWS/GCP/DigitalOcean
```

### Estrutura do Projeto

```
src/
├── controllers/          # Controladores da API
├── services/            # Lógica de negócio
├── repositories/        # Acesso a dados
├── models/             # Modelos do Prisma
├── middleware/         # Middlewares personalizados
├── utils/              # Utilitários e helpers
├── config/             # Configurações
├── types/              # Tipos TypeScript
└── __tests__/          # Testes automatizados
```

## 📊 Modelo de Dados

### Entidades Principais

- **Usuario**: Pessoa física que utiliza o sistema
- **Grupo**: Agrupamento de usuários (casal, família, república)
- **Conta**: Contas bancárias, carteiras, investimentos
- **Categoria**: Classificação hierárquica de transações
- **Transacao**: Movimentações financeiras (entrada/saída)
- **Orcamento**: Planejamento por categoria/período
- **Meta**: Objetivos de poupança ou investimento

### Relacionamentos

- Usuario ↔ Grupo (N:M) - Múltiplos grupos por usuário
- Usuario → Conta (1:N) - Múltiplas contas por usuário
- Conta → Transacao (1:N) - Histórico de movimentações
- Categoria → Transacao (1:N) - Classificação de gastos
- Usuario → Orcamento (1:N) - Planejamentos individuais/grupos

## 🚀 Como Executar

### Pré-requisitos

- Node.js 18+
- PostgreSQL 14+
- Redis 6+
- Docker (opcional)

### Instalação

1. **Clone o repositório**
```bash
git clone https://github.com/Alttabcorp/finops-api.git
cd finops-api
```

2. **Instale as dependências**
```bash
npm install
```

3. **Configure as variáveis de ambiente**
```bash
cp .env.example .env
# Edite o arquivo .env com suas configurações
```

4. **Execute as migrações**
```bash
npx prisma migrate dev
npx prisma generate
```

5. **Inicie o servidor**
```bash
# Desenvolvimento
npm run dev

# Produção
npm run build
npm start
```

### Docker (Alternativo)

```bash
# Desenvolvimento
docker-compose up -d

# Produção
docker-compose -f docker-compose.prod.yml up -d
```

## 📚 Documentação da API

### Endpoints Principais

```
# Autenticação
POST /api/auth/login
POST /api/auth/register
POST /api/auth/refresh
POST /api/auth/logout

# Usuários
GET /api/users/profile
PUT /api/users/profile
GET /api/users/groups

# Grupos
POST /api/groups
GET /api/groups/:id
PUT /api/groups/:id
POST /api/groups/:id/members

# Transações
GET /api/transactions
POST /api/transactions
PUT /api/transactions/:id
DELETE /api/transactions/:id

# Categorias
GET /api/categories
POST /api/categories
PUT /api/categories/:id

# Relatórios
GET /api/reports/monthly
GET /api/reports/categories
GET /api/reports/goals
```

### Swagger UI
Acesse `http://localhost:3000/api-docs` para documentação interativa.

## 🧪 Testes

```bash
# Executar todos os testes
npm test

# Testes em modo watch
npm run test:watch

# Cobertura de testes
npm run test:coverage

# Testes e2e
npm run test:e2e
```

## 🚀 Deploy

### Variáveis de Ambiente

```env
# Database
DATABASE_URL="postgresql://user:password@localhost:5432/finops"

# Redis
REDIS_URL="redis://localhost:6379"

# JWT
JWT_SECRET="your-super-secret-key"
JWT_EXPIRES_IN="7d"

# Server
PORT=3000
NODE_ENV="production"
```

### CI/CD com GitHub Actions

O projeto inclui pipeline automatizado para:
- ✅ Linting e formatação
- ✅ Testes unitários e integração
- ✅ Build e validação
- ✅ Deploy automatizado

## 🤝 Contribuição

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

### Padrões de Código

- **ESLint + Prettier** para formatação
- **Conventional Commits** para mensagens
- **Testes obrigatórios** para novas features
- **Documentação** atualizada

## 📝 Roadmap

### V1.0 - MVP
- [x] Autenticação e autorização
- [x] CRUD básico de transações
- [x] Sistema de categorias
- [x] Cálculos básicos de organização

### V1.1 - Colaboração
- [ ] Sistema de grupos
- [ ] Modelos de organização financeira
- [ ] Divisão Splitwise
- [ ] Relatórios básicos

### V2.0 - Avançado
- [ ] Metas e objetivos
- [ ] Notificações inteligentes
- [ ] Dashboard avançado
- [ ] Exportação de dados

### V3.0 - Premium
- [ ] IA para sugestões financeiras
- [ ] Integração com bancos (opcional)
- [ ] Análises preditivas
- [ ] Multi-moeda

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👥 Equipe

- **Desenvolvimento**: [Alttabcorp](https://github.com/Alttabcorp)
- **Documentação**: Baseada em análise de requisitos completa
- **Arquitetura**: Modelo escalável e modular

## 📞 Suporte

- **Issues**: [GitHub Issues](https://github.com/Alttabcorp/finops-api/issues)
- **Documentação**: [Wiki do Projeto](https://github.com/Alttabcorp/finops-api/wiki)
- **Email**: contato@alttabcorp.com

---

<div align="center">

**FinOps API** - Organizando finanças com inteligência e simplicidade 💰

[![Made with ❤️](https://img.shields.io/badge/Made%20with-❤️-red.svg)](https://github.com/Alttabcorp)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Node.js](https://img.shields.io/badge/Node.js-43853D?style=flat&logo=node.js&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat&logo=postgresql&logoColor=white)](https://www.postgresql.org/)

</div>
