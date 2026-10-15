# 🛒 Prumo – Gestão Comercial e Controle de Estoque

![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)
![Java](https://img.shields.io/badge/Java-25%20LTS-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-Java%2025-brightgreen)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-18-blue)

> **Projeto de Extensão (PEX) – Bacharelado em Engenharia de Software (Faculdade Descomplica)**
> **Estudo de caso / parceiro local:** Ricardo Importados
> **ODS's:** ODS 8 (Trabalho Decente e Crescimento Econômico) | ODS 9 (Indústria, Inovação e Infraestrutura)

---

## 📌 Sobre o Projeto

O **Prumo** é uma aplicação web full stack criada para ajudar o microempreendedor a sair do controle manual (cadernos e anotações informais) e passar para uma gestão digital simples e automatizada.

O sistema atende às necessidades operacionais da loja **Ricardo Importados**, oferecendo controle unificado de produtos eletrônicos, atualização automática de estoque, registro simplificado de vendas diárias e resumo financeiro para fechamento de caixa.

### Problema e solução

| Hoje (controle manual) | Com o Prumo |
|---|---|
| Estoque anotado em caderno, sujeito a erros | Saldo atualizado automaticamente a cada venda |
| Vendas sem registro padronizado | Lançamento rápido com forma de pagamento |
| Fechamento de caixa feito "de cabeça" | Resumo diário gerado pelo sistema |
| Acesso só no balcão | Interface responsiva, acessível pelo celular ou desktop |

---

## 🛠️ Tecnologias e Ferramentas

- **Backend:** Java 25 (LTS) | Spring Boot (Spring Web, Spring Data JPA, Bean Validation)
- **Banco de dados:** PostgreSQL
- **API:** RESTful, comunicação HTTP em JSON (testada via Insomnia / Postman)
- **Frontend:** HTML5, CSS3, JavaScript e Bootstrap (interface responsiva web/mobile)
- **Build e versionamento:** Maven, Git, GitHub
- **Ambientes de desenvolvimento:** IntelliJ IDEA (backend) | Visual Studio Code (frontend)
- **Apoio:** pgAdmin 4, Insomnia / Postman

---

## 🎯 Funcionalidades da Primeira Versão (MVP)

- [ ] **Gestão de produtos e estoque:** cadastro de eletrônicos com preço de custo, preço de venda, marca/modelo e quantidade em estoque
- [ ] **Baixa automática:** atualização do saldo a cada venda confirmada
- [ ] **PDV simplificado:** lançamento rápido de vendas com quantidade e forma de pagamento (Dinheiro, PIX, Cartão)
- [ ] **Fechamento do dia:** resumo das entradas diárias para conferência rápida do caixa

### Fora do escopo do MVP (possíveis evoluções)

- Autenticação e perfis de usuário
- Relatórios por período e gráficos
- Alerta de estoque mínimo
- Cadastro de clientes e fornecedores
- Deploy em nuvem

---

## 📐 Arquitetura da Solução

O projeto usa arquitetura em camadas para separar as responsabilidades:

```text
[ Frontend Web Responsivo (HTML/CSS/JS/Bootstrap) ]
                      │
                      ▼
[ Controller / Endpoints REST (Spring Web) ]
                      │
                      ▼
[ Service / Regras de negócio ]
                      │
                      ▼
[ Repository / Spring Data JPA ]
                      │
                      ▼
[ PostgreSQL ]
```

### Modelo de dados inicial (proposta)

- **Produto:** id, nome, marca, modelo, precoCusto, precoVenda, quantidadeEstoque
- **Venda:** id, dataHora, formaPagamento, total
- **ItemVenda:** id, venda, produto, quantidade, precoUnitario

### Endpoints previstos

| Método | Rota | Descrição |
|---|---|---|
| GET | `/api/produtos` | Lista os produtos |
| POST | `/api/produtos` | Cadastra um produto |
| PUT | `/api/produtos/{id}` | Atualiza um produto |
| DELETE | `/api/produtos/{id}` | Remove um produto |
| POST | `/api/vendas` | Registra uma venda e dá baixa no estoque |
| GET | `/api/fechamento?data=AAAA-MM-DD` | Resumo financeiro do dia |

> As rotas acima são o planejamento inicial e podem mudar durante o desenvolvimento.

---

## 🚀 Como Executar Localmente

### Pré-requisitos

- Java JDK 25 (LTS)
- PostgreSQL 18 em execução (desenvolvido e testado na versão 18.6)
- Maven (ou o Maven Wrapper `mvnw` do projeto)

### Passo a passo

1. Clone o repositório:

```bash
git clone https://github.com/seu-usuario/prumo-gestao-comercial.git
cd prumo-gestao-comercial
```

2. Crie o banco de dados:

```sql
CREATE DATABASE prumo_db;
```

3. Configure a conexão em `src/main/resources/application.properties`:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/prumo_db
spring.datasource.username=${DB_USER}
spring.datasource.password=${DB_PASSWORD}
spring.jpa.hibernate.ddl-auto=update
```

> Defina `DB_USER` e `DB_PASSWORD` como variáveis de ambiente. **Nunca versione senhas no repositório.**

4. Execute a aplicação:

```bash
./mvnw spring-boot:run
```

5. A API ficará disponível em `http://localhost:8080`.

---

## 🗂️ Estrutura do Projeto (prevista)

```text
prumo-gestao-comercial/
├── src/
│   ├── main/
│   │   ├── java/.../prumo/
│   │   │   ├── controller/
│   │   │   ├── service/
│   │   │   ├── repository/
│   │   │   ├── model/
│   │   │   └── dto/
│   │   └── resources/
│   │       ├── static/        # frontend (HTML/CSS/JS)
│   │       └── application.properties
│   └── test/
├── pom.xml
└── README.md
```

---

## 🗺️ Roadmap

- [x] Definição de escopo e estudo de caso
- [ ] Modelagem do banco de dados e diagrama de classes
- [ ] CRUD de produtos
- [ ] Registro de vendas com baixa de estoque
- [ ] Fechamento do dia
- [ ] Interface web responsiva
- [ ] Testes e validação com o parceiro
- [ ] Documentação final

---

## 👤 Autor

**Leonardo Laranjeira**
Estudante de Engenharia de Software
[LinkedIn](https://www.linkedin.com/in/leonardolaranjeira/) | [GitHub](https://github.com/leonardolaranjeira)

Desenvolvido como projeto de consolidação prática e acadêmica do curso de Engenharia de Software.

---

## 📄 Licença

Projeto acadêmico, sem fins comerciais. Este projeto está licenciado sob a Licença MIT.
