<script> 
  import { onMount } from 'svelte';
  import { goto } from '$app/navigation';
  
  let answer = " "
  let dailyDouble = localStorage.getItem('DD')
  answer = localStorage.getItem('ans')

  function goBack(){
    goto('/');
  }
  function showQuestion(){
    goto('/question');
  }
 // document.getElementById('question').textContent = question
 // document.getElementById('DD').textContent = dailyDouble
 

</script>
<body> </body>

  <div class="answer">
    <p> {answer.toUpperCase()} </p>
    <button on:click={() => goBack()} style="width: 100; height: 50px;" > Go Back </button>
    <button on:click={() => showQuestion()} style="width: 100; height: 50px;" > Show Question </button>
  </div>  

<style>

.answer{
    color: white;
    text-shadow: 12px 5px #000000;
    font-family: 'font';
    font-size: 7rem;
    align-items: center;
    text-align: center;
    position: absolute;
    margin: auto;
    top: 18%;
    left:  3%;
    
}
body {
  position: relative;
  height: 100vh;
  margin: 0;
  display: flex;
  background-color: #0a3b99;
  background-size: 100% 100%;
}
</style>