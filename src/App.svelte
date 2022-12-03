<script>
  import svelteLogo from './assets/svelte.svg'
  import Counter from './lib/Counter.svelte'
  import Recette from './lib/Recette.svelte'
  import item from './data/cuisine.json'
  import fruitLogo from './assets/fruit.png'

 let hasData = item.length>0;
</script>
<header>
  <h1>
    <div>
      <img src={fruitLogo} class="fruit svelte" alt="Fruit Logo" />
    </div>
    
  </h1>

</header>
<main>

  <!-- <div>
    <a href="https://vitejs.dev" target="_blank" rel="noreferrer"> 
      <img src="/vite.svg" class="logo" alt="Vite Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank" rel="noreferrer"> 
      <img src={fruitLogo} class="logo svelte" alt="Svelte Logo" />
    </a>
    <img src={item[0].url} class="logo svelte" alt="Svelte Logo" />

  </div> -->
  <h1>Site de cuisine</h1>
  <div>


  </div>
  <div class="card">
    <Counter />
  </div>
  <!-- {#if hasData}
    sqdsqddsqdqsd
  {/if}
  <div class="container">
    <ul>
  {#each item as {id,url,name} ,i}
    <li class:align-right="{i%3 !== 0}"><img src={url} class="logo " alt="Svelte Logo" /></li>

  {/each}
    </ul>
  </div> -->

  <div class="grid">
  {#each  Object.values(item) as d}
  <div class="grid-item">
  <Recette {d}/>
</div>
{/each}
</div>
</main>

<style>

.grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
		grid-gap: 0.8rem;
	}

</style>
