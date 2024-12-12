Script SQL 
```
CREATE TABLE Cliente (
 CPF VARCHAR(11) PRIMARY KEY,
 Nome VARCHAR(100) NOT NULL,
 Endereço VARCHAR(200) NOT NULL,
 Telefone VARCHAR(20) NOT NULL
);

CREATE TABLE Veículo (
 Placa VARCHAR(7) PRIMARY KEY,
 Modelo VARCHAR(50) NOT NULL,
 Ano INT NOT NULL,
 Cor VARCHAR(20) NOT NULL,
 CPF_Cliente VARCHAR(11) FOREIGN KEY REFERENCES Cliente(CPF)
);

CREATE TABLE Ordem_de_Serviço (
 Número_OS INT PRIMARY KEY,
 Data DATE NOT NULL,
 Tipo_Serviço VARCHAR(50) NOT NULL,
 Status VARCHAR(20) NOT NULL,
 Placa_Veículo VARCHAR(7) FOREIGN KEY REFERENCES Veículo(Placa)
);

CREATE TABLE Serviço (
 ID INT PRIMARY KEY,
 Número_OS INT FOREIGN KEY REFERENCES Ordem_de_Serviço(Número_OS),
 Descrição VARCHAR(200) NOT NULL,
 Valor DECIMAL(10, 2) NOT NULL
);

CREATE TABLE Mecânico (
 ID INT PRIMARY KEY,
 Nome VARCHAR(100) NOT NULL,
 Especialidade VARCHAR(50) NOT NULL
);

CREATE TABLE Peça (
 ID INT PRIMARY KEY,
 Descrição VARCHAR(200) NOT NULL,
 Valor DECIMAL(10, 2) NOT NULL
);

CREATE TABLE Serviço_Mecânico (
 ID_Serviço INT FOREIGN KEY REFERENCES Serviço(ID),
 ID_Mecânico INT FOREIGN KEY REFERENCES Mecânico(ID)
);
```

Queries SQL
Recuperações simples
```
SELECT * FROM Cliente;
SELECT * FROM Ordem_de_Serviço WHERE Status = 'Concluído';
```

Filtros com WHERE
```
SELECT * FROM Veículo WHERE Ano > 2010;
SELECT * FROM Serviço WHERE Valor > 100;
```

Expressões para gerar atributos derivados
```
SELECT *, Valor * 1.1 AS Valor_Total FROM Serviço;
```

Ordenações dos dados com ORDER BY
```
SELECT * FROM Ordem_de_Serviço ORDER BY Data DESC;
```

Condições de filtros aos grupos – HAVING
```
SELECT CPF_Cliente, COUNT(*) AS Quantidade_OS 
FROM Ordem_de_Serviço 
GROUP BY CPF_Cliente 
HAVING COUNT(*) > 2;
```

Junções entre tabelas
```
SELECT C.Nome, V.Modelo, OS.Tipo_Serviço 
FROM Cliente C 
INNER JOIN Veículo V ON C.CPF = V.CPF_Cliente 
INNER JOIN Ordem_de_Serviço OS ON V.Placa = OS.Placa_Veículo;
```

