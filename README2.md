# QUERY GROUP BY

## 1

_Contare quanti iscritti ci sono stati ogni anno_

- SELECT count(\*) , YEAR(`enrolment_date`) as `anno` FROM `students`
  GROUP BY `anno`

## 2

_Contare gli insegnanti che hanno l'ufficio nello stesso edificio_

- SELECT count(\*), `office_address` FROM `teachers`
  GROUP BY `office_address`

## 3

_Calcolare la media dei voti di ogni appello d'esame_

- SELECT `exam_id`, avg(`vote`) FROM `exam_student` GROUP BY `exam_id`

## 4

_Contare quanti corsi di laurea ci sono per ogni dipartimento_

- SELECT COUNT(\*), `department_id` FROM `degrees` GROUP BY `department_id`

# QUERY JOIN

## 1.

_Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia_

- SELECT `students`.`name` ,`students`.`surname` ,`students`.`registration_number`
  FROM `students`
  JOIN `degrees`
  ON `students`.`degree_id` = `degrees`.`id`
  WHERE `degrees`.`name` = 'Corso di Laurea in Economia'

## 2.

_Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze_

- SELECT `degrees`.\*
  FROM `degrees`
  JOIN `departments`
  ON `degrees`.`department_id`= `departments`.`id`
  WHERE `departments`.`name` = 'Dipartimento di Neuroscienze'
  AND `degrees`.`level`= 'magistrale'

## 3.

_Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)_

- SELECT \*
  FROM `courses`
  JOIN `course_teacher`
  ON `courses`.`id` = `course_teacher`.`course_id`  
  JOIN `teachers`
  ON `course_teacher`.`teacher_id` = `teachers`.`id`
  WHERE `teachers`.`id` = 44

## 4.

_Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome_

- SELECT `students`.`surname`,`students`.`name`,`students`.`registration_number`,`degrees`.`name`,`departments`.`name`
  FROM `students`
  JOIN `degrees`
  ON `students`.`degree_id` = `degrees`.`id`
  JOIN `departments`
  ON `degrees`.`department_id` = `departments`.`id`
  ORDER BY `students`.`surname`,`students`.`name`

## 5.

_Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti_

- SELECT `degrees`.`name`, `courses`.`name`, `teachers`.`name`,`teachers`.`surname`
  FROM `degrees`
  JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
  JOIN `course_teacher` ON `courses`.`id`= `course_teacher`.`course_id`
  JOIN `teachers` ON `course_teacher`.`teacher_id` =`teachers`.`id`

## 6.

_Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)_

- SELECT DISTINCT `teachers`.`id`, `teachers`.`name`, `teachers`.`surname`
  FROM `teachers`
  JOIN `course_teacher` ON `teachers`.`id` =`course_teacher`.`teacher_id`
  JOIN `courses` ON `course_teacher`.`course_id` =`courses`.`id`
  JOIN `degrees` ON `courses`.`degree_id` =`degrees`.`id`
  JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
  WHERE `departments`.`name` = 'Dipartimento di Matematica'
