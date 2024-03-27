<script>
    import "../app.css";
  import PriorityColor from "./components/priorityColor.svelte";
  import TaskForm from "./components/taskForm.svelte";
  </script>
  
  <slot />

  <div class="flex flex-col justify-center w-full items-center m-6">
    <TaskForm/>
    <PriorityColor/>

  </div>
  