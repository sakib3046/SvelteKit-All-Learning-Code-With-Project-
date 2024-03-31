<script>
  import DispathedButton from "./dispathedButton.svelte";
  import Nasted from "./nasted.svelte";
  import Post from "./post.svelte";

  let imgsrc = "src/assets/user.png";
  let colorChange = true;

  setInterval(() => {
    colorChange = !colorChange;
  }, 1000);

  let name = "Sakib";
  let age = 21;
  $: greeting = `Hello My Name is ${name} & My age is ${age}`;

  function ageIncrease() {
    age = age + 1;
    console.log(age);
  }

  let lang = ["c", "c++", "java", "php"];
  let selectedLang;
  let selectedLangarray=[];
  let optionBindingValue=[];

  setTimeout(() => {
    lang = [...lang, "Javascript"];
  }, 3000);

  let ifelseNumber = "";

  let cheack = true;


  let showNasted=false;


</script>

<div class="container">
  <!-- .Page........................................................Page.......................Page......... -->
  <img class="img" src={imgsrc} alt="" />
  <h1 class:colorChangeColor={colorChange}>
    1. Class connection between svelte, css and javascript
  </h1>

  <!-- .Page........................................................Page.......................Page......... -->

  <h1 style="color: red;">2. Greeting and Reactivity:</h1>
  <p>{greeting}</p>

  <button on:click={ageIncrease}>Age Increase</button>

  <!-- .Page........................................................Page.......................Page......... -->

  <h1 style="color: red;">3. Array listing with each loop:</h1>

  <ul>
    {#each lang as item}
      <li>{item}</li>
    {/each}
  </ul>

  <!-- .Page........................................................Page.......................Page......... -->
  <h1 style="color: red;">4. If else:</h1>

  <h1>{(ifelseNumber = -5)} is a:</h1>
  {#if ifelseNumber > 0}
    <h2>'Positive'</h2>
  {:else if ifelseNumber < 0}
    <h2>'Negative'</h2>
  {:else}
    <h2>'zero'</h2>
  {/if}

  <!-- .Page........................................................................................Page............Page. -->

  <h1 style="color: red;">5. Component event and event dispatching</h1>

  <DispathedButton
    on:done={(e) => console.log(e.detail.currentNumber, e.timeStamp)}
  />

  <!-- .Page.......Page........Page.Page..........Page....Page.Page.Page.................Page.Page..Page.....Page. -->

  <h1 style="color: red;">6. Input Binding</h1>

  <h2>Hello I am {name}. And I {cheack ? "" : "do not "}love You!!!</h2>
  <input type="text" bind:value={name} />
  <h2>Did you love?</h2>
  <input type="checkbox" bind:checked={cheack} />

  <!-- .Page................Page.Page....................................Page.Page............................... -->

  <h1 style="color: red;">7. Input Binding Groups</h1>
  <h2>You have selected: {selectedLang || "nothing"}</h2>

  {#each lang as language}
    <input type="radio" bind:group={selectedLang} value={language} id="" />
    {language}
  {/each}

  <h2>You have selected: {selectedLangarray.length ? selectedLangarray.join(", ") : "nothing"}</h2>

  {#each lang as language}
    <input type="checkbox" bind:group={selectedLangarray} value={language} id="" />
    {language}
  {/each}
<hr>
  <h2>You have selected : {optionBindingValue.length ? optionBindingValue.join(', ') :'Nothing' }</h2>
  <select multiple bind:value={optionBindingValue} name="" id="">
    {#each lang as language}
        <option value={language}>{language}</option>
    {/each}
  </select>


  <!-- .Page...............................Page.Page...Page.........................Page.Page.Page.... -->

  <h1 style="color: red;">8. Lifecycle Function</h1>
  
  {#if showNasted}
  <Nasted/>  
  {/if}
  

  <button on:click={()=>{showNasted=!showNasted}}>Toggle</button>


  <!-- .Page...............................Page.Page...Page.........................Page.Page.Page.... -->


  <h1 style="color: red;">9. Slot</h1>

  <Post>
    This is a slot example
  </Post>





</div>














<style>
  .container {
    margin: 10px;
    padding: 10px;
  }

  .img {
    width: 150px;
  }

  .colorChangeColor {
    color: green;
  }
</style>
