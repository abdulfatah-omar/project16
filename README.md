# project16

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Newsletter Signup</title>
</head>
<body>

    <h2>Newsletter Signup</h2>
    
    <form id="newsletterForm" onsubmit="validateForm()">
        <!-- other form fields -->
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>

        <!-- new phone number field -->
        <label for="phone">Phone Number:</label>
        <input type="text" id="phone" name="phone" maxlength="15" placeholder="e.g., 123-456-7890" required>

        <button type="submit">Subscribe</button>
    </form>

    <script>
        function validateForm() {
            // Retrieve phone number input
            var phoneNumber = document.getElementById('phone').value;

            // Check if the phone number is not blank
            if (phoneNumber.trim() === '') {
                alert('Phone number cannot be blank');
                return false;
            }

            // Check if the phone number contains only numbers and dashes
            var phonePattern = /^[0-9\-]+$/;
            if (!phonePattern.test(phoneNumber)) {
                alert('Phone number can only contain numbers and dashes');
                return false;
            }

            // Sanitize the phone number before submitting the form
            var sanitizedPhoneNumber = sanitizePhoneNumber(phoneNumber);
            document.getElementById('phone').value = sanitizedPhoneNumber;

            // Continue with form submission
            // document.getElementById('newsletterForm').submit();
        }

        function sanitizePhoneNumber(phoneNumber) {
            // Implement your sanitization logic here
            // For example, you can remove any non-numeric characters
            return phoneNumber.replace(/[^0-9\-]/g, '');
        }
    </script>

</body>
</html>
