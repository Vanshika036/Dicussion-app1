<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>To-Do App</title>
 <style>
  body {
   display: flex;
   font-family: Arial, sans-serif;
  }
  .container {
   width: 100%;
   display: flex;
  }
  .left-pane, .right-pane {
   flex: 1;
   padding: 20px;
  }
  .left-pane {
   border-right: 1px solid #ddd;
  }
  .task-list {
   list-style-type: none;
   padding: 0;
  }
  .task-list li {
   padding: 10px;
   display: flex;
   justify-content: space-between;
   align-items: center;
   border-bottom: 1px solid #ddd;
  }
  .task-list li.completed {
   text-decoration: line-through;
  }
  .delete-btn, .complete-btn {
   cursor: pointer;
  }
  form {
   display: flex;
   flex-direction: column;
  }
  form input, form button {
   margin-bottom: 10px;
  }
 </style>
</head>
<body>
 <div class="container">
  <!-- Left pane (task list) -->
  <div class="left-pane">
   <h2>Task List</h2>
   <ul class="task-list" id="task-list">
    <!-- Tasks will be added here dynamically -->
   </ul>
  </div>

  <!-- Right pane (task form) -->
  <div class="right-pane">
   <h2>Add New Task</h2>
   <form id="task-form">
    <input type="text" id="task-input" placeholder="Enter task" required>
    <button type="submit">Add Task</button>
   </form>
  </div>
 </div>

 <script>
  // Select form elements and task list
  const taskForm = document.getElementById('task-form');
  const taskInput = document.getElementById('task-input');
  const taskList = document.getElementById('task-list');

  // Event listener for form submission
  taskForm.addEventListener('submit', function(event) {
   event.preventDefault(); // Prevent form from submitting

   // Get the task input value
   const taskText = taskInput.value;

   // Create a new task item (li)
   const newTask = document.createElement('li');
   newTask.textContent = taskText;

   // Create the complete button
   const completeBtn = document.createElement('button');
   completeBtn.textContent = 'Complete';
   completeBtn.classList.add('complete-btn');
   completeBtn.addEventListener('click', function() {
    newTask.classList.toggle('completed');
   });

   // Create the delete button
   const deleteBtn = document.createElement('button');
   deleteBtn.textContent = '❌';
   deleteBtn.classList.add('delete-btn');
   deleteBtn.addEventListener('click', function() {
    taskList.removeChild(newTask);
   });

   // Append buttons to the task
   newTask.appendChild(completeBtn);
   newTask.appendChild(deleteBtn);

   // Add the new task to the task list
   taskList.appendChild(newTask);

   // Clear the task input field
   taskInput.value = '';
  });
 </script>
</body>
</html>
