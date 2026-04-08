# To-Do-List-With-ReactJs

📘 React To-Do List App

A simple and efficient To-Do List application built with React.js. This project demonstrates how to manage tasks using React Hooks and basic state management.

🚀 Features
➕ Add new tasks
❌ Delete tasks
✔️ Mark tasks as completed
🔄 Dynamic UI updates
⚡ Fast and responsive


🛠️ Technologies Used
React.js
JavaScript (ES6+)
HTML5
CSS3

💡 How It Works
Tasks are stored using React's useState hook
Users can add tasks through an input field
Each task can be:
marked as completed
deleted
React updates the UI automatically when the state changes

<img width="1593" height="735" alt="Todo1" src="https://github.com/user-attachments/assets/215f8ef3-1521-40c6-a53a-09f4588f55cb" />


ToDoList.jsx

```
import React, {useState} from 'react'

function ToDoList(){
    const [tasks,setTasks] = useState(["Eat Breakfast", "Take a shower", "Walk the dog"])
    const [newTask, setNewTask] = useState("")
    

    function handleInput(event){
        setNewTask(event.target.value)
    }
    function addTask(){

        if(newTask.trim() !== ""){
             setTasks(t =>[...t, newTask])
            setNewTask("")
        }
    }
    function deleteTask(index){
        const updatedTasks = tasks.filter((_, i) => i !== index)
        setTasks(updatedTasks)
    }   

    function moveTaskUp(index){
        if(index > 0){
            const updatedTasks = [...tasks];
            [updatedTasks[index], updatedTasks[index - 1]] = 
            [updatedTasks[index -1], updatedTasks[index]]
            setTasks(updatedTasks)
        }
    }

    function moveTaskDown(index){
            if(index < tasks.length -1){
            const updatedTasks = [...tasks];
            [updatedTasks[index], updatedTasks[index + 1]] = 
            [updatedTasks[index + 1], updatedTasks[index]]
            setTasks(updatedTasks)
        }
    }
    
    return(
            <div className='to-do-list'>
                <h1>To-Do-List</h1>
                
                
                <div>
                <input 
                    type="text" 
                        placeholder='Enter a task...'
                            value={newTask}
                               onChange={handleInput}/>
                
                <button 
                    className='add-button'
                         onClick={addTask}>Add</button>
                </div>

                <ol>
                    {tasks.map((task, index) =>
                        <li key={index}>
                            <span className='text'>{task}</span>
                            <button 
                                className='delete-button'
                                    onClick={() => deleteTask(index)}>
                                Delete
                            </button>

                            <button 
                                className='move-button'
                                    onClick={() => moveTaskUp(index)}>
                                ☝
                            </button>

                              <button 
                                className='move-button'
                                    onClick={() => moveTaskDown(index)}>
                                👇
                            </button>
                        </li>
                    )}
                </ol>

            </div>
    )

}

export default ToDoList
```

APP.JSX
```
import ToDoList from "./ToDoList"

function App() {
  return(
    <>
      <ToDoList/>
    </>
  )
}

export default App
```

index.css

```
body{
    background-color: rgb(39, 36, 36);
}

.to-do-list{
    font-family: Arial, Helvetica, sans-serif;
    text-align: center;
    margin-top: 100px;
}
h1{
    font-size: 4rem;
    color: white;
}

button{
    font-size: 1.7rem;
    font-weight: bold;
    padding: 10px 20px;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.5s ease; 
}
.add-button{
    background-color: hsl(120, 91%, 35%);
}
.add-button:hover{
    background-color: hsl(120, 87%, 26%);
}

.delete-button{
    background-color: hsl(7, 100%, 39%);
}
.delete-button:hover{
    background-color: hsl(0, 100%, 32%);
}

.move-button{
    background-color: hsl(172, 97%, 35%);
}
.move-button:hover{
      background-color: hsl(172, 98%, 22%);
}
input[type="text"]{
    font-size: 1.6rem;
    padding: 10px;
    border: 2px solid hsl(0, 0%, 57%);
    border-radius: 5px;
    color: rgba(0, 0, 0, 0.918);
}
ol{
    padding: 0;

}
li{
    font-size: 2rem;
    font-weight: bold;
    padding: 15px;
    background-color: hsl(0, 4%, 87%);
    margin-bottom: 10px;
    border: 3px solid rgb(70, 66, 66);
    border-radius: 5px;
    display: flex;
    align-items: center;
}

.text{
   flex: 1;
}
.delete-button, .move-button{
    padding: 8px 12px;
    font-size: 1.4rem;
    margin-left: 10px;
}

```

🤝 Contributing

Contributions are welcome! Feel free to fork this repository and submit a pull request

📄 License

This project is open-source and available under the MIT License
