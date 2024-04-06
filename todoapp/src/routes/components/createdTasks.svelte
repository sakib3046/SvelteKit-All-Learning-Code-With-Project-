<script>
    import {taskStore} from '../../store.js'

    export let taskList =[];

    $: completedTask = $taskStore.filter(t => t.completed).length

    function toggleCheck(e,id) {
        let tempTask=[...$taskStore]
        let index=tempTask.findIndex(t=> t.id == id)
        tempTask[index].completed= e.target.checked
        taskStore.set(tempTask)
    }

    function dblhandler(id) {
        let tempTask=[...$taskStore]
        let index=tempTask.findIndex(t=> t.id == id)
        tempTask[index].editable= true
        taskStore.set(tempTask)
        
    }
    function dblUpdater(e,id) {
        if (e.key=='Enter' && e.target.value) {
            let tempTask=[...$taskStore]
            let index=tempTask.findIndex(t=> t.id == id)
            tempTask[index].title= e.target.value
            tempTask[index].editable= false
            taskStore.set(tempTask)
        
        }
    }
    

</script>

<style>
    .complitedTask{
        text-decoration: line-through;
    }
</style>


<div class="my-4 p-4 flex flex-col border border-black rounded-[15px] items-center shadow-2xl w-max" >
  <h1 class="font-bold mb-1"><span class="text-green-600 font-bold">Task</span> List</h1>
 <div class="h-[5px] w-[200px] bg-green-600 rounded-full" ></div>
 <p class="text-sm m-2">Total Task: {$taskStore.length} Activated Task: {$taskStore.length-completedTask} Completed: {completedTask}</p>
 
 {#if taskList.length == 0}
    <p>
        There is no Task
    </p>
    {:else}
     <ul class="">
        {#each taskList as task }
            <li class="flex flex-col outline-gray-500 p-2 m-2 bg-green-100 rounded-[10px]"
             on:dblclick={e => dblhandler(task.id)}>
                <div class="">
                    <input type="checkbox" checked={task.completed} on:change={e=>toggleCheck(e,task.id)}>
                    <label for="" class="text-sm"> {task.completed?"Done!!!" : "Not Done Yet"}</label>
                </div>
                <input type="text" class="{task.completed ? "complitedTask font-light text-lg": "font-semibold text-lg"} " bind:value ={task.title} disabled={!task.editable} on:keypress={e=> dblUpdater(e,task.id)} >
                <input type="text" class="min-h-10 bg-orange-100 rounded-[10px] p-2" bind:value ={task.description} disabled={!taskList.editable} >
                <div class="w-full rounded-full h-1" style="background-color: {task.color};"></div>
            </li>
        {/each}
     </ul>
 {/if}
</div>