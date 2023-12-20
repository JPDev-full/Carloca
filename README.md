# Modelo de banco de dados da locadora Carloca.

![image](https://github.com/JPDev-full/Carloca/assets/120661541/9bb3b27d-7d86-4b3e-8d25-1d282a1f1aac)


Para constrir a base dados e usar rodar os seguintes comandos no client:

CREATE DATABASE carloca_db;

USE carloca_db;

Para criar as tabelas:

CREATE TABLE Categorias (
    categoria_id INT AUTO_INCREMENT PRIMARY KEY,
    nome_categoria VARCHAR(50) NOT NULL
);

CREATE TABLE Carros (
    carro_id INT AUTO_INCREMENT PRIMARY KEY,
    modelo VARCHAR(50) NOT NULL,
    montadora VARCHAR(50) NOT NULL,
    cor ENUM('branco', 'preto', 'prata') NOT NULL,
    versao VARCHAR(50),
    categoria_id INT,
    quilometragem_atual FLOAT DEFAULT 0,
    locado BOOLEAN DEFAULT 0,
    local_locacao VARCHAR(100),
    FOREIGN KEY (categoria_id) REFERENCES Categorias(categoria_id)
);

CREATE TABLE Clientes (
    cliente_id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    carro_alugado_id INT,
    FOREIGN KEY (carro_alugado_id) REFERENCES Carros(carro_id)
);

CREATE TABLE Historico_Aluguel (
    aluguel_id INT AUTO_INCREMENT PRIMARY KEY,
    carro_id INT,
    cliente_id INT,
    data_inicio DATE,
    data_fim DATE,
    quilometragem_inicial FLOAT,
    quilometragem_final FLOAT,
    local_devolucao VARCHAR(100),
    FOREIGN KEY (carro_id) REFERENCES Carros(carro_id),
    FOREIGN KEY (cliente_id) REFERENCES Clientes(cliente_id)
);

Database Model for Carloca Car Rental Company.

To build the database and use it, run the following commands on the client:

CREATE DATABASE carloca_db;

USE carloca_db;
To create the tables:

CREATE TABLE Categorias (
    categoria_id INT AUTO_INCREMENT PRIMARY KEY,
    nome_categoria VARCHAR(50) NOT NULL
);

CREATE TABLE Carros (
    carro_id INT AUTO_INCREMENT PRIMARY KEY,
    modelo VARCHAR(50) NOT NULL,
    montadora VARCHAR(50) NOT NULL,
    cor ENUM('white', 'black', 'silver') NOT NULL,
    versao VARCHAR(50),
    categoria_id INT,
    quilometragem_atual FLOAT DEFAULT 0,
    locado BOOLEAN DEFAULT 0,
    local_locacao VARCHAR(100),
    FOREIGN KEY (categoria_id) REFERENCES Categorias(categoria_id)
);

CREATE TABLE Clientes (
    cliente_id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    carro_alugado_id INT,
    FOREIGN KEY (carro_alugado_id) REFERENCES Carros(carro_id)
);

CREATE TABLE Historico_Aluguel (
    aluguel_id INT AUTO_INCREMENT PRIMARY KEY,
    carro_id INT,
    cliente_id INT,
    data_inicio DATE,
    data_fim DATE,
    quilometragem_inicial FLOAT,
    quilometragem_final FLOAT,
    local_devolucao VARCHAR(100),
    FOREIGN KEY (carro_id) REFERENCES Carros(carro_id),
    FOREIGN KEY (cliente_id) REFERENCES Clientes(cliente_id)
);
