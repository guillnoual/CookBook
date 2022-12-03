<script>
	import {fade} from 'svelte/transition'
    import { Modal, Content, Trigger}  from "sv-popup"
	export let d;
	let click;
	let clicked = click ? true : false;	
 
    console.log(d.etapes);

</script>

<div class="image-wrapper">
    <Modal wrapper={false} basic={true} big={true} button={false}>
        <Content>
            
            <img class="m-image" loading="lazy" src={d.url} alt="random img"/>
      <h2 class="contentText">  
        <ul>
            Ingrédients : 
            {#each d.ingredrients as name, index}
                <li> - {name}</li>
            {/each}
            <br>
            Etapes :
            {#each d.etapes as etp, index}
                <li> - {etp}</li>
            {/each}
        </ul>
      </h2>
        </Content>
        <Trigger>
            <img class="m-image" loading="lazy" src={d.url} alt="random img"/>
      
        </Trigger>
      </Modal>
</div>
<!-- <div class="image-wrapper">
<img class="image" loading="lazy" on:click={()=>{
	clicked = !clicked;
}} src={d.url} crossorigin="anonymous" alt="random img"/>
</div>
{#if clicked}
<div class="modal" transition:fade={{duration: 100}}>
	<div on:click={()=>{clicked = !clicked}} class="close">
		x
	</div>
	
	<div class="modal-image">
		<img class="m-image" loading="lazy" src={d.url} alt="random img"/>
	</div>
</div>
{/if} -->
<style>
    html{
        color:red;
    }
	img:before {
background:black;
	}
	.m-image{

		width:100%;
		height:auto;
		max-height:500px;
		object-fit: scale-down;
	}
	.close {
		cursor: pointer;
		font-size: 3rem;
		position: absolute;
		right: 0;
		color: red;
		margin-right:1.5rem;
		top:0;
	}
	.image {
		cursor: pointer;
		width:100%;
		max-width:400px;
		max-height:400px;
  	transition: 0.125s;
	}
	
	.image:hover {
		opacity: 0.7;
	}
	
	img:active {
		opacity: 0.5;
	}
	
	.modal-image {
	  margin: auto;
  	display: block;
  	width: 80%;
  	max-width: 100%;	
	}
	.modal {
  	position: fixed;
		z-index: 2;
  	padding-top: 100px;
  	left: 0;
  	top: 0;
  	width: 100%;
  	height: 100%;
  	overflow: auto;
  	background-color: rgb(0,0,0);
  	background-color: rgba(0,0,0,0.9);
	}

    .contentText {
		color: #bb72f1
	}
</style>