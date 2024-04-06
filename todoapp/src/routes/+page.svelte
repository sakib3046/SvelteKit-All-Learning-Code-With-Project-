<script>
    import "../app.css";
    import {taskStore} from '../store'
  import CreatedTasks from "./components/createdTasks.svelte";
    import TaskForm from "./components/taskForm.svelte";
    // import { onDestroy } from "svelte";


    // const unsubscribe =taskStore.subscribe(value=>{
    //   taskStore= value;
    // })

    // onDestroy(()=>{
    //   unsubscribe()
    // })

    $:console.log($taskStore)
  
  </script>
  
  <slot />

  <div class="flex flex-col justify-center w-full items-center m-6">
    <TaskForm/>
    <CreatedTasks  taskList={$taskStore}/>

  </div>
  