<script>
    import{goto} from '$app/navigation';
    const onclick=()=>{
        goto('/')
    }
</script>
<header><button on:click={onclick}>MD SAKIB HASAN</button></header>
<slot/>