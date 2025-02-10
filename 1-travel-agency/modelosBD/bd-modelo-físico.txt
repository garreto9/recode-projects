create database travel_agency;

use travel_agency;

CREATE TABLE CLIENTE (
    Telefone VARCHAR(15),
    CPF CHAR(11),
    Email VARCHAR(50),
    Nome VARCHAR(50),
    ID_Cliente VARCHAR(10) PRIMARY KEY
);

CREATE TABLE Cliente_Reserva (
    ID_Cliente VARCHAR(10),
    ID_Reserva VARCHAR(10),
    FOREIGN KEY(ID_Cliente) REFERENCES CLIENTE (ID_Cliente)
);

CREATE TABLE RESERVA (
    ID_Reserva VARCHAR(10) PRIMARY KEY,
    Estado_Reserva VARCHAR(10),
    Data_Reserva DATE,
    ID_Pagamento VARCHAR(10)
);

CREATE TABLE PAGAMENTO (
    Valor_Pago NUMERIC(10),
    ID_Pagamento VARCHAR(10) PRIMARY KEY,
    Forma_Pagamento VARCHAR(30),
    Data_Pagamento DATETIME
);

CREATE TABLE Cliente_Viagem (
    ID_Viagem VARCHAR(10),
    ID_Cliente VARCHAR(10),
    FOREIGN KEY(ID_Cliente) REFERENCES CLIENTE (ID_Cliente)
);

CREATE TABLE VIAGEM (
    Data_Retorno DATETIME,
    ID_Viagem VARCHAR(10) PRIMARY KEY,
    Data_Partida DATETIME,
    Codigo_Viagem VARCHAR(10),
    Preco VARCHAR(20),
    Destino VARCHAR(50)
);

CREATE TABLE PACOTE (
    ID_Pacote VARCHAR(10) PRIMARY KEY,
    Valor VARCHAR(20),
    Duracao DATETIME,
    Itens_Inclusos VARCHAR(30),
    Destino VARCHAR(50),
    Nome VARCHAR(50)
);

ALTER TABLE Cliente_Reserva ADD FOREIGN KEY(ID_Reserva) REFERENCES RESERVA (ID_Reserva);
ALTER TABLE RESERVA ADD FOREIGN KEY(ID_Pagamento) REFERENCES PAGAMENTO (ID_Pagamento);
ALTER TABLE Cliente_Viagem ADD FOREIGN KEY(ID_Viagem) REFERENCES VIAGEM (ID_Viagem);
