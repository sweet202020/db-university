Group by:
Contare quanti iscritti ci sono stati ogni anno
```sql
SELECT YEAR(`enrolment_date`) as 'anno', COUNT(id) as 'students_for_year'
FROM `students`
GROUP BY YEAR(`enrolment_date`);
```
Contare gli insegnanti che hanno l'ufficio nello stesso edificio
```sql
SELECT office_address as 'buildings', COUNT(id) as 'number_of_teachers'
FROM `teachers`
GROUP BY (office_address);
```

Calcolare la media dei voti di ogni appello d'esame
```sql
SELECT `exam_id` as 'appello', AVG(vote) as 'media_voto'
FROM `exam_student`
GROUP BY(`exam_id`);
```

Contare quanti corsi di laurea ci sono per ogni dipartimento
```sql
SELECT `department_id` as 'dipartimento', COUNT(id) as 'numero_corsi'
FROM `degrees`
GROUP BY(`department_id`);
```
