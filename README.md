## 1

_Selezionare tutti gli studenti nati nel 1990 (160)_

- SELECT \* FROM `students` WHERE YEAR(date_of_birth) = 1990;

## 2

_Selezionare tutti i corsi che valgono più di 10 crediti (479)_

- SELECT \* FROM `courses` WHERE cfu > 10;

## 3

_Selezionare tutti gli studenti che hanno più di 30 anni_

- SELECT \* FROM `students` WHERE date_of_birth < '1993-10-01';

## 4

_Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)_

- SELECT \* FROM `courses` WHERE period = 'I semestre' AND year = 1;

## 5

_Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)_

- SELECT \* FROM `exams` WHERE date = '2020-06-20' and hour > '14:00:00';

## 6

_Selezionare tutti i corsi di laurea magistrale (38)_

- SELECT \* FROM `degrees` WHERE name LIKE '%magistrale%';

## 7

_Da quanti dipartimenti è composta l'università? (12)_

- SELECT count(\*) FROM `departments`;

## 8

_Quanti sono gli insegnanti che non hanno un numero di telefono? (50)_

- SELECT count(\*) FROM `teachers` WHERE phone is NULL;
