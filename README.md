# Banco API Performance

## 📖 Introdução
Este repositório contém scripts de **testes de performance** para a [Banco API](https://github.com/IaraStevani/banco-api).  
Os testes foram desenvolvidos utilizando o **k6**, uma ferramenta moderna e de código aberto para testes de carga e desempenho em APIs.  

O objetivo é validar a **escalabilidade, estabilidade e resiliência** da API em diferentes cenários de carga.

---

## 🛠️ Tecnologias Utilizadas
- [k6](https://k6.io/) → execução dos testes de performance  
- **JavaScript (ES6)** → linguagem de escrita dos cenários  
- **Variáveis de ambiente** → configuração dinâmica da URL da API  

---

## 📂 Estrutura do Repositório
```
banco-api-performance/
├── fixtures/           # Dados de entrada para os testes (ex: usuários, payloads)
├── helpers/            # Funções utilitárias reutilizáveis para interação com a API
├── tests/              # Casos de teste organizados por módulo da API.
├── utils/              # Funções utilitárias reutilizáveis 
├── reports/            # Relatórios exportados em HTML/JSON (gerados após execução)
├── config/             # Arquivo de configuração de variáveis de ambiente
└── README.md           # Documentação do projeto
```

---

## 🎯 Objetivo de Cada Grupo de Arquivo
- **fixtures/**: Dados de entrada para os testes (ex: usuários, payloads).
- **helpers/**: Funções utilitárias reutilizáveis para interação com a API.
- **tests/**: Casos de teste organizados por módulo da API.
- **utils/**: Funções utilitárias reutilizáveis  
- **config/**: Arquivo de configuração de variáveis de ambiente

---

## ⚙️ Instalação
1. Clone o repositório:
   ```bash
   git clone https://github.com/IaraStevani/banco-api-performance.git
   cd banco-api-performance
   ```

2. Instale o [k6](https://k6.io/docs/getting-started/installation/).

3. Altere o arquivo `.config.local.josn` e defina a URL base da API a ser testada:

   ```json
   {
      "baseUrl": "http://localhost:3000"
   }

   ```
   > Essas variaveis serão usadas dinamicamente nos testes para montar as requisições. 

---

## ▶️ Execução do Projeto

### Executar um teste simples
```bash
k6 run tests/login.test.js.js
```

Certifique-se de passar a variável de ambiente 'BASE_URL', caso não esteja usando um 'config.local.json' ou uma abordagem de carregamento automático:

```bash
k6 run tests/autenticacao/login.test.js -e BASE_URL=http://localhost:3000
```

### Acompanhar relatório em tempo real (Dashboard do k6)

Você pode ativar o modo dashboard do k6 e exportar o relatório ao final do teste:

```bash
K6_WEB_DASHBOARD=true K6_WEB_DASHBOARD_EXPORT=html-report.html k6 run --env BASE_URL=http://localhost:3000 tests/<nome-do-teste>.js
```

- `K6_WEB_DASHBOARD=true` → habilita o dashboard em tempo real no navegador.  
- `K6_WEB_DASHBOARD_EXPORT=html-report.html` → exporta o relatório em HTML após a execução.  

O relatório será salvo em `reports/html-report.html`.
