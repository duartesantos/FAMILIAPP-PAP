# 📱 Sistema de Gamificação para Pais e Filhos

Sistema de gamificação desenvolvido como Projeto de Aptidão Profissional (PAP) que permite aos pais criarem tarefas e produtos, enquanto os filhos ganham pontos ao completar tarefas e podem trocar esses pontos por produtos.

## 📋 Índice

- [Descrição](#-descrição)
- [Funcionalidades](#-funcionalidades)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Pré-requisitos](#-pré-requisitos)
- [Instalação e Configuração](#-instalação-e-configuração)
- [Como Executar](#-como-executar)
- [Estrutura da Base de Dados](#-estrutura-da-base-de-dados)
- [API Endpoints](#-api-endpoints)
- [Documentação](#-documentação)
- [Autor](#-autor)

## 📖 Descrição

Este projeto consiste numa aplicação móvel desenvolvida com Ionic/Angular que implementa um sistema de gamificação para incentivar crianças a realizar tarefas domésticas e escolares. Os pais podem criar tarefas e definir produtos que podem ser adquiridos com pontos, enquanto os filhos completam tarefas para ganhar pontos e trocá-los por recompensas.

## ✨ Funcionalidades

### Para Pais:
- ✅ **Registo e Login** - Sistema de autenticação para pais
- 👨‍👩‍👧‍👦 **Gestão de Filhos** - Adicionar, editar e eliminar filhos
- 📝 **Gestão de Tarefas** - Criar, visualizar e eliminar tarefas
- ✅ **Aprovação de Tarefas** - Validar tarefas completadas pelos filhos
- 🛒 **Gestão de Produtos** - Criar produtos com pontos e quantidades
- 📊 **Visualização de Produtos Comprados** - Acompanhar produtos adquiridos pelos filhos
- 📈 **Histórico de Tarefas Feitas** - Consultar tarefas completadas

### Para Filhos:
- 🔐 **Login** - Acesso com credenciais próprias
- 📋 **Visualizar Tarefas** - Ver tarefas atribuídas pelo pai
- ✅ **Completar Tarefas** - Marcar tarefas como concluídas
- 💰 **Sistema de Pontos** - Acumular pontos ao completar tarefas
- 🛍️ **Loja de Produtos** - Visualizar produtos disponíveis
- 🛒 **Comprar Produtos** - Trocar pontos por produtos
- 📦 **Produtos Comprados** - Ver histórico de compras

## 🛠️ Tecnologias Utilizadas

### Frontend
- **Ionic Framework** (v6.1.9) - Framework para desenvolvimento de aplicações móveis
- **Angular** (v14.0.0) - Framework JavaScript
- **TypeScript** (v4.7.3) - Linguagem de programação
- **RxJS** (v6.6.0) - Biblioteca para programação reativa

### Backend
- **PHP** (v7.4+) - Linguagem de programação do servidor
- **MySQL/MariaDB** - Sistema de gestão de base de dados
- **PDO** - Extensão PHP para acesso à base de dados

### Ferramentas
- **XAMPP** - Ambiente de desenvolvimento local
- **Node.js** - Runtime para execução do frontend
- **npm** - Gestor de pacotes

## 📁 Estrutura do Projeto

```
PAP_DUARTESANTOS-master/
│
├── apipap/                          # API Backend (PHP)
│   ├── conexao.php                  # Configuração da conexão à base de dados
│   ├── login/
│   │   └── login.php                # Endpoint de autenticação
│   ├── registar/
│   │   └── registar.php             # Endpoint de registo
│   ├── filhos/
│   │   ├── listar.php               # Listar filhos
│   │   ├── inserir.php              # Adicionar filho
│   │   └── eliminar.php             # Eliminar filho
│   ├── tarefas/
│   │   ├── listar.php               # Listar tarefas
│   │   ├── inserir.php              # Criar tarefa
│   │   ├── eliminar.php             # Eliminar tarefa
│   │   └── buscarFilhos.php         # Buscar filhos para atribuir tarefas
│   ├── tarefas-filho/
│   │   ├── listar.php               # Listar tarefas do filho
│   │   ├── fazerTarefa.php          # Completar tarefa
│   │   └── eliminar.php             # Eliminar tarefa
│   ├── tarefas-feitas/
│   │   └── listar.php               # Listar tarefas completadas (pai)
│   ├── tarefas-feitas-filho/
│   │   └── listar.php               # Listar tarefas completadas (filho)
│   ├── produtos/
│   │   ├── listar.php               # Listar produtos
│   │   ├── inserir.php              # Criar produto
│   │   └── eliminar.php             # Eliminar produto
│   ├── produtos-filho/
│   │   ├── listar.php               # Listar produtos disponíveis (filho)
│   │   └── comprarProduto.php       # Comprar produto
│   ├── produtos-comprados/
│   │   └── listar.php               # Listar produtos comprados (pai)
│   └── produtos-comprados-filho/
│       └── listar.php               # Listar produtos comprados (filho)
│
├── PAP_DUARTESANTOS_FIM/            # Aplicação Frontend (Ionic/Angular)
│   ├── src/
│   │   ├── app/                     # Módulos e páginas da aplicação
│   │   │   ├── login/               # Página de login
│   │   │   ├── registar/            # Página de registo
│   │   │   ├── filhos/              # Gestão de filhos
│   │   │   ├── add-filho/           # Adicionar filho
│   │   │   ├── filhos-home/         # Home do filho
│   │   │   ├── tarefas/             # Gestão de tarefas (pai)
│   │   │   ├── add-tarefa/          # Adicionar tarefa
│   │   │   ├── mostrar-tarefa/      # Detalhes da tarefa
│   │   │   ├── tarefas-filho/       # Tarefas do filho
│   │   │   ├── tarefas-feitas/      # Tarefas completadas (pai)
│   │   │   ├── tarefas-feitas-filho/# Tarefas completadas (filho)
│   │   │   ├── produtos/            # Gestão de produtos (pai)
│   │   │   ├── add-produto/         # Adicionar produto
│   │   │   ├── produtos-filho/      # Loja de produtos (filho)
│   │   │   ├── produtos-comprados/  # Produtos comprados (pai)
│   │   │   └── produtos-comprados-filho/# Produtos comprados (filho)
│   │   ├── services/                # Serviços Angular
│   │   │   ├── api.ts               # Serviço de comunicação com API
│   │   │   └── login.service.ts     # Serviço de autenticação
│   │   └── environments/            # Configurações de ambiente
│   ├── package.json                 # Dependências do projeto
│   └── angular.json                 # Configuração do Angular
│
├── appgamificacao.sql               # Script SQL da base de dados
├── RelatorioPAP_DuarteSantos.docx   # Relatório do projeto
└── README.md                        # Este ficheiro
```

## 📋 Pré-requisitos

Antes de começar, certifique-se de que tem instalado:

- **XAMPP** (ou similar) com PHP 7.4+ e MySQL/MariaDB
- **Node.js** (v14 ou superior) e **npm**
- **Ionic CLI** - Instalar globalmente: `npm install -g @ionic/cli`
- **Angular CLI** (v14) - Instalar globalmente: `npm install -g @angular/cli@14`

## 🚀 Instalação e Configuração

### 1. Configuração da Base de Dados

1. Inicie o XAMPP e certifique-se de que o Apache e MySQL estão em execução
2. Aceda ao phpMyAdmin (http://localhost/phpmyadmin)
3. Crie uma nova base de dados chamada `appgamificacao`
4. Importe o ficheiro `appgamificacao.sql` para criar as tabelas e dados de exemplo

### 2. Configuração do Backend (API)

1. Copie a pasta `apipap` para `C:\xampp\htdocs\apipap`
   - **Nota:** Se o XAMPP estiver noutra localização, ajuste o caminho conforme necessário

2. Verifique/ajuste as credenciais da base de dados no ficheiro `apipap/conexao.php`:
```php
$banco = 'appgamificacao';
$host = 'localhost';
$usuario = 'root';
$senha = '';  // Ajuste se necessário
```

### 3. Configuração do Frontend

1. Navegue até à pasta do projeto frontend:
```bash
cd PAP_DUARTESANTOS_FIM
```

2. Instale as dependências:
```bash
npm install
```

3. Configure o endereço da API no ficheiro `src/services/api.ts`:
```typescript
server: string = 'http://localhost/apipap/';
```

**Nota:** Se estiver a usar um servidor diferente ou a executar num dispositivo móvel, ajuste este endereço para o IP do seu computador (ex: `http://192.168.1.100/apipap/`)

## ▶️ Como Executar

### Executar o Backend

1. Certifique-se de que o XAMPP está em execução
2. O Apache e MySQL devem estar ativos
3. A API estará disponível em: `http://localhost/apipap/`

### Executar o Frontend

1. Na pasta `PAP_DUARTESANTOS_FIM`, execute:
```bash
ionic serve
```

2. A aplicação será aberta automaticamente no navegador em `http://localhost:8100`

### Executar no Dispositivo Móvel

Para testar num dispositivo móvel:

1. Certifique-se de que o dispositivo está na mesma rede Wi-Fi
2. Descubra o IP do seu computador (ex: `192.168.1.100`)
3. Atualize o `server` em `src/services/api.ts` para usar o IP do computador
4. Execute:
```bash
ionic serve --external
```
5. Aceda ao endereço fornecido a partir do dispositivo móvel

### Build para Produção

Para gerar uma versão de produção:

```bash
ionic build --prod
```

## 🗄️ Estrutura da Base de Dados

A base de dados `appgamificacao` contém as seguintes tabelas:

### `utilizadorpai`
Armazena os dados dos pais/responsáveis.
- `idutilizadorPai` (PK)
- `NomePai`
- `MailPai`
- `Senha`
- `TipoUtilizador` (default: 'pai')

### `utilizadorfilho`
Armazena os dados dos filhos.
- `idutilizadorFilho` (PK)
- `NomeFilho`
- `MailFilho`
- `Senha`
- `Pontos` (pontos acumulados)
- `utilizadorPai_idutilizadorPai` (FK)
- `TipoUtilizador` (default: 'filho')

### `tarefa`
Armazena as tarefas criadas pelos pais.
- `idTarefa` (PK)
- `NomeTarefa`
- `DescricaoTarefa`
- `PontosTarefa`
- `DataAtribuicao`
- `TarefaFeita` (0 ou 1)
- `DataTarefaFeita`
- `utilizadorFilho_idutilizadorFilho` (FK)
- `utilizadorPai_idutilizadorPai` (FK)

### `produto`
Armazena os produtos disponíveis para compra.
- `idproduto` (PK)
- `NomeProduto`
- `PontosProduto`
- `QuantidadeProduto`
- `ProdutoComprado` (0 ou 1)
- `utilizadorPai_idutilizadorPai` (FK)

### `produto_has_utilizadorfilho`
Tabela de relacionamento entre produtos e filhos (histórico de compras).
- `produto_idproduto` (FK)
- `utilizadorFilho_idutilizadorFilho` (FK)
- `DataCompra`

## 🔌 API Endpoints

### Autenticação
- `POST /login/login.php` - Login de utilizador (pai ou filho)
- `POST /registar/registar.php` - Registo de novo pai

### Filhos
- `POST /filhos/listar.php` - Listar filhos de um pai
- `POST /filhos/inserir.php` - Adicionar novo filho
- `POST /filhos/eliminar.php` - Eliminar filho

### Tarefas (Pai)
- `POST /tarefas/listar.php` - Listar todas as tarefas
- `POST /tarefas/inserir.php` - Criar nova tarefa
- `POST /tarefas/eliminar.php` - Eliminar tarefa
- `POST /tarefas/buscarFilhos.php` - Buscar filhos para atribuir tarefas
- `POST /tarefas-feitas/listar.php` - Listar tarefas completadas

### Tarefas (Filho)
- `POST /tarefas-filho/listar.php` - Listar tarefas do filho
- `POST /tarefas-filho/fazerTarefa.php` - Completar tarefa
- `POST /tarefas-feitas-filho/listar.php` - Listar tarefas completadas pelo filho

### Produtos (Pai)
- `POST /produtos/listar.php` - Listar produtos
- `POST /produtos/inserir.php` - Criar novo produto
- `POST /produtos/eliminar.php` - Eliminar produto
- `POST /produtos-comprados/listar.php` - Listar produtos comprados

### Produtos (Filho)
- `POST /produtos-filho/listar.php` - Listar produtos disponíveis
- `POST /produtos-filho/comprarProduto.php` - Comprar produto
- `POST /produtos-comprados-filho/listar.php` - Listar produtos comprados pelo filho

## 📚 Documentação

Para mais detalhes sobre o projeto, consulte o relatório completo:
- **RelatorioPAP_DuarteSantos.docx** - Relatório detalhado do Projeto de Aptidão Profissional

## 👤 Autor

**Duarte Santos**

Projeto desenvolvido como Projeto de Aptidão Profissional (PAP).

---

## 📝 Notas Importantes

- Certifique-se de que o XAMPP está em execução antes de iniciar a aplicação
- A pasta `apipap` deve estar localizada em `C:\xampp\htdocs\apipap`
- Para testar em dispositivos móveis, use o IP do computador em vez de `localhost`
- As credenciais padrão da base de dados são: utilizador `root` sem senha (ajuste se necessário)

## 🐛 Resolução de Problemas

### Erro de conexão à API
- Verifique se o Apache está em execução no XAMPP
- Confirme que a pasta `apipap` está em `htdocs`
- Verifique o endereço da API em `src/services/api.ts`

### Erro de conexão à base de dados
- Verifique se o MySQL está em execução no XAMPP
- Confirme que a base de dados `appgamificacao` foi criada e importada
- Verifique as credenciais em `apipap/conexao.php`

### Erro ao instalar dependências
- Certifique-se de que está a usar Node.js v14 ou superior
- Tente limpar o cache: `npm cache clean --force`
- Elimine a pasta `node_modules` e execute `npm install` novamente

---

