<script>
    import "../app.css";
  import TaskForm from "./components/taskForm.svelte";
  let task =[];
  $:console.log(task)


  function addNewTask(e) {

    task=[ e.detail, ...task]
  }

  
  </script>
  
  <slot />

  <div class="flex flex-col justify-center w-full items-center m-6">
    <TaskForm on:createTask={addNewTask}/>

  </div>
  