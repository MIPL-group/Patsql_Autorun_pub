# Source: PATSQL-StackOverflow
## Group: dev_set
### ID: 059M

# input:input1

| SchoolAvg:Str | exams_description:Str | School:Str |
|---|---|---|
| .90 | Medical Asst.Exam | School A |
| .88 | Health Exam | School A |
| .65 | EKG Exam | School A |
| .76 | Phlebotomy | School A |
| .93 | Medical Asst.Exam | School B |
| .79 | Health Exam | School B |
| .82 | EKG Exam | School B |
| .76 | Phlebotomy | School B |

# input:input0

| NationalAvg:Str | exams_description:Str |
|---|---|
| .78 | Medical Asst.Exam |
| .90 | Health Exam |
| .79 | EKG Exam |
| .81 | Phlebotomy |
| .88 | XXXXXXXXXX |

# constraint

{
  "constants": [],
  "aggregation_functions": []
}

# output:output

| School Avg:Str | NationalAvg:Str | exams_description:Str | School:Str |
|---|---|---|---|
| .90 | .78 | Medical Asst.Exam | School A |
| .88 | .90 | Health Exam | School A |
| .65 | .79 | EKG Exam | School A |
| .76 | .81 | Phlebotomy | School A |
| .93 | .78 | Medical Asst.Exam | School B |
| .79 | .90 | Health Exam | School B |
| .82 | .79 | EKG Exam | School B |
| .76 | .81 | Phlebotomy | School B |
| NULL | .88 | XXXXXXXXXX | NULL |

# solution

```sql
select A.exams_description, A.NationalAvg, B.schools_name, B.SchoolAvg
from CTE A
left Join CTE1 B ON A.exams_description = B.exams_description
```
