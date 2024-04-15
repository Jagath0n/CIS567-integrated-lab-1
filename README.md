# CIS567-integrated-lab-1
copy of code from Integrated Lab

HOMEWORK_MAX = 800.0;
QUIZZES_MAX = 400.0;
MIDTERM_MAX = 150.0;
FINAL_MAX = 200.0;

# Type your code here.
def calculate_average(points, max_points):
    if points > max_points:
        return 100.0
    else:
        return (points / max_points) * 100.0

def calculate_course_average(status, homework_avg, quizzes_avg, midterm_avg, final_exam_avg):
    if status == "UG":
        return (0.20 * homework_avg) + (0.20 * quizzes_avg) + (0.30 * midterm_avg) + (0.30 * final_exam_avg)
    elif status == "G":
        return (0.15 * homework_avg) + (0.05 * quizzes_avg) + (0.35 * midterm_avg) + (0.45 * final_exam_avg)
    elif status == "DL":
        return (0.05 * homework_avg) + (0.05 * quizzes_avg) + (0.40 * midterm_avg) + (0.50 * final_exam_avg)

def get_letter_grade(average):
    if average >= 90.0:
        return "A"
    elif 80.0 <= average < 90.0:
        return "B"
    elif 70.0 <= average < 80.0:
        return "C"
    elif 60.0 <= average < 70.0:
        return "D"
    else:
        return "F"

def main():
    status = input()
    if status not in ["UG", "G", "DL"]:
        print("Error: student status must be UG, G or DL")
        return

    homework, quizzes, midterm, final_exam = map(float, input().split())

    homework_avg = calculate_average(homework, 800)
    quizzes_avg = calculate_average(quizzes, 400)
    midterm_avg = calculate_average(midterm, 150)
    final_exam_avg = calculate_average(final_exam, 200)

    print(f"Homework: {homework_avg:2.1f}%")
    print(f"Quizzes: {quizzes_avg:2.1f}%")
    print(f"Midterm: {midterm_avg:2.1f}%")
    print(f"Final Exam: {final_exam_avg:2.1f}%")

    homework_avg = min(homework_avg, 100.0)
    quizzes_avg = min(quizzes_avg, 100.0)
    midterm_avg = min(midterm_avg, 100.0)
    final_exam_avg = min(final_exam_avg, 100.0)

    course_avg = calculate_course_average(status, homework_avg, quizzes_avg, midterm_avg, final_exam_avg)
    print(f"{status} average: {course_avg:2.1f}%")

    letter_grade = get_letter_grade(course_avg)
    print(f"Course grade: {letter_grade}")

if __name__ == "__main__":
    main()
