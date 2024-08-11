<script>
    import {goto,beforeNavigate,afterNavigate} from '$app/navigation'
    const handleClick=()=>{
        console.log('Going to Prodect page')
        goto('/products')
    }
    beforeNavigate((navigation)=>{
        console.log({before:navigation});
    });
    afterNavigate((navigation)=>{
        console.log({after:navigation});
    });

</script>
<h1>Welcome To Home Route</h1>



<button on:click={handleClick} >All Products</button>