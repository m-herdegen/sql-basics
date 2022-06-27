1. Select all rows from the classes table.
   SELECT \* FROM classes;

2. Select the name and credits from the classes table where the number of credits is greater than 3.
   SELECT name, credits FROM classes where credits > 3;

3. All rows from the classes table where credits is an even number.
   SELECT \* FROM classes WHERE credits = 2 OR credits = 4;

4. All of Tianna's enrollments that she hasn't yet received a grade for.
   SELECT \* FROM enrollments WHERE student_id = 1 AND grade IS NULL;

5. All of Tianna's enrollments that she hasn't yet received a grade for, selected by her first name, not her student.id
   SELECT enrollments.id, enrollments.student_id, enrollments.class_id, enrollments.grade FROM enrollments INNER JOIN students ON students.id = enrollments.student_id WHERE students.first_name = 'Tianna' AND grade IS NULL;

6. All of Tianna's enrollments that she hasn't yet received a grade for, selected by her first name, not her student.id, with the class name included in the result set.
   SELECT enrollments.id, enrollments.student_id, enrollments.class_id, enrollments.grade, classes.name FROM enrollments INNER JOIN students ON students.id = enrollments.student_id INNER JOIN classes ON classes.id = enrollments.class_id WHERE students.first_name = 'Tianna' AND grade IS NULL;

7. All students born before 1986 who have a 't' in their first or last name.
   SELECT \* FROM students WHERE first_name LIKE '%T%' OR first_name LIKE '%t%' OR last_name LIKE '%T%' OR last_name LIKE '%t%' AND birthdate < '1986-01-01';

8. The average age of all the students.
   SELECT AVG(AGE(birthdate)) from students;

9. Addresses that have a space in their city name.
   SELECT \* FROM addresses WHERE city LIKE '% %';

10. Students & their addresses that live in a city with more than one word in the city name.
    SELECT \* FROM addresses INNER JOIN students ON addresses.id = students.id WHERE city LIKE '% %';

11. The average number of credits for classes offered at the school.
    SELECT AVG(credits) FROM classes;

12. The first and last name of all students who have received an 'A'.
    SELECT students.first_name, students.last_name FROM enrollments INNER JOIN students ON students.id = enrollments.student_id INNER JOIN classes ON classes.id = enrollments.class_id WHERE grade = 'A';

13. Each student's first name and the total credits they've enrolled in.
    SELECT students.first_name, students.last_name, SUM(classes.credits) FROM enrollments INNER JOIN students ON students.id = enrollments.student_id INNER JOIN classes ON classes.id = enrollments.class_id GROUP BY students.first_name, students.last_name;

14. The total number of credits each student has received a grade for.
    SELECT students.first_name, students.last_name, SUM(classes.credits) FROM enrollments INNER JOIN students ON students.id = enrollments.student_id INNER JOIN classes ON classes.id = enrollments.class_id WHERE grade IS NOT NULL GROUP BY students.first_name, students.last_name;

15. All enrollments, including the class name.
    SELECT enrollments.id, enrollments.student_id, enrollments.class_id, enrollments.grade, classes.name FROM enrollments INNER JOIN classes on classes.id = enrollments.class_id;

16. Students born between 1982-1985 (inclusive).
    SELECT \* FROM students WHERE birthdate BETWEEN '1982-01-01' AND '1985-12-31';

17. Insert a new enrollment recording that Andre Rohan took PHYS 218 and got an A.
    INSERT INTO enrollments (student_id, class_id, grade) VALUES(5, 4, 'A');
