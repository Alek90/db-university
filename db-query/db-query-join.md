## Query con Join
-Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
-Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze
-Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
-Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
-Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
-Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
-BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami


## Query
-SELECT `students`.* FROM `degrees` JOIN `students` ON `degrees`.`id` = `students`.`degree_id` WHERE `degrees`.`name` = 'Corso di Laurea in Economia'
-SELECT `degrees`.*, `departments`.`name` as `department_name` FROM `departments` JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id` WHERE `departments`.`name` = 'Dipartimento di Neuroscienze'
-SELECT `courses`.* FROM `courses` JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` WHERE `teachers`.`name` = 'Fulvio' AND `teachers`.`surname` = 'Amato'
-SELECT `students`.`surname` as `student_surname`, `students`.`name` as `student_name`, `students`.`registration_number` as `student_registration_number`, `degrees`.*, `departments`.`name` as `department_name` FROM `departments` JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id` JOIN `students` ON `degrees`.`id` = `students`.`degree_id` ORDER BY `student_surname`, `student_name`
-SELECT `degrees`.*, `courses`.`name` as `course_name`, `courses`.`period` as `course_period`, `courses`.`year` as `course_year`, `teachers`.`name` as `teacher_name`, `teachers`.`surname` as `teacher_surname` FROM `degrees` JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id` JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` ORDER BY `degrees`.`id` ASC
-SELECT DISTINCT `teachers`.* FROM `teachers` JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id` JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id` JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `departments`.`name` = 'Dipartimento di Matematica'
-BONUS--SELECT `students`.`surname` as `student_surname`, `students`.`name` as `student_name`, `courses`.`name` as `exam_course_name`, COUNT(`vote`) as `number_time` FROM `exam_student` JOIN `students` ON `exam_student`.`student_id` = `students`.`id` JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id` JOIN `courses` ON `exams`.`course_id` = `courses`.`id` GROUP BY `student_surname`, `student_name`, `exam_course_name`







