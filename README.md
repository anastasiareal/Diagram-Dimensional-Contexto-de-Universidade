# Projeto de Modelagem Dimensional (Star Schema)


Este projeto transforma um diagrama relacional de um sistema universitário em um esquema dimensional (star schema) otimizado para análise de dados, com foco nos professores. O objetivo é facilitar consultas analíticas sobre o ensino ministrado por professores, incluindo disciplinas, cursos, departamentos e aspectos temporais. O esquema ignora dados relacionados a alunos, conforme especificado.


O star schema foi projetado para um data warehouse, utilizando uma tabela fato central (Fato_Ensino_Professor) e tabelas de dimensão ao redor dela. A implementação foi feita em PostgreSQL (adaptada para pgAdmin), incluindo scripts para criação de tabelas, população de dados fictícios e exemplos de uso.



**Base do Projeto**

Diagrama Relacional Original: Baseado em um modelo ER com entidades como Professor, Departamento, Disciplina, Curso, Pré-requisitos e Aluno (mas alunos foram excluídos do foco). Relações incluem professores vinculados a departamentos, disciplinas em cursos e pré-requisitos.
Foco: Análise de professores, como disciplinas ministradas, cursos associados e departamentos, com adição de uma dimensão temporal para agregações por data (ex.: semestre, ano).
Motivação: Converter um modelo transacional em analítico para consultas eficientes, como contagens de disciplinas por professor por período.


**Tabela Fato: Fato_Ensino_Professor**

**_Descrição:_** Registra instâncias de ensino. Cada linha representa um professor ministrando uma disciplina em um curso, em um departamento, em uma data específica.
Campos:
Professor_Key (FK para Dim_Professor)
Disciplina_Key (FK para Dim_Disciplina)
Curso_Key (FK para Dim_Curso)
Departamento_Key (FK para Dim_Departamento)
Data_Key (FK para Dim_Data)

**_Descrição:_** Registra instâncias de ensino. Cada linha representa um professor ministrando uma disciplina em um curso, em um departamento, em uma data específica.
Campos:
Professor_Key (FK para Dim_Professor)
Disciplina_Key (FK para Dim_Disciplina)
Curso_Key (FK para Dim_Curso)
Departamento_Key (FK para Dim_Departamento)
Data_Key (FK para Dim_Data)


**Tabelas de Dimensão**

**_Dim_Professor:_** Detalhes dos professores.
Campos: Professor_Key (PK, SERIAL), IdProfessor, Nome_Professor.

**_Dim_Disciplina:_** Detalhes das disciplinas.
Campos: Disciplina_Key (PK, SERIAL), IdDisciplina, Nome_Disciplina, IdPreRequisitos.

**_Dim_Curso:_** Detalhes dos cursos.
Campos: Curso_Key (PK, SERIAL), IdCurso, Nome_Curso.

**_Dim_Departamento:_** Detalhes dos departamentos.
Campos: Departamento_Key (PK, SERIAL), IdDepartamento, Nom, Campus, IdProfessor_Coorden.

**_Dim_Data:_** Dimensão temporal para análises por tempo (granularidade diária).
Campos: Data_Key (PK, SERIAL), Data_Completa (DATE), Ano, Trimestre, Mes, Nome_Mes, Dia, Semana, Semestre, Eh_Feriado (bool).


















