# practical-9-WT-CT-A-24-Tanvi-SAthe
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Admission Registration</title>
  <style>
    body {
      font-family: "Poppins", Arial, sans-serif;
      background: linear-gradient(135deg, #74ebd5, #ACB6E5);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .container {
      background-color: #fff;
      padding: 30px 40px;
      border-radius: 12px;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
      width: 400px;
    }

    h2 {
      text-align: center;
      color: #333;
      margin-bottom: 25px;
    }

    label {
      font-weight: 600;
      color: #444;
      display: block;
      margin-bottom: 5px;
      margin-top: 15px;
    }

    input[type="text"],
    input[type="date"],
    input[type="password"] {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 6px;
      box-sizing: border-box;
      font-size: 15px;
      outline: none;
      transition: border-color 0.3s;
    }

    input:focus {
      border-color: #74b9ff;
    }

    .error {
      color: red;
      font-size: 13px;
      margin-top: 3px;
      display: block;
    }

    input[type="submit"] {
      width: 100%;
      background-color: #4e73df;
      color: white;
      border: none;
      padding: 12px;
      font-size: 16px;
      border-radius: 8px;
      margin-top: 25px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    input[type="submit"]:hover {
      background-color: #375ac3;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Admission Registration</h2>

    <form id="admissionForm" onsubmit="return validateForm()">
      <label>Full Name:</label>
      <input type="text" id="name">
      <span id="nameError" class="error"></span>

      <label>Email:</label>
      <input type="text" id="email">
      <span id="emailError" class="error"></span>

      <label>Phone Number:</label>
      <input type="text" id="phone">
      <span id="phoneError" class="error"></span>

      <label>Date of Birth:</label>
      <input type="date" id="dob">
      <span id="dobError" class="error"></span>

      <label>Password:</label>
      <input type="password" id="password">
      <span id="passwordError" class="error"></span>

      <input type="submit" value="Register">
    </form>
  </div>

  <script>
    function validateForm() {
      const name = document.getElementById("name").value.trim();
      const email = document.getElementById("email").value.trim();
      const phone = document.getElementById("phone").value.trim();
      const dob = document.getElementById("dob").value;
      const password = document.getElementById("password").value.trim();

      document.querySelectorAll(".error").forEach(el => el.textContent = "");

      let valid = true;

      if (name === "" || !/^[A-Za-z\s]+$/.test(name)) {
        document.getElementById("nameError").textContent = "Please enter a valid name (letters only).";
        valid = false;
      }

      const emailPattern = /^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$/;
      if (!emailPattern.test(email)) {
        document.getElementById("emailError").textContent = "Please enter a valid email address.";
        valid = false;
      }

      const phonePattern = /^[0-9]{10}$/;
      if (!phonePattern.test(phone)) {
        document.getElementById("phoneError").textContent = "Please enter a 10-digit phone number.";
        valid = false;
      }

      if (dob) {
        const birthDate = new Date(dob);
        const age = new Date().getFullYear() - birthDate.getFullYear();
        if (age < 16) {
          document.getElementById("dobError").textContent = "You must be at least 16 years old.";
          valid = false;
        }
      } else {
        document.getElementById("dobError").textContent = "Please select your date of birth.";
        valid = false;
      }

      if (password.length < 6) {
        document.getElementById("passwordError").textContent = "Password must be at least 6 characters long.";
        valid = false;
      }

      return valid;
    }
  </script>
</body>
</html>
