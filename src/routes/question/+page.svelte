<script> 
  import { onMount } from 'svelte';
  import { goto } from '$app/navigation';
  
  let question = " "
  let dailyDouble = localStorage.getItem('DD')
  question = localStorage.getItem('question')

  function goBack(){
    goto('/');
  }

  function showAnswer(){
    goto('/answer');
  }

  
 // document.getElementById('question').textContent = question
 // document.getElementById('DD').textContent = dailyDouble
 

</script>
<body> </body>

  <div class="question">
    <p> {question.toUpperCase()} </p>
    <button on:click={() => goBack()} style="width: 100; height: 50px;" > go back </button>
    <button on:click={() => showAnswer()} style="width: 100; height: 50px;" > Show Answer</button>
  </div>  

<style>

.question{
    color: white;
    text-shadow: 12px 5px #000000;
    font-family: 'font';
    font-size: 10rem;
    text-align: center;
    position: absolute;
    margin: auto;
    justify-content: center;
    top: 35%;
    left: 25%
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