1) Selezionare tutti gli studenti nati nel 1990 (160)

SELECT * FROM students WHERE YEAR(date_of_birth)=1990; 

--------------------------------------------------------
2) Selezionare tutti i corsi che valgono più di 10 crediti (479)

SELECT name FROM courses WHERE cfu > 10; 

--------------------------------------------------------
3) Selezionare tutti gli studenti che ad OGGI hanno almeno 30 anni compiuti (3725)

SELECT name FROM students WHERE date_of_birth>DATEADD(CURRENT_DATE, -30, YEAR) 
#1305 - FUNCTION university.DATEADD does not exist

--------------------------------------------------------
4) Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

SELECT * FROM courses WHERE period = "I semestre" AND year = 1

--------------------------------------------------------
5) Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

SELECT * FROM exams WHERE date = '2020-06-20' AND hour > '14:00:00'

--------------------------------------------------------
6) Selezionare tutti i corsi di laurea magistrale (38)

SELECT * FROM degrees WHERE level = 'magistrale'

--------------------------------------------------------
7) Da quanti dipartimenti è composta l'università? (12)

SELECT COUNT(id) FROM departments

--------------------------------------------------------
8) Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

SELECT COUNT(id) FROM teachers WHERE phone is null

--------------------------------------------------------
9) Inserire nella tabella degli studenti un nuovo record con i propri dati (per il campo degree_id, inserire un valore casuale)

INSERT INTO students (date_of_birth, degree_id, email, enrolment_date, fiscal_code, name, surname)
VALUES ('1995-02-23', 15, 'pippo.pinko@gmail.com', CURRENT_DATE, 'ABCDEF12G34H567I', 'Pippo', 'Pinko')

--------------------------------------------------------
10) Cambiare il numero dell’ufficio del professor Pietro Rizzo in 126

UPDATE teachers
SET office_number='126'
WHERE name='Pietro' AND surname='Rizzo'

--------------------------------------------------------
11) Eliminare dalla tabella studenti il record creato precedentemente al punto 9

DELETE FROM students WHERE surname='Pinko'