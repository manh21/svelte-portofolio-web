<script>
    import projects from "./data/projects.js";
    import { onMount } from "svelte";
    import MyModal from "./MyModal.svelte";
    
    let currentID;
    let showModal;

    onMount(() => {
        console.log("Start Projetcs")
    });

    function coverClick(id) {
        currentID = id;
        showModal = true;
        console.log(id);
    }

</script>

<div class="mx-auto max-w-screen-lg mb-5 overflow-hidden">
    <div class="grid w-full md:grid-cols-3 sm:grid-cols-1 gap-5">
    {#each projects as p}

        <div on:click={() => coverClick(p.id)} class="bg-gray-200 rounded shadow-md overflow-hidden">
            <div class="relative h-40 overflow-hidden">
                <div class="absolute w-full h-full bg-opacity-0 cursor-pointer hover:bg-black hover:bg-opacity-50">
                    <div class="h-full opacity-0 hover:opacity-100">
                        <svg class="mx-auto block h-full" width="64px" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="white">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM10 7v3m0 0v3m0-3h3m-3 0H7" />
                        </svg>
                    </div>
                </div>
                <img class="w-full" src="{p.image[0]}" alt="{p.name} cover">
            </div>
            <div class="p-5">
                <h2 class="text-xl font-semibold">{p.name}</h2>
                <p class="">{p.description}</p>
                <div class="mt-2">
                {#if p.link != ''}
                    <a class="text-sm inline-block p-2 rounded no-underline bg-green-600 text-white hover:no-underline" href="{p.link}" target="_blank">Website</a>
                {/if}
                
                {#if p.source != ''}
                    <a class="text-sm inline-block p-2 rounded no-underline bg-blue-600 text-white hover:no-underline" href="{p.source}" target="_blank">Source Code</a>
                {:else}
                    <a class="text-sm inline-block p-2 rounded no-underline bg-red-600 text-white cursor-not-allowed hover:no-underline" href="/">Private Source</a>
                {/if}
                </div>
            </div>
        </div>
        
    {/each}
    </div>
</div>

{#if currentID && showModal}
<svelte:component this={MyModal} event={currentID} onClose={() => showModal = false}/>
{/if}

<style>

</style>