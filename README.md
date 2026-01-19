# Desafio Elixir - Sistema de Gestão de Estoque

Este é um desafio técnico para desenvolvedores **júnior** com o objetivo de avaliar suas habilidades em **Elixir** e **Phoenix Framework**.

> **Importante:** Não esperamos perfeição! O que queremos observar é **seu processo de aprendizado**, **sua curiosidade**, **capacidade de resolver problemas** e **persistência**.

---

## Sobre o Desafio

Você irá construir um **Sistema de Gestão de Estoque** que permite gerenciar produtos e suas movimentações (entradas e saídas). Este é um problema real que empresas enfrentam diariamente!

---

## Requisitos Técnicos

- **Elixir** (versão 1.14+)
- **Phoenix Framework** (versão 1.7+)
- **PostgreSQL** como banco de dados
- **Git** para versionamento

---

## Níveis de Entrega

Escolha o nível que melhor se adequa ao seu momento. **Não há problema em entregar apenas o nível básico** - o importante é a qualidade do que você entregar!

---

### Nível 1: Básico (Obrigatório)

**Objetivo:** Demonstrar que você consegue criar uma aplicação funcional com Elixir/Phoenix.

#### 1.1 Cadastro de Produtos
- [ ] Nome (obrigatório, mínimo 3 caracteres)
- [ ] Descrição (opcional)
- [ ] Quantidade em estoque (obrigatório, número inteiro >= 0)
- [ ] Preço unitário (opcional, decimal >= 0)

#### 1.2 Listagem de Produtos
- [ ] Exibir todos os produtos cadastrados
- [ ] Mostrar: Nome, Descrição, Quantidade em estoque, Preço

#### 1.3 Edição e Exclusão
- [ ] Permitir editar dados do produto
- [ ] Permitir excluir produto

#### 1.4 Validações Básicas
- [ ] Validar campos obrigatórios
- [ ] Não permitir quantidade negativa
- [ ] Exibir mensagens de erro amigáveis

**Entregáveis do Nível 1:**
- CRUD completo de produtos funcionando
- Validações implementadas
- Interface web básica (pode usar os generators do Phoenix)

---

### Nível 2: Intermediário (Opcional)

**Objetivo:** Demonstrar entendimento de relacionamentos e lógica de negócio.

#### 2.1 Movimentações de Estoque
- [ ] Registrar movimentações de **Entrada** e **Saída**
- [ ] Cada movimentação deve conter:
  - Produto relacionado
  - Tipo (`:entrada` ou `:saida`)
  - Quantidade (inteiro positivo)
  - Data/hora (automática)
  - Observação (opcional)

#### 2.2 Lógica de Estoque
- [ ] **Entrada:** aumenta quantidade em estoque
- [ ] **Saída:** diminui quantidade em estoque
- [ ] **Bloquear** saída se quantidade for maior que estoque disponível
- [ ] Atualizar estoque automaticamente após movimentação

#### 2.3 Histórico de Movimentações
- [ ] Listar todas as movimentações de um produto
- [ ] Mostrar: Data, Tipo, Quantidade, Observação
- [ ] Ordenar por data (mais recente primeiro)

**Entregáveis do Nível 2:**
- Relacionamento Product -> Movements funcionando
- Lógica de estoque implementada
- Histórico de movimentações por produto

---

### Nível 3: Avançado (Opcional - Para se destacar!)

**Objetivo:** Demonstrar conhecimento de boas práticas e features avançadas.

Escolha **pelo menos 2** das funcionalidades abaixo:

#### 3.1 API REST
- [ ] Criar endpoints JSON para produtos e movimentações
- [ ] Documentar os endpoints no README
- [ ] Implementar respostas de erro padronizadas

#### 3.2 Testes Automatizados
- [ ] Testes unitários para o contexto de Estoque
- [ ] Testes para validações
- [ ] Testes para lógica de movimentação

#### 3.3 Filtros e Busca
- [ ] Buscar produtos por nome
- [ ] Filtrar produtos com estoque baixo (< 10 unidades)
- [ ] Filtrar movimentações por período (data inicial e final)

#### 3.4 Dashboard Simples
- [ ] Total de produtos cadastrados
- [ ] Produtos com estoque zerado
- [ ] Valor total em estoque (quantidade × preço)
- [ ] Últimas 5 movimentações

#### 3.5 LiveView (Diferencial)
- [ ] Atualização em tempo real da listagem de produtos
- [ ] Formulário de movimentação sem reload da página

**Entregáveis do Nível 3:**
- Funcionalidades escolhidas implementadas e funcionando
- Código bem organizado e documentado

---

## Estrutura Esperada do Banco de Dados

### Tabela `products`
| Campo | Tipo | Obrigatório |
|-------|------|-------------|
| id | integer | auto |
| name | string | sim |
| description | text | não |
| quantity | integer | sim (default: 0) |
| price | decimal | não |
| inserted_at | datetime | auto |
| updated_at | datetime | auto |

### Tabela `movements` (Nível 2+)
| Campo | Tipo | Obrigatório |
|-------|------|-------------|
| id | integer | auto |
| product_id | references | sim |
| type | string/enum | sim |
| quantity | integer | sim |
| notes | text | não |
| inserted_at | datetime | auto |

---

## Entrega

### Repositório
- [ ] Projeto publicado no **GitHub**
- [ ] Código limpo e organizado
- [ ] Commits frequentes e com mensagens descritivas

### README (Atualize este arquivo!)
Ao final do desafio, adicione uma seção com:
- [ ] **Como rodar a aplicação** (comandos necessários)
- [ ] **Nível entregue** (1, 2 ou 3)
- [ ] **O que você aprendeu**
- [ ] **Principais desafios enfrentados**
- [ ] **O que faria diferente com mais tempo**

---

## Recursos para Aprendizado

### Elixir - Primeiros Passos
- [Elixir School (PT-BR)](https://elixirschool.com/pt) - Tutorial completo em português
- [Elixir Getting Started](https://elixir-lang.org/getting-started/introduction.html) - Documentação oficial
- [Exercism Elixir Track](https://exercism.org/tracks/elixir) - Exercícios práticos

### Phoenix Framework
- [Phoenix Guides](https://hexdocs.pm/phoenix/overview.html) - Documentação oficial
- [Phoenix Tutorial](https://www.phoenixframework.org/) - Site oficial
- [Phoenix LiveView](https://hexdocs.pm/phoenix_live_view/welcome.html) - Para o nível avançado

### Comandos Úteis
```bash
# Criar novo projeto Phoenix
mix phx.new stock_management --database postgres

# Entrar no diretório
cd stock_management

# Criar banco de dados
mix ecto.create

# Gerar CRUD completo (scaffold)
mix phx.gen.html Stock Product products name:string description:text quantity:integer price:decimal

# Rodar migrations
mix ecto.migrate

# Iniciar servidor
mix phx.server

# Rodar testes
mix test
```

### Dicas de Ouro
1. **Use os generators!** O Phoenix tem excelentes geradores de código
2. **Leia os erros** - Elixir tem mensagens de erro muito claras
3. **IEx é seu amigo** - Use `iex -S mix` para testar código no terminal
4. **Commits frequentes** - Ajuda a voltar atrás se algo der errado

---

## Prazo

**7 dias corridos** após o recebimento deste desafio

---

## Critérios de Avaliação

| Critério | Peso |
|----------|------|
| Código funcionando | Alto |
| Organização e clareza do código | Alto |
| README bem escrito | Médio |
| Commits organizados | Médio |
| Boas práticas Elixir | Médio |
| Funcionalidades extras | Baixo (diferencial) |

---

## Dúvidas?

Não hesite em perguntar! Saber fazer perguntas é uma habilidade importante.

---

## Reflexão Final (Opcional, mas recomendada)

Ao terminar, responda:
- O que você achou de trabalhar com Elixir?
- Qual foi o momento mais desafiador?
- O que você faria diferente se começasse de novo?

---

**Boa sorte! Estamos ansiosos para ver sua solução!**

---

## Sua Solução

> *Preencha esta seção ao finalizar o desafio*

### Como Rodar

```bash
# Seus comandos aqui
```

### Nível Entregue
- [ ] Nível 1 (Básico)
- [ ] Nível 2 (Intermediário)
- [ ] Nível 3 (Avançado)

### O que Aprendi
> *Escreva aqui...*

### Principais Desafios
> *Escreva aqui...*

### O que Faria Diferente
> *Escreva aqui...*
