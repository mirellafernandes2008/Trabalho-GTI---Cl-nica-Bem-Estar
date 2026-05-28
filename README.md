CREATE DATABASE clinica_bem_estar;
USE clinica_bem_estar;

CREATE TABLE tbl_pacientes (
    id_paciente INT AUTO_INCREMENT PRIMARY KEY,
    nome_paciente VARCHAR(100) NOT NULL,
    telefone_paciente VARCHAR(13) NOT NULL,
    cpf_paciente VARCHAR(14) NOT NULL,
    email_paciente VARCHAR(100) NOT NULL
);

CREATE TABLE tbl_agendamentos (
    id_agendamento INT AUTO_INCREMENT PRIMARY KEY,
    data_hora_agendamento DATETIME,
    lab_agendamento VARCHAR(100),
    fk_paciente INT
);

CREATE TABLE tbl_feedbacks (
    id_feedback INT AUTO_INCREMENT PRIMARY KEY,
    profissional_feedback VARCHAR(100),
    fk_paciente INT
);

ALTER TABLE tbl_agendamentos
ADD CONSTRAINT FOREIGN KEY (fk_paciente)
REFERENCES tbl_pacientes(id_paciente);

ALTER TABLE tbl_feedbacks
ADD CONSTRAINT FOREIGN KEY (fk_paciente)
REFERENCES tbl_pacientes(id_paciente);
