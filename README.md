CREATE DATABASE IF NOT EXISTS arquitetura_academia;
USE arquitetura_academia;

-- Tabelas representando os componentes do sistema
CREATE TABLE FrontEnd_Web (
    id INT PRIMARY KEY AUTO_INCREMENT,
    descricao VARCHAR(100) DEFAULT 'React + TypeScript'
);

CREATE TABLE Mobile_App (
    id INT PRIMARY KEY AUTO_INCREMENT,
    descricao VARCHAR(100) DEFAULT 'Flutter'
);

CREATE TABLE API_Backend (
    id INT PRIMARY KEY AUTO_INCREMENT,
    descricao VARCHAR(100) DEFAULT 'Node.js + NestJS'
);

CREATE TABLE Database_Postgres (
    id INT PRIMARY KEY AUTO_INCREMENT,
    descricao VARCHAR(100) DEFAULT 'PostgreSQL (RDS AWS)'
);

CREATE TABLE Biometria (
    id INT PRIMARY KEY AUTO_INCREMENT,
    descricao VARCHAR(100) DEFAULT 'Módulo Biometria'
);

CREATE TABLE Pagamento (
    id INT PRIMARY KEY AUTO_INCREMENT,
    descricao VARCHAR(100) DEFAULT 'Integração com Gateway'
);

CREATE TABLE Infra_AWS (
    id INT PRIMARY KEY AUTO_INCREMENT,
    descricao VARCHAR(100) DEFAULT 'Infraestrutura em AWS'
);

-- Simulando ligações via FOREIGN KEYS (apenas para visualização)
ALTER TABLE FrontEnd_Web ADD COLUMN backend_id INT, ADD FOREIGN KEY (backend_id) REFERENCES API_Backend(id);
ALTER TABLE Mobile_App ADD COLUMN backend_id INT, ADD FOREIGN KEY (backend_id) REFERENCES API_Backend(id);
ALTER TABLE API_Backend ADD COLUMN db_id INT, ADD FOREIGN KEY (db_id) REFERENCES Database_Postgres(id);
ALTER TABLE API_Backend ADD COLUMN biometria_id INT, ADD FOREIGN KEY (biometria_id) REFERENCES Biometria(id);
ALTER TABLE API_Backend ADD COLUMN pagamento_id INT, ADD FOREIGN KEY (pagamento_id) REFERENCES Pagamento(id);
ALTER TABLE API_Backend ADD COLUMN infra_id INT, ADD FOREIGN KEY (infra_id) REFERENCES Infra_AWS(id);
