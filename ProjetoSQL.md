Script SQL
```
CREATE TABLE Cliente (
 CPF_CNPJ VARCHAR(14) PRIMARY KEY,
 Nome VARCHAR(100) NOT NULL,
 Endereço VARCHAR(200) NOT NULL,
 Telefone VARCHAR(20) NOT NULL,
 Tipo VARCHAR(2) CHECK (Tipo IN ('PF', 'PJ'))
);

CREATE TABLE Conta (
 ID INT PRIMARY KEY,
 Cliente_ID VARCHAR(14) FOREIGN KEY REFERENCES Cliente(CPF_CNPJ),
 Email VARCHAR(100) NOT NULL,
 Senha VARCHAR(100) NOT NULL,
 Tipo VARCHAR(2) CHECK (Tipo IN ('PF', 'PJ'))
);

CREATE TABLE Vendedor (
 ID INT PRIMARY KEY,
 Nome VARCHAR(100) NOT NULL,
 Endereço VARCHAR(200) NOT NULL,
 Telefone VARCHAR(20) NOT NULL
);

CREATE TABLE Fornecedor (
 ID INT PRIMARY KEY,
 Nome VARCHAR(100) NOT NULL,
 Endereço VARCHAR(200) NOT NULL,
 Telefone VARCHAR(20) NOT NULL
);

CREATE TABLE Produto (
 ID INT PRIMARY KEY,
 Nome VARCHAR(100) NOT NULL,
 Descrição VARCHAR(200) NOT NULL,
 Preço DECIMAL(10, 2) NOT NULL,
 Estoque INT NOT NULL
);

CREATE TABLE Pedido (
 ID INT PRIMARY KEY,
 Cliente_ID VARCHAR(14) FOREIGN KEY REFERENCES Cliente(CPF_CNPJ),
 Data DATETIME NOT NULL,
 Status VARCHAR(20) NOT NULL
);

CREATE TABLE ItemPedido (
 ID INT PRIMARY KEY,
 Pedido_ID INT FOREIGN KEY REFERENCES Pedido(ID),
 Produto_ID INT FOREIGN KEY REFERENCES Produto(ID),
 Quantidade INT NOT NULL
);

CREATE TABLE Pagamento (
 ID INT PRIMARY KEY,
 Pedido_ID INT FOREIGN KEY REFERENCES Pedido(ID),
 Forma_Pagamento VARCHAR(20) NOT NULL,
 Data_Pagamento DATETIME NOT NULL
);

CREATE TABLE Entrega (
 ID INT PRIMARY KEY,
 Pedido_ID INT FOREIGN KEY REFERENCES Pedido(ID),
 Status VARCHAR(20) NOT NULL,
 Código_Rastreio VARCHAR(20) NOT NULL
);
```

Queries SQL
*Recuperações simples*
```
SELECT * FROM Cliente;
SELECT * FROM Pedido WHERE Status = 'Concluído';
```

Filtros com WHERE
```
SELECT * FROM Produto WHERE Preço > 100;
SELECT * FROM Pedido WHERE Data >= '2022-01-01' AND Data <= '2022-12-31';
```

Expressões para gerar atributos derivados
```
SELECT *, Preço * Quantidade AS Total FROM ItemPedido;
```

Ordenações dos dados com ORDER BY
```
SELECT * FROM Pedido ORDER BY Data DESC;
```

Condições de filtros aos grupos – HAVING
```
SELECT Cliente_ID, COUNT(*) AS Quantidade_Pedidos 
FROM Pedido 
GROUP BY Cliente_ID 
HAVING COUNT(*) > 5;
```

Junções entre tabelas
```
SELECT C.Nome, P.Nome, IP.Quantidade 
FROM Cliente C 
INNER JOIN Pedido P ON C.CPF_CNPJ = P.Cliente_ID 
INNER JOIN ItemPedido IP ON (link unavailable) = IP.Pedido_ID 
INNER JOIN Produto PR ON IP.Produto_ID = (link unavailable);

