// ============================================================
// Exercícios MongoDB - Catálogo de E-commerce
// Banco de Dados - 2º ADS - UNIFAAT
// Aluno: José Henrique Teixeira Luiz | RA: 3225002
// ============================================================

// ============================================================
// EXERCÍCIO 1: Criação e Coleções (CREATE - "C" do CRUD)
// ============================================================

// 1.1 - Acessar/criar o banco de dados loja_virtual
use loja_virtual

// 1.2 - Criar a coleção produtos e inserir um smartphone (insertOne)
db.produtos.insertOne({
  nome: "Smartphone Galaxy A15",
  categoria: "Eletronicos",
  preco: 1299.90,
  marca: "Samsung",
  armazenamento: "128GB",
  cor: "Azul"
})

// 1.3 - Inserir mais dois produtos de categorias diferentes (insertMany)
db.produtos.insertMany([
  {
    nome: "MongoDB na Pratica",
    categoria: "Livros",
    preco: 79.90,
    autor: "Joao Silva",
    editora: "Tech Books",
    paginas: 320
  },
  {
    nome: "Camiseta Basica",
    categoria: "Roupas",
    preco: 49.90,
    tamanho: "M",
    cor: "Preta",
    material: "Algodao"
  },
  {
    nome: "Notebook Ultra X",
    categoria: "Eletronicos",
    preco: 3899.90,
    marca: "Lenovo",
    memoria_ram: "16GB",
    processador: "Intel i7"
  },
  {
    nome: "Tenis Runner Pro",
    categoria: "Calcados",
    preco: 299.90,
    tamanho: 42,
    cor: "Branco",
    marca: "Olympikus"
  }
])

// ============================================================
// EXERCÍCIO 2: Consultas e Filtros (READ - "R" do CRUD)
// ============================================================

// 2.1 - Listar todos os produtos da coleção
db.produtos.find()

// 2.2 - Buscar apenas produtos com preço superior a 100
db.produtos.find({ preco: { $gt: 100 } })

// 2.3 - Listar apenas produtos da categoria Eletronicos
db.produtos.find({ categoria: "Eletronicos" })

// 2.4 - Retornar apenas o nome e preço dos produtos (projeção)
db.produtos.find({}, { nome: 1, preco: 1, _id: 0 })

// ============================================================
// EXERCÍCIO 3: Atualização Dinâmica (UPDATE - "U" do CRUD)
// ============================================================

// 3.1 - Atualizar o preço de um produto específico usando $set
db.produtos.updateOne(
  { nome: "Smartphone Galaxy A15" },
  { $set: { preco: 1199.90 } }
)

// 3.2 - Adicionar campo 'estoque' para todos os produtos usando updateMany
db.produtos.updateMany(
  {},
  { $set: { estoque: 50 } }
)

// 3.3 - Marcar produtos da categoria Roupas com o campo promocao: true
db.produtos.updateMany(
  { categoria: "Roupas" },
  { $set: { promocao: true } }
)

// ============================================================
// EXERCÍCIO 4: Exclusão de Dados (DELETE - "D" do CRUD)
// ============================================================

// 4.1 - Remover um produto específico usando deleteOne
db.produtos.deleteOne({ nome: "MongoDB na Pratica" })

// 4.2 - Remover todos os produtos de uma categoria usando deleteMany
db.produtos.deleteMany({ categoria: "Calcados" })