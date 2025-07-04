# 🎬 ScreenMatch - Sistema de Catálogo de Séries

![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.1.1-green)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-blue)
![HTML5](https://img.shields.io/badge/HTML5-Frontend-red)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow)

O ScreenMatch é uma aplicação web completa para catalogação e pesquisa de séries de TV, desenvolvida como parte da formação Java da Alura. O projeto consiste em uma API REST em Spring Boot (backend) e uma interface web moderna (frontend) para visualização das séries.

## 📁 Estrutura do Projeto

```
ScreenMatch-web/
├── backend/          # API REST em Spring Boot
├── front/           # Interface web frontend  
└── readme.md        # Documentação principal
```

## 🚀 Funcionalidades Principais

### Backend (API REST)
- **Catalogação de Séries**: Sistema completo de gerenciamento de séries e episódios
- **API RESTful**: Endpoints para consulta de séries, temporadas e episódios
- **Integração com ChatGPT**: Tradução automática de sinopses
- **Banco de Dados**: Persistência com PostgreSQL e Spring Data JPA
- **Categorização**: Sistema de categorias para organização das séries
- **Top Rankings**: Endpoints para séries mais bem avaliadas

### Frontend (Interface Web)
- **Interface Moderna**: Design responsivo e intuitivo
- **Navegação por Categorias**: Filtros dinâmicos para organização
- **Páginas de Detalhes**: Visualização completa de séries e temporadas
- **Integração com API**: Consumo dinâmico dos dados do backend

## 🛠️ Tecnologias Utilizadas

### Backend
- **Java 17**: Linguagem principal
- **Spring Boot 3.1.1**: Framework principal
- **Spring Data JPA**: Persistência de dados
- **Spring Web**: Desenvolvimento da API REST
- **PostgreSQL**: Banco de dados relacional
- **Jackson**: Serialização/deserialização JSON
- **OpenAI GPT-3**: Integração para tradução de textos
- **Maven**: Gerenciamento de dependências

### Frontend
- **HTML5**: Estrutura das páginas
- **CSS3**: Estilização e design responsivo
- **JavaScript ES6+**: Lógica e interações
- **Fetch API**: Comunicação com o backend
- **Google Fonts**: Tipografia

## 📊 Arquitetura da Aplicação

### Backend - Estrutura de Pacotes

```
br.com.alura.screenmatch/
├── config/
│   └── CorsConfiguration.java     # Configuração CORS
├── controller/
│   └── SerieController.java       # Endpoints da API
├── dto/
│   ├── EpisodioDTO.java          # Data Transfer Objects
│   └── SerieDTO.java
├── model/
│   ├── Categoria.java            # Entidades do domínio
│   ├── Serie.java
│   ├── Episodio.java
│   └── DadosSerie.java
├── repository/
│   └── SerieRepository.java      # Acesso a dados
├── service/
│   ├── SerieService.java         # Lógica de negócio
│   ├── ConsultaChatGPT.java      # Integração ChatGPT
│   └── ConsumoApi.java           # Consumo de APIs externas
└── ScreenmatchApplication.java   # Classe principal
```

### Frontend - Estrutura de Arquivos

```
front/
├── index.html              # Página principal
├── detalhes.html          # Página de detalhes das séries
├── styles.css             # Estilos globais
├── css/
│   ├── home.css          # Estilos da página inicial
│   └── detalhes.css      # Estilos da página de detalhes
├── scripts/
│   ├── index.js          # Script principal
│   ├── getDados.js       # Funções de API
│   └── series.js         # Lógica específica de séries
└── img/
    └── logo.png          # Recursos visuais
```

## 🔗 Endpoints da API

### Séries
- `GET /series` - Lista todas as séries
- `GET /series/top5` - Top 5 séries mais bem avaliadas  
- `GET /series/lancamentos` - Séries lançadas recentemente
- `GET /series/{id}` - Detalhes de uma série específica
- `GET /series/{id}/temporadas/todas` - Todas as temporadas de uma série
- `GET /series/{id}/temporadas/{numero}` - Episódios de uma temporada específica

### Categorias Disponíveis
- Comédia
- Ação  
- Crime
- Drama
- Aventura

## ⚙️ Configuração e Instalação

### Pré-requisitos
- Java 17 ou superior
- Maven 3.6+
- PostgreSQL 12+
- VS Code (recomendado para o frontend)

### Backend

1. **Clone o repositório**
```bash
git clone <url-do-repositorio>
cd ScreenMatch-web/backend
```

2. **Configure o banco de dados**
Crie um arquivo `.env` ou configure as variáveis de ambiente:
```properties
DB_HOST=localhost:5432
DB_NAME=screenmatch
DB_USER=seu_usuario
DB_PASSWORD=sua_senha
```

3. **Execute a aplicação**
```bash
# Windows
./mvnw.cmd spring-boot:run

# Linux/Mac
./mvnw spring-boot:run
```

A API estará disponível em `http://localhost:8080`

### Frontend

1. **Navegue até o diretório frontend**
```bash
cd ScreenMatch-web/front
```

2. **Instale a extensão Live Server no VS Code**

3. **Abra o projeto no VS Code**
```bash
code .
```

4. **Execute com Live Server**
- Clique com o botão direito em `index.html`
- Selecione "Open with Live Server"

A aplicação frontend estará disponível em `http://localhost:5500`

## 🗄️ Modelo de Dados

### Entidades Principais

**Serie**
- `id`: Identificador único
- `titulo`: Nome da série
- `totalTemporadas`: Número de temporadas
- `avaliacao`: Nota da série
- `genero`: Categoria (enum)
- `atores`: Lista de atores principais
- `poster`: URL da imagem
- `sinopse`: Descrição da série

**Episodio**
- `id`: Identificador único
- `titulo`: Nome do episódio
- `numeroEpisodio`: Número na temporada
- `avaliacao`: Nota do episódio
- `dataLancamento`: Data de lançamento
- `serie`: Referência à série (FK)

## 🎯 Funcionalidades Detalhadas

### Backend Features
- **CRUD Completo**: Operações de criação, leitura, atualização e exclusão
- **Consultas Customizadas**: Queries otimizadas com Spring Data JPA
- **Tradução Automática**: Integração com ChatGPT para traduzir sinopses
- **Validação de Dados**: Validações robustas nos DTOs
- **Tratamento de Erros**: Handling adequado de exceções
- **CORS Configurado**: Acesso liberado para o frontend

### Frontend Features
- **Navegação Intuitiva**: Interface amigável e responsiva
- **Filtros Dinâmicos**: Busca por categoria em tempo real
- **Carregamento Assíncrono**: Dados carregados via Ajax
- **Design Responsivo**: Adaptável a diferentes dispositivos
- **Experiência Rica**: Transições e animações suaves

## 📈 Melhorias Futuras

- [ ] Sistema de autenticação e autorização
- [ ] Funcionalidade de favoritos
- [ ] Sistema de avaliações pelos usuários
- [ ] Busca textual avançada
- [ ] Cache para melhor performance
- [ ] Testes automatizados (unitários e integração)
- [ ] Deploy automatizado
- [ ] Integração com mais APIs de séries
- [ ] Sistema de recomendações

## 🤝 Contribuição

Este projeto foi desenvolvido como parte do curso da Alura. Contribuições são bem-vindas:

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto é parte do material educacional da Alura e está disponível para fins de aprendizado.

## 👥 Autores

- **Desenvolvimento Backend**: Curso Alura - Formação Java
- **Desenvolvimento Frontend**: Monica Hillman (Alura)
- **Adaptações**: Baseado no projeto original da Alura

## 📞 Suporte

Para dúvidas e suporte, consulte:
- [Documentação da Alura](https://www.alura.com.br)
- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)

---

**⭐ Se este projeto foi útil para você, considere dar uma estrela no repositório!**