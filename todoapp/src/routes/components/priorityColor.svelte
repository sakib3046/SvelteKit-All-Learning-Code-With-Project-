<script>
    let colors=['orange','red','yellow','green','blue'];
    export let selectedColor='';

    function changeColor(color) {
        selectedColor=color
    }

</script>

<style>
    .selected{
        border: 2px solid black;
    }
</style>

<div class="flex flex-row">
    {#each colors as color }
        <div on:click={()=>changeColor(color)} class=" {selectedColor==color?'selected':''} color m-2 h-[25px] w-[25px] rounded-lg" style="background:{color}"></div>
    {/each}

</div>