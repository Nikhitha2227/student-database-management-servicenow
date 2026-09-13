# Client Scripts

Client Scripts are used to validate form data and control field behavior on the client side.

## Marks Validation

Used in the Academic table to validate the obtained marks entered by the user.

```javascript
function onChange(control, oldValue, newValue, isLoading) {

    if (isLoading || newValue == '') {
        return;
    }

    var obtainedMarks = parseFloat(newValue);

    if (isNaN(obtainedMarks) || obtainedMarks < 0) {
        g_form.showFieldMsg(
            'obtained_marks',
            'Enter a valid marks value.',
            'error'
        );

        g_form.setValue('obtained_marks', '');
    }
}
```

## Attendance Validation

Used in the Attendance table to validate the number of attended classes entered by the user.

```javascript
function onChange(control, oldValue, newValue, isLoading) {

    if (isLoading || newValue == '') {
        return;
    }

    var attendedClasses = parseInt(newValue, 10);

    if (isNaN(attendedClasses) || attendedClasses < 0) {
        g_form.showFieldMsg(
            'attended_classes',
            'Enter a valid number of attended classes.',
            'error'
        );

        g_form.setValue('attended_classes', '');
    }
}
```

## Fee Validation

Used in the Fee table to validate the paid fee amount.

```javascript
function onChange(control, oldValue, newValue, isLoading) {

    if (isLoading || newValue == '') {
        return;
    }

    var paidFee = parseFloat(newValue);

    if (isNaN(paidFee) || paidFee < 0) {
        g_form.showFieldMsg(
            'paid_fee',
            'Enter a valid fee amount.',
            'error'
        );

        g_form.setValue('paid_fee', '');
    }
}
```
