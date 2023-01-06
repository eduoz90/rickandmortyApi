<script>
 import Character from'./libs/Characters.svelte';
 //creamos un array para guardar los datos del json
 let characters = [];
 let page = 1;
 

 //Es una función que me devuelve los datos de la api en formato json.
 async function Loadcharacter() {
    const response = await fetch("https://rickandmortyapi.com/api/character?page=" + page);
    const data = await response.json();
    characters = data.results;
  }

  //Llamada de la función.
  Loadcharacter();


  function previusPage(){
    page--;
    Loadcharacter()
  }

  function nextPage(){
    page++;
    Loadcharacter()
  }
</script>

<h1 class="titulo">Rick and Morty Api</h1>


<div class="btn">
  <button class="btn1" on:click={previusPage} disabled={page ===1}>Previus</button>
  <button class="btn2" on:click={nextPage}>Next</button>
</div>


<div class="contenido">
  <div class="grid">
    {#each characters as character}

  <Character  {character}/>

  {/each}
  </div>
  
</div>
