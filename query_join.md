1) Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT students.name, students.surname, degrees.name 
FROM students 
INNER JOIN degrees ON students.degree_id=degrees.id
WHERE degrees.name='Corso di Laurea in Economia'

-------------------------------------------------------------------
2) Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT degrees.name, departments.name FROM degrees INNER JOIN departments ON degrees.department_id=departments.id 
AND departments.name='Dipartimento di Neuroscienze' 
WHERE degrees.level='magistrale'

-------------------------------------------------------------------
3) Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT * FROM courses INNER JOIN teachers ON teachers.id=44

-------------------------------------------------------------------
4) Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT students.name, students.surname, degrees.name, departments.name
FROM students
INNER JOIN degrees ON students.degree_id=degrees.id
INNER JOIN departments ON degrees.department_id=departments.id
ORDER BY students.surname, students.name

-------------------------------------------------------------------
5) Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT degrees.name, courses.name, teachers.name, teachers.surname
FROM degrees
INNER JOIN courses ON degrees.id=courses.degree_id
INNER JOIN course_teacher ON courses.id=course_teacher.course_id
INNER JOIN teachers ON course_teacher.teacher_id=teachers.id
ORDER BY degrees.name, courses.name, teachers.surname

-------------------------------------------------------------------
6) Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (5)

SELECT teachers.name, teachers.surname, departments.name
FROM teachers
INNER JOIN course_teacher ON teachers.id=course_teacher.teacher_id
INNER JOIN courses ON course_teacher.course_id=courses.id
INNER JOIN degrees on courses.degree_id=degrees.id
INNER JOIN departments ON degrees.department_id=departments.id
WHERE departments.id=5

-------------------------------------------------------------------
7) BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

(Tentativo)
SELECT students.name, students.surname, COUNT(exams.course_id), MAX(exam_student.vote)
FROM students
INNER JOIN exam_student ON students.id=exam_student.student_id
INNER JOIN exams ON exam_student.exam_id=exams.id
GROUP BY exams.course_id
ORDER BY students.surname, students.name, exams.date

-------------------------------------------------------------------