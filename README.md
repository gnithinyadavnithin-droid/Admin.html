<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>King's Ganesh - Admin</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #ff6b00, #ffb300);
  min-height: 100vh;
  padding: 20px;
}

.container {
  max-width: 900px;
  margin: auto;
}

.card {
  background: white;
  border-radius: 20px;
  padding: 25px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

.logo {
  text-align: center;
  font-size: 45px;
}

h1 {
  text-align: center;
  color: #d35400;
}

.subtitle {
  text-align: center;
  color: #666;
}

input {
  width: 100%;
  padding: 14px;
  margin: 10px 0;
  border: 1px solid #ddd;
  border-radius: 10px;
  font-size: 16px;
}

button {
  width: 100%;
  padding: 14px;
  border: none;
  border-radius: 10px;
  background: #e65100;
  color: white;
  font-size: 17px;
  font-weight: bold;
  cursor: pointer;
}

button:hover {
  background: #bf360c;
}

#error {
  color: red;
  text-align: center;
  margin-top: 10px;
}

#adminPanel {
  display: none;
  margin-top: 20px;
}

.search {
  margin-bottom: 15px;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 15px;
}

th, td {
  padding: 12px;
  border-bottom: 1px solid #ddd;
  text-align: left;
}

th {
  background: #ff9800;
  color: white;
}

.logout {
  background: #555;
  margin-top: 20px;
}

.logout:hover {
  background: #333;
}

@media (max-width: 600px) {
  table {
    font-size: 13px;
  }

  th, td {
    padding: 8px;
  }
}
</style>
</head>

<body>

<div class="container">

  <div class="card" id="loginBox">

    <div class="logo">🙏</div>

    <h1>King's Ganesh</h1>

    <p class="subtitle">
      🔐 Admin Access
    </p>

    <input
      type="password"
      id="password"
      placeholder="Enter Admin Password"
    >

    <button onclick="login()">
      🔓 Open Admin Panel
    </button>

    <p id="error"></p>

  </div>


  <div class="card" id="adminPanel">

    <div class="logo">🙏</div>

    <h1>King's Ganesh Admin</h1>

    <p class="subtitle">
      Registered Participants
    </p>

    <input
      class="search"
      type="text"
      id="search"
      placeholder="Search name, mobile or token..."
      onkeyup="searchTable()"
    >

    <table id="tokenTable">

      <thead>
        <tr>
          <th>Token</th>
          <th>Name</th>
          <th>Mobile</th>
        </tr>
      </thead>

      <tbody>

        <!-- ADD YOUR PRIVATE DEMO DATA HERE -->

        <tr>
          <td>KG0001</td>
          <td>Example Name</td>
          <td>9876543210</td>
        </tr>

        <tr>
          <td>KG0002</td>
          <td>Example Person</td>
          <td>9123456780</td>
        </tr>

      </tbody>

    </table>

    <button class="logout" onclick="logout()">
      🔒 Logout
    </button>

  </div>

</div>


<script>

/*
  IMPORTANT:
  This is only a basic website password.
  Do NOT use it for highly confidential information.
*/

const ADMIN_PASSWORD = "KINGSGANESH2026";


function login() {

  const enteredPassword =
    document.getElementById("password").value;

  if (enteredPassword === ADMIN_PASSWORD) {

    document.getElementById("loginBox").style.display = "none";

    document.getElementById("adminPanel").style.display = "block";

  } else {

    document.getElementById("error").textContent =
      "❌ Incorrect password";

  }
}


function logout() {

  document.getElementById("adminPanel").style.display = "none";

  document.getElementById("loginBox").style.display = "block";

  document.getElementById("password").value = "";

  document.getElementById("error").textContent = "";

}


function searchTable() {

  const search =
    document.getElementById("search").value.toLowerCase();

  const rows =
    document.querySelectorAll("#tokenTable tbody tr");

  rows.forEach(function(row) {

    const text =
      row.textContent.toLowerCase();

    row.style.display =
      text.includes(search) ? "" : "none";

  });

}

</script>

</body>
</html>
