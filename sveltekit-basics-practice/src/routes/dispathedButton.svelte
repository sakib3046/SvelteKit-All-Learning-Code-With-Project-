<script>
    import {createEventDispatcher} from "svelte";
    const disPatch= createEventDispatcher();
    let num=0;
    function handleDone() {
        disPatch("done",{
            currentNumber: num,
        });
    }
</script>
<button on:click={()=>{num += 1}}>After Increase the number is {num}</button>
<button on:click={handleDone}>Done!!!</button>