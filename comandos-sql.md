# Comandos SQL - Referências

## Modelagem Física

### Criar um banco de dados
```sql
CREATE DATABASE vendas CHARACTER SET UTF8mB4;
```

### Criar tabela fabricantes
```SQL
CREATE TABLE fabricantes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,

);
```

### Visualizar detalhes estruturais da tabela

```sql
DESC fabricantes;
```

### Criar Tabela Produtos
```SQL
CREATE TABLE produtos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    descricao TEXT(1000) NOT NULL,
    preco DECIMAL(6,2) NOT NULL,
    fabricantes_id INT NOT NULL
);
```

### Criação de chave estrangeira (relacionamento entre as tabelas)

```sql
ALTER TABLE produtos
    # CONSTRAINT é uma restrição definida no relacionamento
    ADD CONSTRAINT fk_produtos_fabricantes

    # A chave estrangeira deve fazer referência à chave primária
    FOREIGN KEY(fabricantes_id) REFERENCES fabricantes(id);
```
### criando uma nova coluna em uma tabela já existente
```sql
ALTER TABLE produtos ADD fabricantes INT NOT NULL AFTER preco;
```

# Atividade

## Criar um novo banco com base na atividade dos Filmes

# Banco
```sql
CREATE DATABASE cinema CHARACTER SET UTF8mB4;
```

### Criando as tabelas filmes

```sql
CREATE TABLE filmes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    ano YEAR(4), NOT NULL,
    genero_id INT NOT NULL
);
```

### Criando as tabelas genêro

```sql
CREATE TABLE genero(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    genero VARCHAR(45) NOT NULL
);
```

## Relacionando
```sql
ALTER TABLE filmes
    ADD CONSTRAINT fk_filmes_genero_idx

    FOREIGN KEY(genero_id) REFERENCES genero(id);
```