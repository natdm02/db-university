DB-UNIVERSITY QUERY JOIN
===
# TRACCIA:
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

# SVOLGIMENTO:

1. SELECT `students`.`name`,`students`.`surname`, `degrees`.`name`  
  FROM `students`  
  INNER JOIN `degrees`  
  ON `students`.`degree_id`= `degrees`.`id`  
  WHERE `degrees`.`name`= "Corso di Laurea in Economia";

2. SELECT \*  
  FROM `degrees`  
  INNER JOIN `departments`  
  ON `degrees`.`department_id`= `departments`.`id`  
  WHERE `departments`.`name`="Dipartimento di Neuroscienze" AND  
  `degrees`.`level`="magistrale";

3. SELECT \*  
  FROM `course_teacher`  
  INNER JOIN `courses`  
  ON `course_teacher`.`course_id` = `courses`.`id`  
  INNER JOIN `teachers`  
  ON `course_teacher`.`teacher_id` = `teachers`.`id`  
  WHERE `teachers`.`id`= 44;

4. SELECT \*  
  FROM `students`  
  INNER JOIN `degrees`  
  ON `students`.`degree_id` = `degrees`.`id`  
  INNER JOIN `departments`  
  ON `degrees`.`department_id` = `departments`.`id`  
  ORDER BY `students`.`surname` ASC;

5. SELECT \*  
  FROM `students`  
  INNER JOIN `degrees`  
  ON `students`.`degree_id` = `degrees`.`id`  
  INNER JOIN `departments`  
  ON `degrees`.`department_id` = `departments`.`id`  
  ORDER BY `students`.`surname` ASC;

6. SELECT DISTINCT `teachers`.`name`,`teachers`.`surname`,`departments`.`name`  
   FROM `teachers`  
   INNER JOIN `course_teacher`  
   ON `course_teacher`.`teacher_id`= `teachers`.`id`  
  INNER JOIN `courses`  
   ON `courses`.`id` = `course_teacher`.`course_id`  
   INNER JOIN `degrees`  
   ON `courses`.`degree_id` = `degrees`.`id`  
  INNER JOIN `departments`  
   ON `degrees`.`department_id` = `departments`.`id`  
  WHERE `departments`.`name`="Dipartimento di Matematica"  
  ORDER BY `teachers`.`surname` ASC;

7. 