comp.js
const Comp = () => {
    return (
      <div className="text-white">
        <div>div1</div>
        <div>div2</div>
      </div>
    );
  };
  
  export default Comp;
....................................................................................................
Task.jsx
  import { CheckIcon, Plus, Trash } from "lucide-react";

const Task = ({ task }) => {
  return (
    <div
      className={`flex items-center justify-between px-3 py-6 bg-purple-950/50 rounded-lg ${
        task.done
          ? "line-through text-gray-500"
          : "text-purple-400"
      }`}
    >
      <p className="text-base pe-3">{task.text}</p>
      <div className="flex items-center gap-4">
        <button>
          {task.done ? (
            <Plus className="h-5 w-5" />
          ) : (
            <CheckIcon className="h-5 w-5" />
          )}
        </button>
        <button className="text-purple-500 hover:text-purple-500/80">
          <Trash />
        </button>
      </div>
    </div>
  );
};

export default Task; 
.........................................................
Taskinput.jsx

import { Plus } from "lucide-react";
import React from "react";

const TaskInput = () => {
  return (
    <form className="flex justify-center gap-2 p-4 w-full">
     <input
        type="text"
        placeholder="Add a new task"
        className="bg-white/5 text-white w-full py-2 px-4 outline-none border-purple-700/50 rounded-lg"
        />
        <button
         type="submit"
         className="bg-purple-700 border border-purple-700/50 text-white rounded-lg hover:bg-purple-400/80 p-3"
        >
          <Plus className="h-5 w-5" />
        </button>
      </form>
    );
};  

export default TaskInput;
.............................................
Taskinput.jsx

import React from 'react'
import Task from './Task';

const TaskList = ({ tasks, done }) => {
  return (
    <section className="p-4 flex flex-col gap-3 w-full">
      <h2 className="text-lg font-semibold text-purple-200 ">
        {tasks.done === true
        ? 'Done - ${tasks.length}'
        : 'Task to do - ${tasks.length}'}
       </h2>

      <div className="flex flex-col gap-2">
        {tasks.map((task)=>(
          <Task task={task} />
        ))}
        </div>
      </section>
  );
};
       
export default TaskList;

APP.js
import Comp from "./Components/Comp"
import TaskInput from "./Components/TaskInput";
import TaskList from "./components/TaskList";

const dummy = [
  {
    id: 1,
    text: "Complete React project setup",
    done: false,
  },
  {
    id: 2,
    text: "Fix Vite dynamic import issue",
    done: false,
  },
  { id: 3, text: "Review pull requests", done: true },
  {
    id: 4,
    text: "Write unit tests for TaskList component",
    done: false,
  },
  { id: 5, text: "Prepare for project demo", done: true },
];

export default function App() {
  return (
    <div className="container mx-auto grid grid-col-2 gap-x-10">
    <div className ="text-black">Coming soon</div>
    <div className="h-full flex-col justify-start items-center w-full px-5">
    <TaskInput />
    <div>
      <TaskList
       tasks={task.filter((task) => !task.done)}
       done={false}
      />
      <TaskList
       tasks={task.filter((task) => task.done)}
       />
    </div>
    </div>
  </div>
 ); 
}

index.css
@tailwind base;
@tailwind components;
@tailwind utilities;
