
<script lang="ts">

  import { onMount } from 'svelte';
  import { goto } from '$app/navigation';

  type tile = {
    round: string;
    value: string;
    dailyDouble: string;
    category: string;
    answer: string;
    question: string;
    solved: boolean;
  };
 

  let gameData:tile[] = [];
  let loading = true;
  let error = false
  let counter = 0;
  let currCat = 0;
  let solved = []
  let cat1 = 31;
  let cat2 = 36;
  let cat3 = 41;
  let cat4 = 46;
  let cat5 = 51;
  let cat6 = 56;

  function changeCat(currCat){
    console.log("i was pushed" + currCat)
    currCat += 5

  }
  function showQuestion(num, i) {
      num = num+i;
      let quest = gameData[num].question;
      let dd = gameData[num].dailyDouble; 
      let ans = gameData[num].answer; 

      gameData[num].solved = true
      localStorage.setItem('DD', dd)
      localStorage.setItem('question', quest)
      localStorage.setItem('ans', ans)


      
     goto('/answer');

    
  }



  onMount(() => { // Everything goes on at the same time
  getData()

  

async function getData() {
  // const response = await fetch('testdata.csv');
  try{
  const response = await fetch('entries.tsv');
  const data = await response.text();

  const table = data.split('\n').slice(1);
  table.forEach(row => {
    const cols = row.split("\t");
    const round = cols[1];
    const value = cols[2];
    const dailyDouble = cols[3];
    const category = cols[4];
    const answer = cols[5];
    const question = cols[6];
    const solved = false;
    

    gameData.push({ round, value, dailyDouble, category, answer, question, solved });
  });

  console.log('Game Data:', gameData);
      loading = false;
    } catch (err) {
      error = true;
      console.error("Error fetching data:", err);
}
}
  })
  
 </script>

<body></body>
{#if loading}
  <p>Loading...</p>
{:else if error}
  <p>Error: {error}</p>
{:else}
<div class="category1">
  <p> {gameData[cat1].category}</p>
  <button on:click={() => changeCat(cat1)} style="width: 200px; height: 50px;" > Change Category (Exprimental) </button>
</div>
<div class="category2">
  <p> {gameData[cat2].category}</p>
  <button on:click={() => changeCat(cat2)} style="width: 200px; height: 50px;" > Change Category (Exprimental) </button>
</div>
<div class="category3">
  <p> {gameData[cat3].category}</p>
  <button on:click={() => changeCat(cat3)} style="width: 200px; height: 50px;" > Change Category (Exprimental) </button>
</div>
<div class="category4">
  <p> {gameData[cat4].category}</p>
  <button on:click={() => changeCat(cat4)} style="width: 200px; height: 50px;" > Change Category (Exprimental) </button>
</div>
<div class="category5">
  <p> {gameData[cat5].category}</p>
  <button on:click={() => changeCat(cat5)} style="width: 200px; height: 50px;" > Change Category (Exprimental) </button>
</div>
<div class="category6">
  <p> {gameData[cat6].category}</p>
  <button on:click={() => changeCat(cat6)} style="width: 200px; height: 50px;" > Change Category (Exprimental) </button>
</div>

<div class= "cat1">
  <button on:click={() => showQuestion(cat1,0)} style="width: 300px; height: 140px;" id="cat11" >A</button>
  <button on:click={() => showQuestion(cat1,1)} style="width: 300px; height: 140px;" id="cat2" >B</button>
  <button on:click={() => showQuestion(cat1,2)} style="width: 300px; height: 140px;" id="cat3">C</button>
  <button on:click={() => showQuestion(cat1,3)} style="width: 300px; height: 140px;" id="cat4" >D</button>
  <button on:click={() => showQuestion(cat1,4)} style="width: 300px; height: 140px;"id="cat5" >E</button>
</div>
<div class= "cat2">
  <button on:click={() => showQuestion(cat2,0)} style="width: 300px; height: 140px;" id="cat11" >A</button>
  <button on:click={() => showQuestion(cat2,1)} style="width: 300px; height: 140px;" id="cat2" >B</button>
  <button on:click={() => showQuestion(cat2,2)} style="width: 300px; height: 140px;" id="cat3">C</button>
  <button on:click={() => showQuestion(cat2,3)} style="width: 300px; height: 140px;" id="cat4" >D</button>
  <button on:click={() => showQuestion(cat2,4)} style="width: 300px; height: 140px;"id="cat5" >E</button>
</div>
<div class= "cat3">
  <button on:click={() => showQuestion(cat3,0)} style="width: 300px; height: 140px;" id="cat11" >A</button>
  <button on:click={() => showQuestion(cat3,1)} style="width: 300px; height: 140px;" id="cat2" >B</button>
  <button on:click={() => showQuestion(cat3,2)} style="width: 300px; height: 140px;" id="cat3">C</button>
  <button on:click={() => showQuestion(cat3,3)} style="width: 300px; height: 140px;" id="cat4" >D</button>
  <button on:click={() => showQuestion(cat3,4)} style="width: 300px; height: 140px;"id="cat5" >E</button>
</div><div class= "cat4">
  <button on:click={() => showQuestion(cat4,0)} style="width: 300px; height: 140px;" id="cat11" >A</button>
  <button on:click={() => showQuestion(cat4,1)} style="width: 300px; height: 140px;" id="cat2" >B</button>
  <button on:click={() => showQuestion(cat4,2)} style="width: 300px; height: 140px;" id="cat3">C</button>
  <button on:click={() => showQuestion(cat4,3)} style="width: 300px; height: 140px;" id="cat4" >D</button>
  <button on:click={() => showQuestion(cat4,4)} style="width: 300px; height: 140px;"id="cat5" >E</button>
</div><div class= "cat5">
  <button on:click={() => showQuestion(cat5,0)} style="width: 300px; height: 140px;" id="cat11" >A</button>
  <button on:click={() => showQuestion(cat5,1)} style="width: 300px; height: 140px;" id="cat2" >B</button>
  <button on:click={() => showQuestion(cat5,2)} style="width: 300px; height: 140px;" id="cat3">C</button>
  <button on:click={() => showQuestion(cat5,3)} style="width: 300px; height: 140px;" id="cat4" >D</button>
  <button on:click={() => showQuestion(cat5,4)} style="width: 300px; height: 140px;"id="cat5" >E</button>
</div><div class= "cat6">
  <button on:click={() => showQuestion(cat6,0)} style="width: 300px; height: 140px;" id="cat11" >A</button>
  <button on:click={() => showQuestion(cat6,1)} style="width: 300px; height: 140px;" id="cat2" >B</button>
  <button on:click={() => showQuestion(cat6,2)} style="width: 300px; height: 140px;" id="cat3">C</button>
  <button on:click={() => showQuestion(cat6,3)} style="width: 300px; height: 140px;" id="cat4" >D</button>
  <button on:click={() => showQuestion(cat6,4)} style="width: 300px; height: 140px;"id="cat5" >E</button>
</div>


{/if}


  
  <style>
  @font-face {
    font-family: 'font';
    src: url('Korina.ttf');
  }


   
    .cat1 {
    position: absolute;
    opacity: 0%;
    top: 28%;
    left: 5.5%;
    width: 200px;
    height: 200px; 
    transform: translate(-50%, -50%);
    }

    .cat2 {
    position: absolute;
    opacity: 0%;
    top: 28%;
    left: 22.5%;
    width: 200px;
    height: 200px; 
    transform: translate(-50%, -50%);
    }
    .cat3 {
    position: absolute;
    opacity: 0%;
    top: 28%;
    left: 38.5%;
    width: 200px;
    height: 200px; 
    transform: translate(-50%, -50%);
    }

    .cat4 {
    position: absolute;
    opacity: 0%;
    top: 28%;
    left: 55.5%;
    width: 200px;
    height: 200px; 
    transform: translate(-50%, -50%);
    }
    .cat5 {
    position: absolute;
    opacity: 0%;
    top: 28%;
    left: 72.5%;
    width: 200px;
    height: 200px; 
    transform: translate(-50%, -50%);
    }
    .cat6 {
    position: absolute;
    opacity: 0%;
    top: 28%;
    left: 88.5%;
    width: 200px;
    height: 200px; 
    transform: translate(-50%, -50%);
    }



    

   #cat11{
    position: relative;

   }

   #cat2{
    position: relative;
    top: 3%;

  }


  #cat3{
    position: relative;
    top: 8%;
    
  }


  #cat4{
    position: relative;
    top: 15%;
    
  }

  #cat5{
    position: relative;
    top: 20%;
    
  }




  .category1, .category2, .category3, .category4, .category5, .category6 {
    color: white;
    font-family: 'font';
    text-shadow: 5px 3px #000000;
    font-size: 1rem;
    position: absolute;
    top: 9%;
    transform: translate(-50%, -50%);
  }





  .category1 {
    left: 8%;
  }

  .category2 {
    left: 25%;
  }

  .category3 {
    left: 41.5%;
  }

  .category4 {
    left: 58%;
  }

  .category5 {
    left: 75%;
  }

  .category6 {
    left: 90%;
  }

   
  body {
      position: relative;
      height: 100vh;
      margin: 0;
      display: flex;
      background: url('board.jpg') no-repeat center center fixed;
      background-size: 100% 100%;
    }

  </style>
