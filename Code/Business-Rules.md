# Business Rules

The application uses Business Rules to perform calculations automatically
when the related records are created or updated.

## Percentage Calculation

Used in the Academic table to calculate the student's percentage from
the total marks and obtained marks.

```javascript
(function executeRule(current, previous) {

    var totalMarks = parseFloat(current.total_marks);
    var obtainedMarks = parseFloat(current.obtained_marks);

    if (totalMarks > 0 && obtainedMarks >= 0 && obtainedMarks <= totalMarks) {
        current.percentage = (obtainedMarks / totalMarks) * 100;
    }

})(current, previous);
```

## Grade Calculation

Used in the Academic table to assign a grade based on the calculated
percentage.

```javascript
(function executeRule(current, previous) {

    var percentage = parseFloat(current.percentage);

    if (!isNaN(percentage)) {

        if (percentage >= 90) {
            current.grade = 'S';
        } else if (percentage >= 80) {
            current.grade = 'A';
        } else if (percentage >= 70) {
            current.grade = 'B';
        } else if (percentage >= 60) {
            current.grade = 'C';
        } else if (percentage >= 50) {
            current.grade = 'D';
        } else {
            current.grade = 'F';
        }
    }

})(current, previous);
```

## Attendance Percentage Calculation

Used in the Attendance table to calculate the student's attendance
percentage from the total number of classes and attended classes.

```javascript
(function executeRule(current, previous) {

    var totalClasses = parseFloat(current.total_classes);
    var attendedClasses = parseFloat(current.attended_classes);

    if (totalClasses > 0 && attendedClasses >= 0 && attendedClasses <= totalClasses) {
        current.attendance_percentage =
            (attendedClasses / totalClasses) * 100;
    }

})(current, previous);
```

## Fee Outstanding Calculation

Used in the Fee table to calculate the remaining fee amount from
the total fee and paid fee.

```javascript
(function executeRule(current, previous) {

    var totalFee = parseFloat(current.total_fee);
    var paidFee = parseFloat(current.paid_fee);

    if (!isNaN(totalFee) && !isNaN(paidFee) && paidFee >= 0 && paidFee <= totalFee) {
        current.fee_outstanding = totalFee - paidFee;
    }

})(current, previous);
```
