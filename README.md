# sqlquerry
CREATE TABLE Disciplina (
    DisciplinaId INT PRIMARY KEY,
    Descricao VARCHAR(200),
    Sigla CHAR(3)
);

INSERT INTO Disciplina (DisciplinaId, Descricao, Sigla)
VALUES (1, 'Matemática', 'MAT'),
       (2, 'História', 'HIS'),
       (3, 'Ciências', 'CIE');

CREATE TABLE Aluno (
    AlunoId INT PRIMARY KEY,
    Nome NVARCHAR(100),
    DataNascimento DATE
);

INSERT INTO Aluno (AlunoId, Nome, DataNascimento)
VALUES (1, 'João', '2000-05-15'),
       (2, 'Maria', '1998-10-22'),
       (3, 'Pedro', '2002-03-08');

CREATE TABLE DisciplinaAluno (
    DisciplinaId INT,
    AlunoId INT,
    SemestreLetivo VARCHAR(20),
    DataMatricula DATE,
    Conceito CHAR(1),
    PRIMARY KEY (DisciplinaId, AlunoId, SemestreLetivo),
    FOREIGN KEY (DisciplinaId) REFERENCES Disciplina(DisciplinaId),
    FOREIGN KEY (AlunoId) REFERENCES Aluno(AlunoId)
);

INSERT INTO DisciplinaAluno (DisciplinaId, AlunoId, SemestreLetivo, DataMatricula, Conceito)
VALUES (1, 1, '2023A', '2023-01-15', 'A'),
       (2, 2, '2023A', '2023-02-20', 'B'),
       (3, 3, '2023B', '2023-03-10', 'C');

       --ex alterar constrain 
       
CREATE TABLE UF (
    ID_UF INT PRIMARY KEY IDENTITY, 
    Cod_UF INT NOT NULL,
    DescUF nvarchar(50) NOT NULL
);

CREATE TABLE IDE (
    ID_IDE INT PRIMARY KEY IDENTITY, 
    Cod_UF INT NOT NULL
    DescIDE nvarchar(50) NOT NULL
);

ALTER TABLE IDE
ADD CONSTRAINT IDE_UF_FK FOREIGN KEY (Cod_UF) REFERENCES UF (ID_UF);
