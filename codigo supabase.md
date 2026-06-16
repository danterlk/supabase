DROP TABLE IF EXISTS professores;
DROP TABLE IF EXISTS alunos;
DROP TABLE IF EXISTS turmas;

CREATE TABLE turmas (
  id bigint generated always as identity primary key,
  nome text not null
);

CREATE TABLE alunos (
  id bigint generated always as identity primary key,
  nome text not null,
  turma_id bigint,
  CONSTRAINT fk_turma
    FOREIGN KEY (turma_id)
    REFERENCES turmas(id)
);

CREATE TABLE professores (
  id bigint generated always as identity primary key,
  nome text not null,
  disciplina text not null,
  turma_id bigint,
  CONSTRAINT fk_professor_turma
    FOREIGN KEY (turma_id)
    REFERENCES turmas(id)
);

INSERT INTO turmas (nome)
VALUES
('ds1'),
('ds2'),
('ds3');

INSERT INTO alunos (nome, turma_id)
VALUES
('du', 1),
('dudu', 1),
('edu', 1),
('ailton', 2),
('dã', 2),
('lucas', 2),
('joao', 3),
('nivea', 3),
('melany', 3);

INSERT INTO professores (nome, disciplina, turma_id)
VALUES
('lucas', 'banco de dados', 1),
('gabriel', 'front end', 2),
('juliana', 'logica', 3);

SELECT
  alunos.id,
  alunos.nome,
  turmas.nome AS turma
FROM alunos
JOIN turmas
  ON alunos.turma_id = turmas.id;

SELECT
  professores.id,
  professores.nome,
  professores.disciplina,
  turmas.nome AS turma
FROM professores
JOIN turmas
  ON professores.turma_id = turmas.id;
