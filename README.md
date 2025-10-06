Online Examination System (Console-Based)
Overview

This is a console-based Online Examination System implemented in Java using JDBC for database connectivity.
It supports separate faculty and student dashboards and allows:

Faculty to create question banks, exams, and view student scores.

Students to take exams, answer MCQs and descriptive questions, and view their scores.

Auto-grading for MCQs and manual grading for descriptive answers.

Timed exams with automatic submission on timeout.

All data is managed using MySQL.

Features
Faculty Dashboard

Register/Login securely.

Create Question Bank: Add questions with options, correct answers, marks, and question type (MCQ or descriptive).

Create Exam: Select questions from the bank, set exam duration.

View Student Scores: See scores for all completed exams.

Student Dashboard

Register/Login securely.

View Available Exams: Check all upcoming exams.

Take Exam: Answer MCQs and descriptive questions. Timed auto-submit supported.

View Scores: See scores for completed exams.

Database Schema

The project uses the following tables:

faculty: id, name, email, password

student: id, name, email, password

questions: id, question_text, option_a, option_b, option_c, option_d, correct_option, question_type, marks, correct_text_answer

exams: id, title, duration

exam_questions: id, exam_id, question_id

student_exams: id, student_id, exam_id, start_time, end_time, score, status

student_answers: id, student_exam_id, question_id, selected_option, marks

All foreign key constraints are implemented with ON DELETE CASCADE.

Installation

Clone the repository

git clone https://github.com/yourusername/online-exam-console.git
cd online-exam-console


Set up the database

Create a MySQL database online_exam.

Run the provided SQL script (schema.sql) to create tables with all required columns.

Configure database properties

Edit db.properties in the resources folder:

db.url=jdbc:mysql://localhost:3306/online_exam
db.username=root
db.password=yourpassword


Compile and Run

javac -d bin src/com/onlineexam/**/*.java
java -cp bin com.onlineexam.app.OnlineExamApp

Usage
Faculty

Login with faculty credentials.

Choose options from the faculty menu:

Create question bank

Create exams

View student scores

Student

Login or signup.

View available exams.

Take exams and submit answers.

View past exam scores.

Technologies Used

Java 11+ (Console-based)

JDBC for database connectivity

MySQL 8+ for data storage

ScheduledExecutorService for exam timers

Notes

MCQs are auto-graded.

Descriptive answers need to be graded manually by faculty.

Exam duration is in minutes.

Student answers and scores are saved in real-time to avoid data loss.

Contributing

Contributions are welcome! Please submit a pull request or open an issue for suggestions.

License

This project is licensed under MIT License.
