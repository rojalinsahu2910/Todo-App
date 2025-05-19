import React, { useState } from 'react';
import 'bootstrap/dist/css/bootstrap.min.css'; // Import Bootstrap

function App() {
  const [todos, setTodos] = useState([]); // List of todos
  const [task, setTask] = useState('');   // Current task input
  const [date, setDate] = useState('');   // Current date input

  // Add new todo
  const addTodo = () => {
    if (task && date) {
      setTodos([...todos, { task, date }]);
      setTask('');
      setDate('');
    }
  };

  // Delete todo by index
  const deleteTodo = (index) => {
    const updated = todos.filter((_, i) => i !== index);
    setTodos(updated);
  };

  return (
    <div className="container mt-5">
      <h2 className="text-center mb-4">Todo App</h2>

      <div className="row mb-3">
        <div className="col">
          <input
            type="text"
            className="form-control"
            placeholder="Enter Todo here"
            value={task}
            onChange={(e) => setTask(e.target.value)}
          />
        </div>
        <div className="col">
          <input
            type="date"
            className="form-control"
            value={date}
            onChange={(e) => setDate(e.target.value)}
          />
        </div>
        <div className="col">
          <button className="btn btn-success w-100" onClick={addTodo}>
            Add
          </button>
        </div>
      </div>

      {todos.map((todo, index) => (
        <div className="row mb-2" key={index}>
          <div className="col">{todo.task}</div>
          <div className="col">{todo.date}</div>
          <div className="col">
            <button
              className="btn btn-danger w-100"
              onClick={() => deleteTodo(index)}
            >
              Delete
            </button>
          </div>
        </div>
      ))}
    </div>
  );
}

export default App;
