# Experiment 2

### Inner Join

```sql
SELECT Students.StudentID, Students.Name, Students.Age,
Courses.CourseID, Courses.CourseName, Enrollments.Grade
FROM Students
INNER JOIN Enrollments
ON Students.StudentID = Enrollments.StudentID
INNER JOIN Courses
ON Enrollments.CourseID = Courses.CourseID;
```

### Output

| StudentID | Name | Age | CourseID | CourseName | Grade |
|-----------|------|-----|----------|------------|-------|
| 1 | Alice | 20 | 1 | Math | A |
| 1 | Alice | 20 | 2 | English | B |
| 2 | Bob | 22 | 1 | Math | A- |
| 3 | Charlie | 21 | 3 | History | B+ |
| 3 | Charlie | 21 | 2 | English | A |

---

### Left Join

```sql
SELECT Students.StudentID, Students.Name, Students.Age,
Courses.CourseID, Courses.CourseName, Enrollments.Grade
FROM Students
LEFT JOIN Enrollments
ON Students.StudentID = Enrollments.StudentID
LEFT JOIN Courses
ON Enrollments.CourseID = Courses.CourseID;
```

### Output

| StudentID | Name | Age | CourseID | CourseName | Grade |
|-----------|------|-----|----------|------------|-------|
| 1 | Alice | 20 | 1 | Math | A |
| 1 | Alice | 20 | 2 | English | B |
| 2 | Bob | 22 | 1 | Math | A- |
| 3 | Charlie | 21 | 3 | History | B+ |
| 3 | Charlie | 21 | 2 | English | A |
| 4 | David | 19 | NULL | NULL | NULL |

---

### Right Join

```sql
SELECT Students.StudentID, Students.Name, Students.Age,
Courses.CourseID, Courses.CourseName, Enrollments.Grade
FROM Courses
RIGHT JOIN Enrollments
ON Courses.CourseID = Enrollments.CourseID
RIGHT JOIN Students
ON Enrollments.StudentID = Students.StudentID;
```

### Output

| StudentID | Name | Age | CourseID | CourseName | Grade |
|-----------|------|-----|----------|------------|-------|
| 1 | Alice | 20 | 1 | Math | A |
| 1 | Alice | 20 | 2 | English | B |
| 2 | Bob | 22 | 1 | Math | A- |
| 3 | Charlie | 21 | 3 | History | B+ |
| 3 | Charlie | 21 | 2 | English | A |
| 4 | David | 19 | NULL | NULL | NULL |