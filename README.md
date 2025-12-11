# serverlab4
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Student Grades-ES6+Async</title>
    </head>
    <body>
        <h2>Student Grades-ES6 +Async</h2>
        <pre id="output"></pre>

        <script>
            class Student {
                constructor(id, name, marks) {
                    this.id = id;
                    this.name = name;
                    this.marks = marks;
                }

                getGrade() {
                    if (this.marks >= 90) return "A+";
                    if (this.marks >= 80) return "A";
                    if (this.marks >= 70) return "B";
                    if (this.marks >= 60) return "C";
                    return "D";
                }

                showDetails = () => {
                    return `ID: ${this.id}
Name:${this.name}
Marks:${this.marks}
Grade:${this.getGrade()}
--------------------`;
                };
            }

            const fetchStudents = () =>
                fetch("students.json").then(res => res.json());

            const displayGrades = async () => {
                try {
                    const data = await fetchStudents();
                    let output = "";
                    const students = data.map(s => new Student(s.id, s.name, s.marks));

                    students.forEach(stu => {
                        output += stu.showDetails() + "\n";
                    });

                    document.getElementById("output").textContent = output;
                } catch {
                    document.getElementById("output").textContent = "Error";
                }
            };

            displayGrades();
        </script>
    </body>
</html>
//////////////students.json/////
[
    { "id": 1, "name": "Alice", "marks": 92 },
    { "id": 2, "name": "Bob", "marks": 85 },
    { "id": 3, "name": "Charlie", "marks": 73 },
    { "id": 4, "name": "David", "marks": 66 },
    { "id": 5, "name": "Eva", "marks": 58 }
]
///////////lab3//////////
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <h2>Employee Details</h2>
        <pre id="output"></pre>

        <script>
            class Employee {
                constructor(id, name, position, salary) {
                    this.id = id;
                    this.name = name;
                    this.position = position;
                    this.salary = salary;
                }

                showDetails = () => {
                    return `Employee ID: ${this.id}
Name: ${this.name}
Position: ${this.position}
Salary: ${this.salary}
--------------------`;
                };
            }

            const emp1 = new Employee(101, "Ravi", "Manager", 5000);
            const emp2 = new Employee(102, "Raj", "Tester", 5000);
            const emp3 = new Employee(103, "Rani", "Manager", 5000);

            const employees = [emp1, emp2, emp3];

            let outputText = "";

            for (let emp of employees) {
                outputText += emp.showDetails() + "\n";
            }

            document.getElementById("output").textContent = outputText;
        </script>
    </body>
</html>
