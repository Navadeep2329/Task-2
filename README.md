<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Frontend Practice Project</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background-color: #f2f2f2;
    }

    /* Layout */
    .container {
      display: grid;
      grid-template-columns: 1fr 2fr;
      gap: 20px;
      padding: 20px;
    }

    .nav {
      background-color: #333;
      color: white;
      padding: 20px;
      display: flex;
      flex-direction: column;
    }

    .nav a {
      color: white;
      text-decoration: none;
      margin-bottom: 10px;
    }

    .content {
      background-color: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    /* Contact Form */
    .contact-form input,
    .contact-form textarea,
    .contact-form button {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    .contact-form button {
      background-color: #28a745;
      color: white;
      border: none;
      cursor: pointer;
    }

    /* To-Do List */
    .todo-section input {
      width: 70%;
      padding: 10px;
      margin-top: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    .todo-section button {
      padding: 10px;
      margin-left: 10px;
      border-radius: 5px;
      background-color: #007bff;
      color: white;
      border: none;
      cursor: pointer;
    }

    ul {
      list-style-type: none;
      padding-left: 0;
    }

    ul li {
      background-color: #eee;
      margin-top: 5px;
      padding: 10px;
      border-radius: 5px;
      cursor: pointer;
    }

    /* Responsive */
    @media (max-width: 768px) {
      .container {
        grid-template-columns: 1fr;
      }
      .nav {
        flex-direction: row;
        justify-content: space-around;
      }
    }
  </style>
</head>
<body>

  <div class="container">
    <!-- Navigation -->
    <div class="nav">
      <a href="#">Home</a>
      <a href="#">Contact</a>
      <a href="#">To-Do</a>
    </div>

    <!-- Main Content -->
    <div class="content">
      <h2>Contact Form</h2>
      <form id="contactForm" class="contact-form">
        <input type="text" id="name" placeholder="Your Name" required>
        <input type="email" id="email" placeholder="Your Email" required>
        <textarea id="message" placeholder="Your Message" rows="4" required></textarea>
        <button type="submit">Send</button>
      </form>

      <hr>

      <h2>To-Do List</h2>
      <div class="todo-section">
        <input type="text" id="taskInput" placeholder="Enter a task">
        <button onclick="addTask()">Add Task</button>
        <ul id="taskList"></ul>
      </div>
    </div>
  </div>

  <script>
    // Contact Form Validation
    document.getElementById("contactForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const name = document.getElementById("name").value.trim();
      const email = document.getElementById("email").value.trim();
      const message = document.getElementById("message").value.trim();

      if (!name || !email || !message) {
        alert("Please fill in all fields.");
        return;
      }

      const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
      if (!email.match(emailPattern)) {
        alert("Please enter a valid email address.");
        return;
      }

      alert("Form submitted successfully!");
    });

    // To-Do List Functionality
    function addTask() {
      const input = document.getElementById("taskInput");
      const task = input.value.trim();
      if (task === "") return;

      const li = document.createElement("li");
      li.textContent = task;
      li.onclick = function() {
        this.remove();
      };
      document.getElementById("taskList").appendChild(li);
      input.value = "";
    }
  </script>

</body>
</html>
