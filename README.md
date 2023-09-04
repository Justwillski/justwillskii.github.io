<!DOCTYPE html>
<html>
<head>
    <title>Todo List App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }

        #app {
            max-width: 400px;
            margin: 0 auto;
        }

        #taskInput {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        li {
            display: flex;
            align-items: center;
            justify-content: space-between;
            background-color: #f5f5f5;
            padding: 10px;
            margin-bottom: 5px;
        }

        .delete-button {
            background-color: #ff4d4d;
            color: white;
            border: none;
            padding: 5px 10px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div id="app">
        <h1>Todo List</h1>
        <input type="text" id="taskInput" placeholder="Add a new task">
        <ul id="taskList"></ul>
    </div>

    <script>
        const taskInput = document.getElementById('taskInput');
        const taskList = document.getElementById('taskList');

        // Function to add a new task
        function addTask() {
            const taskText = taskInput.value.trim();
            if (taskText !== '') {
                const li = document.createElement('li');
                li.innerHTML = `
                    ${taskText}
                    <button class="delete-button">Delete</button>
                `;
                taskList.appendChild(li);

                // Clear the input field
                taskInput.value = '';

                // Attach a click event to the delete button
                const deleteButton = li.querySelector('.delete-button');
                deleteButton.addEventListener('click', function() {
                    taskList.removeChild(li);
                });
            }
        }

        // Listen for Enter key press to add a new task
        taskInput.addEventListener('keyup', function(event) {
            if (event.key === 'Enter') {
                addTask();
            }
        });
    </script>
</body>
</html>
