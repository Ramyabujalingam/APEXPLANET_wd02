# APEXPLANET_wd02
<html>
<head>
    <meta charset="UTF-8">
    <title>Contact & To-Do List</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            background-color: #f4f7fa;
            margin: 0;
            padding: 0;
        }

        nav {
            width: 100%;
            background-color: #3498db;
            color: white;
            padding: 15px 0;
            text-align: center;
        }

        nav a {
            margin: 0 20px;
            font-size: 18px;
            font-weight: bold;
            text-decoration: none;
            color: white;
        }

        nav a:hover {
            text-decoration: underline;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            display: flex;
            flex-direction: column;
            gap: 30px;
            margin-top: 30px;
            align-items: center;
        }

        .box {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            width: 350px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            color: #3498db;
            margin-bottom: 15px;
        }

        label {
            font-size: 16px;
            margin-bottom: 5px;
            color: #555;
        }

        input[type="text"], input[type="email"] {
            width: 100%;
            padding: 10px;
            margin: 8px 0;
            border-radius: 5px;
            border: 1px solid #ddd;
            font-size: 16px;
            transition: border 0.3s ease;
        }

        input[type="text"]:focus, input[type="email"]:focus {
            border-color: #3498db;
            outline: none;
        }

        button {
            width: 100%;
            padding: 10px;
            background-color: #3498db;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #2980b9;
        }

        #formMessage {
            text-align: center;
            color: green;
            font-size: 14px;
            margin-top: 10px;
        }

        ul {
            list-style: none;
            padding: 0;
            margin-top: 20px;
        }

        li {
            background-color: #f1f1f1;
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 5px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        .delete-btn {
            background-color: #e74c3c;
            color: white;
            border: none;
            padding: 4px 8px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 12px;
            transition: background-color 0.3s ease;
            width: auto;
        }

        .delete-btn:hover {
            background-color: #c0392b;
        }
    </style>
</head>
<body>

    <nav>
        <a href="#">INTERACTIVE WEBPAGE</a>
        
    </nav>

    <div class="container">
        <div class="box">
            <h2>Contact Form</h2>
            <form id="contactForm">
                <label for="name">Name</label>
                <input type="text" id="name" placeholder="Enter your name" required><br>
                <label for="email">Email</label>
                <input type="email" id="email" placeholder="Enter your email" required><br>
                <button type="submit">Submit</button>
            </form>
            <p id="formMessage"></p>
        </div>

        <div class="box">
            <h2>To-Do List</h2>
            <input type="text" id="taskInput" placeholder="Enter task" />
            <button onclick="addTask()">Add Task</button>
            <ul id="taskList"></ul>
        </div>
    </div>

    <script>
        // Contact form submission
        document.getElementById("contactForm").addEventListener("submit", function(e) {
            e.preventDefault();
            const name = document.getElementById("name").value;
            const email = document.getElementById("email").value;

            if (name && email) {
                document.getElementById("formMessage").innerText = "Form submitted successfully!";
                document.getElementById("contactForm").reset();
            } else {
                document.getElementById("formMessage").innerText = "Please fill out all fields.";
                document.getElementById("formMessage").style.color = "red";
            }
        });

        // Adding tasks to the list
        function addTask() {
            const input = document.getElementById("taskInput");
            const taskText = input.value.trim();
            if (taskText !== "") {
                const li = document.createElement("li");
                li.textContent = taskText + " ";
                
                const deleteBtn = document.createElement("button");
                deleteBtn.className = "delete-btn";
                deleteBtn.textContent = "X";
                deleteBtn.onclick = () => li.remove();

                li.appendChild(deleteBtn);
                document.getElementById("taskList").appendChild(li);

                input.value = ""; // Clear input after adding task
            }
        }
    </script>

</body>
</html>
