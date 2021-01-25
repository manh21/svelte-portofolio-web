<script>
    import { onMount, onDestroy, createEventDispatcher } from "svelte";
    import projects from "./data/projects.js";

    export let onClose;
    export let event;
    let modal;
    
    onMount(() => {
        // animate = true;
    });

    function getImages(id){
        return projects.find((d) => {return d["id"] == id}).image
    }
</script>

<div 
 on:click={onClose}
 id="popup-bg"
 class="fixed z-40 top-0 left-0 bg-gray-500 w-full h-full bg-opacity-80"
></div>

<!-- class="fixed mt-10 p-2 z-50 bg-white md:w-6/12 h-full w-full top-0 md:left-1/4 sm:left-0" -->
<div 
 role="dialog"
 aria-modal="true"
 id="popup"
 class="modal"
 bind:this={modal}
>
    {#each getImages(event) as image}
        <img src="{image}" alt="preview"/>
    {/each}
</div>


<style>
    #popup-bg{
        position: fixed;
		top: 0;
		left: 0;
		width: 100%;
        height: 100%;
        overflow: hidden;
        background-color: rgba(0,0,0,0.8);
        background-image: url("data:image/svg+xml,%3Csvg width='40' height='40' viewBox='0 0 40 40' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23ffffff' fill-opacity='0.28' fill-rule='evenodd'%3E%3Cpath d='M0 40L40 0H20L0 20M40 40V20L20 40'/%3E%3C/g%3E%3C/svg%3E");
    }
    .modal {
		position: fixed;
		left: 50%;
		top: 50%;
		width: calc(100vw - 3em);
		max-width: 35em;
		max-height: calc(100vh - 3em);
        overflow: auto;
        z-index: 999;
		transform: translate(-50%,-50%);
		padding: 1em;
		border-radius: 0.2em;
		background: white;
	}
</style>