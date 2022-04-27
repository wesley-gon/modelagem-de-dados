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