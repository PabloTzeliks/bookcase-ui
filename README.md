# 📚 BookCase UI — Frontend

<div align="center">
  <img src=".github/assets/preview.png" alt="BookCase Preview" width="800"/>
  <br/><br/>
  <p><em>Sua estante pessoal, moderna e rápida. 📖</em></p>

  ![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
  ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
  ![TailwindCSS](https://img.shields.io/badge/TailwindCSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
</div>

---

## 🗂️ Sobre o Projeto

**BookCase** é uma aplicação web front-end construída para ser a interface visual de um sistema pessoal de gerenciamento de biblioteca. A ideia é simples e poderosa: você pesquisa um livro, adiciona à sua estante com um status (Lendo, Lido ou Quero Ler) e uma avaliação de 1 a 5 estrelas — tudo de forma rápida e responsiva.

> 🏆 **Este foi o primeiro projeto com interface própria que consome uma API desenvolvida do zero (Spring Boot).**
> O projeto foi construído intencionalmente com **JavaScript Vanilla** (sem frameworks) para solidificar os fundamentos da linguagem: manipulação do DOM, chamadas assíncronas com `fetch`, módulos ES6+ e muito mais.

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Uso |
|---|---|
| **HTML5 Semântico** | Estrutura e marcação das páginas |
| **Tailwind CSS (CDN)** | Estilização responsiva e moderna sem CSS customizado |
| **JavaScript Vanilla (ES6+)** | Toda a lógica da aplicação: DOM, fetch, autenticação, renderização |
| **Fetch API** | Requisições assíncronas para a API back-end e Google Books |
| **Phosphor Icons** | Ícones modernos e leves via CDN |
| **Google Books API** | Busca de livros por título/autor |

---

## ✨ Funcionalidades Implementadas

### 🔐 Autenticação JWT / Basic Auth
- Login e registro de usuário com validação de campos em tempo real.
- O token/credencial de autenticação é armazenado no `localStorage` como `LibraryCredential`.
- A aplicação verifica o estado de autenticação ao carregar cada página e redireciona o usuário conforme necessário.

### 📖 Busca e Adição de Livros
- Integração com a **Google Books API** para buscar livros pelo título ou autor diretamente da barra de pesquisa.
- Resultados exibidos em um modal com capa, título e autor.
- Ao selecionar um livro, um segundo modal permite escolher o **status** e a **avaliação** antes de adicionar à estante.

### 🏗️ Renderização Dinâmica da Estante
- Os livros são buscados da API back-end e a estante é montada dinamicamente com JavaScript puro via `.map().join('')`, sem nenhum framework de templates.
- Layout responsivo: de 2 colunas no mobile até 5 colunas no desktop.

### 🔍 Filtros por Status (Em Memória)
- Filtragem instantânea por: **Todos**, **Lendo**, **Lidos** e **Quero Ler**.
- Os filtros operam sobre os dados já carregados em memória, sem fazer novas requisições à API — rápido e eficiente.

### 🖼️ Tratamento Inteligente de Capas
- Lógica embutida no JavaScript para melhorar a qualidade das capas vindas da Google Books API:
  - Remove o efeito de dobra/curl da imagem.
  - Aumenta o zoom para melhor resolução.
- Para livros sem capa disponível, é gerado automaticamente um **placeholder visual** via [placehold.co](https://placehold.co).

### ⭐ Sistema de Avaliação com Estrelas
- Cada livro na estante exibe de **0 a 5 estrelas** de forma dinâmica, baseadas na nota salva no banco de dados.
- No modal de adição, o usuário pode interagir com as estrelas para selecionar a avaliação antes de salvar.

---

## 🚀 Como Executar

Este projeto é **front-end puro** — não há build, sem `npm install`, sem complicação.

### Pré-requisitos

- **API Back-End rodando** na porta `8080`. Os `fetch`s da aplicação apontam para `http://localhost:8080`. Sem o back-end no ar, a autenticação e a estante não funcionarão.
  > O back-end (Spring Boot) pode ser encontrado no repositório: [bookcase-api](https://github.com/PabloTzeliks/bookcase-api)

### Passos

**Opção 1 — Live Server (Recomendado)**
1. Clone este repositório:
   ```bash
   git clone https://github.com/PabloTzeliks/bookcase-ui.git
   ```
2. Abra a pasta no **VS Code**.
3. Instale a extensão [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer).
4. Clique com o botão direito em `index.html` → **"Open with Live Server"**.
5. O navegador abrirá em `http://127.0.0.1:5500`.

**Opção 2 — Abertura Direta**
1. Clone o repositório.
2. Dê um duplo-clique no arquivo `index.html` para abri-lo no navegador.

> ⚠️ Lembre-se: a API Back-End precisa estar rodando em `http://localhost:8080` para que o login e o carregamento da estante funcionem.

---

## 📁 Estrutura de Arquivos

```
bookcase-ui/
│
├── index.html          # Página de entrada: landing page com modais de Login e Cadastro
├── bookcase.html       # Dashboard principal: estante, busca e filtros
│
└── js/
    ├── auth.js         # Lógica de autenticação: login, registro, logout, redirecionamento
    ├── bookcase.js     # Core do app: busca, renderização, filtros, avaliação e modais
    └── api.js          # (Reservado para utilitários de API)
```

---

## 🧑‍💻 Sobre o Desenvolvimento

Este projeto marca uma conquista importante: **a primeira interface gráfica real consumindo uma API própria**. A decisão de usar **JavaScript Vanilla** foi intencional — cada linha de código aqui representa um aprendizado fundamental:

- Como fazer e encadear requisições HTTP com `fetch` e `async/await`.
- Como manipular o DOM para criar UIs dinâmicas e responsivas sem React ou Vue.
- Como gerenciar estado simples no front-end com variáveis e `localStorage`.
- Como integrar APIs de terceiros (Google Books) junto com uma API própria.

É um projeto de fundamentos, e como todo bom começo, ele foi construído com muita curiosidade e dedicação. 🚀

---

<div align="center">
  <p>Feito com ❤️ por <a href="https://github.com/PabloTzeliks">Pablo Tzeliks</a></p>
</div>
