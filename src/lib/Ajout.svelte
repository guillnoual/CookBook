<script>
   
    import { Modal, Content, Trigger}  from "sv-popup"
    import item from './../data/cuisine.json'
    export let answer;
    let files;


    $: if (files) {
		// Note that `files` is of type `FileList`, not an Array:
		// https://developer.mozilla.org/en-US/docs/Web/API/FileList
		console.log(files);

		for (const file of files) {
			console.log(`${file.name}: ${file.size} bytes`);
		}
	}
    $:console.log("zeazaez");
    $:console.log({files});
    $:console.log("bbb");
    let valueIngredient = `oeuf`;
    let valueRecette = `Some words are *italic*, some are **bold**`;
    
    let  avatar, fileinput;
	
	const onFileSelected =(e)=>{
  let image = e.target.files[0];
            let reader = new FileReader();
            reader.readAsDataURL(image);
            reader.onload = e => {
                 avatar = e.target.result
            };
}
	function validate() {
		console.log("I'm the qsdsqd function");
        console.log({avatar});
	}


  </script>
<div id="app">
      <Modal basic big={true}>
        <Content>

            <h1>Upload Image</h1>
  
        {#if avatar}
        <img class="avatar" src="{avatar}" alt="d" />
        {:else}
        <img class="avatar" src="https://cdn4.iconfinder.com/data/icons/small-n-flat/24/user-alt-512.png" alt="" /> 
        {/if}
				<img class="upload" src="https://static.thenounproject.com/png/625182-200.png" alt="" on:click={()=>{fileinput.click();}} />
        <div class="chan" on:click={()=>{fileinput.click();}}>Choose Image</div>


        <label for="avatar">Upload a picture:</label>
        <input
        accept="image/png, image/jpeg"
        bind:files
        id="avatar"
        name="avatar"
        type="file"
        />



        <input style="display:none" type="file" accept=".jpg, .jpeg, .png" on:change={(e)=>onFileSelected(e)} bind:this={fileinput} >


            <div class="contentText">
                <h2>Ecrivez les ingrédients de la recette</h2>
                <textarea  bind:value={valueIngredient}></textarea>
                <h2>Ecrivez les étapes de la recette</h2>
                    <textarea  bind:value={valueRecette}></textarea>
                <form on:submit|preventDefault={validate}>
                    <button type="submit">
                        Sauvegarder
                    </button>
                </form>
            </div>

            {#if files}
	<h2>Selected files:</h2>
	{#each Array.from(files) as file}
		<p>{file.name} ({file.size} bytes) </p>
	{/each}
{/if}
        </Content>
        <Trigger>
            <button>
                Ajout
            </button>
      
        </Trigger>
      </Modal>

    </div>
  
  <style>
    textarea { width: 100%; height: 200px; }
    .contentText {
		color: #bb72f1
	}
    #app{
	display:flex;
		align-items:center;
		justify-content:center;
		flex-flow:column;
}
 
	.upload{
		display:flex;
	height:50px;
		width:50px;
		cursor:pointer;
	}
	.avatar{
		display:flex;
		height:200px;
		width:200px;
	}
  </style>