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
![Modelagem de Banco de Dados Completa](https://github.com/luizfelipesoarees/modelagem-de-banco-de-dados-completa/assets/141787273/c78bc7e1-2eee-46e3-a12f-636bc43fb9f4)

## 🔢 Modelagem Lógica

## ⚙️ Modelagem Física

## 💻 Dados

## CRUD

## Relatórios
