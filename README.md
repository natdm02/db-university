DB-UNIVERSITY
===
# TRACCIA:

1.  Selezionare tutti gli studenti nati nel 1990 (160)

2.  Selezionare tutti i corsi che valgono più di 10 crediti (479)

3.  Selezionare tutti gli studenti che hanno più di 30 anni

4.  Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

5.  Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

6.  Selezionare tutti i corsi di laurea magistrale (38)

7. Da quanti dipartimenti è composta l'università? (12)

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

# SVOLGIMENTO:

1. SELECT *
FROM students
WHERE YEAR (date_of_birth) = 1990;

2. SELECT \*  
  FROM `courses`  
  WHERE `cfu` > 10;

3. SELECT \*  
  FROM `students`  
  WHERE (CURDATE()-YEAR(`date_of_birth`)) > 30;

4. SELECT \*  
  FROM `courses`  
  WHERE `period` = 'I semestre' AND  
   `year`=1;

5. SELECT \*  
  FROM `exams`  
  WHERE HOUR(`hour`)> = 14 AND  
   `date`='2020-06-20';

6. SELECT \*  
  FROM `degrees`  
  WHERE level = 'magistrale';

7. SELECT COUNT(\*) AS 'departments'  
  FROM `departments`;

8. SELECT COUNT(\*)  
  FROM `teachers`  
  WHERE phone is NULL;