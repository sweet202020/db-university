Modellizzare la struttura di una tabella per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi **Dipartimenti** (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più **Corsi di Laurea** (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni **Corso di Laurea** prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni **Corso** può essere tenuto da diversi Insegnanti;
- ogni **Corso** prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo **Corso** di Laurea;
- ogni Studente può iscriversi a più **appelli** di Esame;
- per ogni appello **d'Esame** a cui lo **Studente** ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.


departments
degree course
courses
teachers
students
exams

## departments

- departments_id | BIGINT | NOTNULL | UNIQUE | AI
- name
- rector


## degree_courses
- degree_courses_id | BIGINT | NOTNULL | UNIQUE | AI
- dep_id
- name 
- students_number
- teachers_numbers
- classes
- number_exams

## courses
- course_id | BIGINT | NOTNULL | UNIQUE | AI
- degree_courses_id
- name
- cfu
- teacher
- class
- lesson_hours
- students_number

# teachers
- teachers_id | BIGINT | NOTNULL | UNIQUE | AI
- course_id
- name
- surname
- email
- age
- courses_name


## students
- student_id | BIGINT | NOTNULL | UNIQUE | AI
- degree_courses_id | BIGINT 
- freshnumber_id | CHAR()
- name
- surname
- numbers_of_cfu


## exams
- exam_id| BIGINT | NOTNULL | UNIQUE | AI
- date
- vote
- numb_of_appeals
- teacher_id
- student_id
- course_id


# relationship

- oneToMany: departments => degree_courses
- oneToMany: degree_courses => courses
- ManyToMany=> courses && teachers + pivot table
- oneToMany: courses => exams
- oneToMany: students => exams
- oneToMany: degree_courses => students