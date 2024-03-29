<script>

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

</script>

<div class="container">
    <img class="img" src={imgsrc} alt="">
    <h1 class:colorChangeColor={colorChange}>1. Class connection between svelte, css and javascript</h1>

    <h1 style="color: red;">2. Greeting and Reactivity:</h1>
    <p>{greeting}</p>

    <button on:click={ageIncrease}>Age Increase</button>

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
        color: brown;
    }
    
    </style>