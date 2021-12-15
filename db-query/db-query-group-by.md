## Query con Group by
-Contare quanti iscritti ci sono stati ogni anno
-Contare gli insegnanti che hanno l'ufficio nello stesso edificio
-Calcolare la media dei voti di ogni appello d'esame
-Contare quanti corsi di laurea ci sono per ogni dipartimento




## Query
-SELECT COUNT(*) as `number_of_enrolment`, YEAR(`enrolment_date`) as `enrolment_year` FROM `students` GROUP BY `enrolment_year`
-SELECT COUNT(*) as `teachers_in_address`, `office_address` as `address` FROM `teachers` GROUP BY `address`
-SELECT `exam_id` as `exam_id`, COUNT(*) as `exam_number`, AVG(`vote`) as `exam_votes_average` FROM `exam_student` GROUP BY `exam_id`
-SELECT `departments`.`name` as `department_name`, COUNT(*) as `degrees_in_department` FROM `departments` JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id` GROUP BY `department_name`

