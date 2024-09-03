<script>

    import { writable } from 'svelte/store';
    import jobFile from '$lib/jobs.json';
    
    $: heroString = writable("");

    setTimeout(()=> {
        $heroString = "Data Wrangler";
    }, 1500);

    setTimeout(()=> {
        $heroString = "Process Pragmatist";
    }, 3000);

    setTimeout(()=> {
        $heroString = "Business Analyst";
    }, 4500);

</script>


<div id="index" class="flex flex-col md:flex-row h-svh bg-slate-200">

    <div class="flex flex-col mx-auto my-auto sm:flex-row ">
    <div class="flex flex-col my-auto mx-auto sm:min-w-[530px] border-slate-700 md:bg-slate-50 md:mx-16 md:p-24 md:shadow-2xl">
        <div class="text-5xl">Smith Hayward</div>
    
        <div class=" h-10 text-3xl italic">{#key $heroString}<span>{$heroString}</span>{/key}</div>
    
    </div>

    <div class="flex flex-col my-6 sm:my-auto ">
        <!-- <a href="/resume.pdf" class="shadow-lg md:shadow-slate-700 text-white my-2 text-center min-w-80 mx-auto p-2 px-4 rounded-xl bg-teal-600 border-2 hover:bg-teal-500 hover:border-2 hover:border-teal-900 hover:my-2 hover:text-[1.1em] hover:font-bold hover:text-black transition-all duration-300 " >
            <button class="">
                Download Resume</button></a> -->
        <a href="#experience0" class=" shadow-lg shadow-slate-700 text-white my-2 text-center min-w-80 mx-auto p-2 px-4 rounded-xl bg-teal-600 border-2 hover:bg-teal-500 hover:border-2 hover:border-teal-900 hover:my-2 hover:text-[1.08em] hover:font-bold hover:text-black transition-all duration-300 " >
            <button class="">
                Job Experience Walkthrough</button></a>
        <a href="#skills" class=" shadow-lg shadow-slate-700 text-white my-2 text-center min-w-80 mx-auto p-2 px-4 rounded-xl bg-teal-600 border-2 hover:bg-teal-500 hover:border-2 hover:border-teal-900 hover:my-2 hover:text-[1.08em] hover:font-bold hover:text-black transition-all duration-300 " >
            <button class="">
                Skills & Knowledge</button></a>
        <a href="#consulting" class=" shadow-lg shadow-slate-700 text-white my-2 text-center min-w-80 mx-auto p-2 px-4 rounded-xl bg-teal-600 border-2 hover:bg-teal-500 hover:border-2 hover:border-teal-900 hover:my-2 hover:text-[1.08em] hover:font-bold hover:text-black transition-all duration-300 " >
            <button class="">
                Consulting Services</button></a>

    </div>
</div>
</div>


{#each jobFile as job, i}
<div id="experience{i}" class="flex flex-col h-svh justify-center bg-slate-300 border-slate-700">
    <div class="mx-auto mt-12">
        { #if i > 0 }<a href="#experience{i-1}" class="m-2 h-12 mx-4 p-4">Prior</a>
        
        {:else}
        <a href="#index" class="m-2 h-12 mx-4 p-4">Home</a>
        {/if}
    </div>
    <div class="mx-auto my-auto border-4 border-red-700">
        {job.title}
    </div>
    <div class="mx-auto mb-12">
        { #if i < jobFile.length-1 }<a href="#experience{i+1}" class="m-2 h-12 mx-4 p-4">Next</a>{/if}
    </div>
</div>
{/each}


<div id="consulting" class="flex flex-col h-svh justify-center bg-slate-200">


</div>

<style>

	@import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200..1000;1,200..1000&display=swap');

	*{ font-family: Nunito, Helvetica, sans-serif;}

div {
    border: 0px solid pink;
}
</style>