# Sistema de Gestão Acadêmica para uma Universidade 🎓

## 📜 Sobre o projeto 
> O sistema de Gestão Acadêmica uma plataforma integrada que visa otimizar e centralizar a administração de informações acadêmicas. Ele abrange aspectos como registro de estudantes, gerenciamento de cursos, acompanhamento do desempenho dos alunos, atribuição de notas, matrículas em disciplinas, coordenação de cursos e interações entre professores e estudantes. A plataforma oferece eficiência na gestão de dados, facilita processos administrativos, e proporciona uma visão abrangente das atividades acadêmicas, contribuindo para a melhoria da qualidade educacional e facilitando a tomada de decisões institucionais.

## 📂 Cenário
> Em uma renomada universidade, conhecida por sua ampla oferta de cursos e comprometimento com o sucesso acadêmico de seus estudantes, surge a necessidade de implementar um Sistema de Gestão Acadêmica. Este sistema visa otimizar a administração de informações relacionadas a estudantes, cursos, professores, disciplinas e matrículas. A crescente complexidade das operações acadêmicas demanda uma solução eficiente para garantir transparência, eficiência e uma experiência acadêmica aprimorada. <br /><br />
Estudantes são identificados por seu nome e data de nascimento, e a idade é derivada desses dados. O endereço é representado de maneira composta, incluindo rua, número e bairro. Múltiplos emails podem ser associados a um estudante, e o Registro Acadêmico (RA) atua como chave única de identificação. <br /><br />
Cada curso é singularmente identificado por um nome, e a coordenação é representada como um atributo composto, incluindo o nome do coordenador e seu email. Um ID exclusivo distingue cada curso. <br /><br />
Professores têm atributos simples, como nome e data de nascimento, e a disciplina lecionada é multivalorada, indicando que um professor pode ensinar várias disciplinas. O ID é a chave exclusiva de cada professor. <br /><br />
Disciplinas têm atributos simples, como nome da disciplina e aulas semanais. A carga horária é derivada do número de aulas, e um ID exclusivo identifica cada disciplina. <br /><br />
Notas são caracterizadas por atributos simples, como data da avaliação e valor da nota. O ID atua como chave exclusiva para cada nota. <br /><br />
Os relacionamentos são fundamentais neste cenário acadêmico. Estudantes são matriculados em cursos, e professores ministram disciplinas. A relação entre estudantes e disciplinas reflete o fato de que vários estudantes frequentam várias disciplinas e vice-versa. A matrícula de estudantes em disciplinas é modelada como uma relação M:N. <br /><br />
A coordenação de cursos é uma relação, onde cada curso é coordenado por um único professor, e reciprocamente, um professor coordena no máximo um curso. A atribuição de notas segue uma relação, onde cada nota é atribuída por um único professor, que pode atribuir várias notas. A avaliação é uma relação, indicando que uma disciplina está associada a várias notas por meio de avaliações, e várias notas estão associadas a várias disciplinas. <br /><br />
A implementação desse Sistema de Gestão Acadêmica proporcionará à universidade um controle mais efetivo sobre matrículas, frequências, desempenho acadêmico e coordenação de cursos. Essa solução abrangente visa aprimorar a experiência acadêmica de estudantes, professores e administradores, contribuindo para o sucesso educacional e administrativo da instituição.
>
## 📊 Modelagem Conceitual
![Modelagem de Banco de Dados Completa](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/bdca5f3b-d7f6-404f-bd6b-17817c678c04)

## 🔢 Modelagem Lógica
![Modelagem Lógica](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/2bb4894c-f724-4ee4-8f98-42241c63d215)

## ⚙️ Modelagem Física
Foi utilizado o seguinte código para a implementação desse cenário no SQL Server: 
> CREATE table Estudante ( <br />
  	RA INT PRIMARY Key, <br />
  	Nome VARCHAR(60), <br />
    Data_nasc DATE, <br />
  	Idade INT, <br />
  	Endereco VARCHAR(60), <br />
  	Rua VARCHAR(60), <br />
  	N INT, <br />
  	Bairro VARCHAR(60), <br />
  	Email VARCHAR(60), <br />
  ); <br /><br />
  
 > CREATE TABLE Email ( <br />
    id INT PRIMARY KEY, <br />
    Email VARCHAR(60), <br />
    estudante_ra INT, <br />
    FOREIGN KEY (estudante_ra) REFERENCES Estudante(RA) <br />
); <br /><br />
  
 > CREATE table Curso ( <br />
  	id INT PRIMARY Key, <br />
  	Nome VARCHAR(60), <br />
    Coordenacao VARCHAR(60), <br />
  	Nome_cord VARCHAR(60), <br />
  	Email_cord VARCHAR(60), <br />
  ); <br /><br />
  
  > CREATE TABLE EstudanteCurso (<br />
    estudante_ra INT, <br />
    curso_id INT, <br />
    PRIMARY KEY (estudante_ra, curso_id), <br />
    FOREIGN KEY (estudante_ra) REFERENCES Estudante(RA), <br />
    FOREIGN KEY (curso_id) REFERENCES Curso(id) <br />
); <br /><br />

> CREATE TABLE Email_Cord ( <br />
    id INT PRIMARY KEY, <br />
    Email VARCHAR(60), <br />
    curso_id INT, <br />
    FOREIGN KEY (curso_id) REFERENCES Curso(id) <br />
); <br /><br />
  
 > CREATE table Disciplina ( <br />
  	id INT PRIMARY Key, <br />
  	Nome VARCHAR(60), <br />
    Aulas_semanais INT, <br />
  	Carga_horaria INT, <br />
  ); <br /><br />
  
  > CREATE TABLE EstudanteDisciplina ( <br />
    estudante_ra INT, <br />
    disciplina_id INT, <br />
    PRIMARY KEY (estudante_ra, disciplina_id), <br />
    FOREIGN KEY (estudante_ra) REFERENCES Estudante(RA), <br />
    FOREIGN KEY (disciplina_id) REFERENCES Disciplina(id) <br />
); <br /><br />

> CREATE TABLE NotaDisciplina ( <br />
    nota_id INT, <br />
    disciplina_id INT, <br />
    PRIMARY KEY (nota_id, disciplina_id), <br />
    FOREIGN KEY (nota_id) REFERENCES Nota(id), <br />
    FOREIGN KEY (disciplina_id) REFERENCES Disciplina(id) <br />
); <br /><br />

> CREATE table Professor ( <br />
  	id INT PRIMARY Key, <br />
  	Nome VARCHAR(60), <br />
    data_nasc DATE, <br />
  	Disciplinas_lecionadas VARCHAR(60), <br />
  ); <br /><br />
  
  > CREATE TABLE Disciplinas_leciona ( <br />
    id INT PRIMARY KEY, <br />
    Disciplinas VARCHAR(60), <br />
    professor_id INT, <br />
    FOREIGN KEY (professor_id) REFERENCES Professor(id) <br />
); <br /><br />

  > CREATE table Nota ( <br />
  	id INT PRIMARY Key, <br />
  	Data_avaliacao DATE, <br />
    Valor_nota INT, <br />
  );

## 💻 Dados
Aqui segue a iserção de dados de todas as tabelas:
> Estudante:
![insert_tabela_estudante](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/cc7cdeb8-68b9-4e18-889e-60b642cefa05)
> 
![tabela_estudante](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/8f7bf0a6-57db-44d5-9409-a55d5978804b)
> Email: ![insert_tabela_email](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/c654cfb6-6d2e-4087-9b4f-f17074d16fe9)
> 
![tabela_email](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/bd2c3e07-3894-42fd-9f70-cdfe6aa38322)
> Curso: ![insert_tabela_curso](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/0132a350-5ab2-4733-9808-ee6eca84943c)
> 
![tabela_curso](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/9d2d432d-8f9e-4663-b68e-06ffc33ce9a0)
> EstudanteCurso:![insert_tabela_estudantecurso](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/9ab87aa9-96c8-465e-b13c-8d473b347095)
>
![_tabela_estudantecurso](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/468f5cc2-2891-4a8f-90e0-79e18a96485d)
> Disciplina: ![insert_tabela_disciplina](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/71f36538-6dd2-48ce-aa9c-0afed7104c21)
> 
![tabela_disciplina](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/ef0ef93d-3488-435a-bd56-023c92812b1f)
> EstudanteDisciplina: ![insert_tabela_estudante_disc](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/1ba2dfe2-e4d4-447c-82ec-b1d7c867376b)
> 
![tabela_estudante_disc](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/7b8c580d-21d2-47bf-b91e-99eeb6316073)
> Email_Cord: ![insert_tabela_email_c](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/d736d065-8f56-4074-9c85-1518d01b697a)
> 
![tabela_email_c](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/89c5d6cd-72d1-4182-a27e-5a88dc4e2067)
> Professor: ![insert_tabela_professor](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/3c11d37c-266d-4477-b105-27ebe3b4e2de)
> 
![tabela_professor](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/6136995e-14b3-41c8-b9ab-3cd8a8d64b30)
> Disciplinas_leciona: ![tabela_dis_l](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/420743b4-506c-4ffa-ad19-ae00bdf462e4)
>
> ![insert_tabela_dis_l](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/075cef5b-c153-49e0-a9cf-c0a428c1a940)
> Nota: ![insert_tabela_nota](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/33e84a31-cf94-4385-9330-f35a702ddcef)
> 
![tabela_nota](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/1fc29512-ca94-4e4a-8144-04d329c071f8)
> NotaDisciplina: ![insert_tabela_notadisc](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/9a8b203a-e5aa-4901-a072-99faea8ccb45)
> 
![tabela_notadisc](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/22e61714-d35e-4eaf-8cd0-b4ef86496fa4)

## CRUD

## Relatórios
