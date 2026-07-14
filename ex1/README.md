# SQL Lab Experiments

## Experiment 1

### Query 1

```sql
SELECT * FROM Students;
```

### Output

| StudentID | Name | Age |
|-----------|------|-----|
| 1 | Alice | 20 |
| 2 | Bob | 22 |
| 3 | Charlie | 21 |
| 4 | David | 19 |

---

### Query 2

```sql
SELECT Name, Age FROM Students WHERE Age > 20;
```

### Output

| Name | Age |
|------|-----|
| Bob | 22 |
| Charlie | 21 |

---

### Query 3

```sql
SELECT Name FROM Students
WHERE StudentID IN (
SELECT StudentID
FROM Enrollments
WHERE CourseID = (
SELECT CourseID
FROM Courses
WHERE CourseName='Database Management'
));
```

### Output

| Name |
|------|
| Alice |
| Bob |
| Charlie |

---

### Query 4

```sql
SELECT CourseID, CourseName
FROM Courses
WHERE CourseID IN (
SELECT CourseID
FROM Enrollments
GROUP BY CourseID
HAVING COUNT(*) > 1);
```

### Output

| CourseID | CourseName |
|----------|----------------------|
| 101 | Database Management |

---

### Query 5

```sql
SELECT AVG(Age) AS AverageAge FROM Students;
```

### Output

| AverageAge |
|------------|
| 20.5 |

---

### Query 6

```sql
SELECT Name, Age
FROM Students
WHERE Age > (SELECT AVG(Age) FROM Students);
```

### Output

| Name | Age |
|------|-----|
| Bob | 22 |
| Charlie | 21 |

---

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