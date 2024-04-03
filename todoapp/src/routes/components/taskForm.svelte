<script>
    import Button from "./button.svelte";
    import PriorityColor from "./priorityColor.svelte";
    import {createEventDispatcher} from 'svelte';
    let title='';
    let description='';
    let color='';
    const dispatch = createEventDispatcher();

    function submitHandler(e){
        if (!title) {
               alert('Enter your task title')
        }
        let id=(Math.random()* new Date().getTime()).toString()

        let task={
            id,
            title,
            description,
            color,
            completed:false,
            editable:false
        }
        dispatch('createTask',task)
        e.target.reset();
        color='';

    }

</script>




<div class="my-4 p-4 flex flex-col border border-black rounded-[15px] items-center shadow-2xl w-max">
    <form action="" on:submit|preventDefault={submitHandler} class=" flex flex-col items-center">

        <h1 class="text-3xl font-bold">ToDo <span class="text-green-600">App</span></h1>
        <h1 class="my-5 text-xl font-semibold ">Enter your tasks</h1>
        <div class="flex flex-col">
            <label for="title" class="py-1"> Enter your task title:</label>
            <input bind:value={title} type="text" placeholder="Task title" class="bg-green-100 px-4 shadow-xl py-2 rounded-[10px] focus:bg-white focus:outline-green-600">
        </div>
    
        <div class="flex flex-col my-4">
            <label for="title" class="py-1"> Enter your task Description:</label>
            <textarea bind:value={description} name="" placeholder="Enter the task description" id="" class=" shadow-xl bg-green-100 px-4 py-2 rounded-[10px] focus:bg-white focus:outline-green-600"></textarea>
        </div>
    
    
        <PriorityColor bind:selectedColor={color}/>
        <Button/>
    </form>
   
    
</div>