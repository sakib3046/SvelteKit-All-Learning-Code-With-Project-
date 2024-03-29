<script>
  import DispathedButton from "./dispathedButton.svelte";


    let imgsrc= "src/assets/user.png";
    let colorChange=true;

    setInterval(() => {
        colorChange=!colorChange;
    }, 1000);

    let name= 'Sakib'
    let age=21
    $: greeting=`Hello My Name is ${name} & My age is ${age}`

    function ageIncrease() {
        age= age+1;
        console.log(age)
    }

    let lang=['c','c++','java','php'
    ]

    setTimeout(() => {
        lang= [...lang,'Javascript']
    }, 3000);


    let ifelseNumber=''

</script>

<div class="container">
    <img class="img" src={imgsrc} alt="">
    <h1 class:colorChangeColor={colorChange}>1. Class connection between svelte, css and javascript</h1>

    <h1 style="color: red;">2. Greeting and Reactivity:</h1>
    <p>{greeting}</p>

    <button on:click={ageIncrease}>Age Increase</button>

    <h1 style="color: red;">3. Array listing with each loop:</h1>

    <ul>
        {#each lang as item }
            <li>{item}</li>                
        {/each}
    
    </ul>

    <h1 style="color: red;">4. If else:</h1>

    <h1> {ifelseNumber=-5} is a: </h1>
        {#if  ifelseNumber>0}
            <h2>'Positive'</h2>
        {:else if ifelseNumber<0}
            <h2>'Negative'</h2>
        {:else}
            <h2>'zero'</h2>            
        {/if}

        <h1 style="color: red;">5, Component event and event dispatching</h1>

        <DispathedButton on:done={(e)=>console.log(e.detail.currentNumber , e.timeStamp)} />
</div>




<style>
    .container{
        margin: 10px;
        padding: 10px;
    }

    .img{
        width: 150px;
    }
    
    .colorChangeColor{
        color: green;
    }
    
    </style>