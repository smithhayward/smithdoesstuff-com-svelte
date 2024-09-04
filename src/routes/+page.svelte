<script>

    import { writable } from 'svelte/store';
    import {fade} from 'svelte/transition';
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


let mode = 'summary';
let bdr = false;

</script>


<div id="index" class="flex flex-col lg:flex-row h-svh bg-slate-200 overflow-hidden ">

    <div class="flex flex-col mx-auto my-auto lg:flex-row ">
    <div class="flex flex-col my-auto mx-auto lg:min-w-[530px]  border-slate-700 lg:bg-slate-50 lg:mx-16 lg:p-24 lg:shadow-2xl">
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
        <!-- <a href="#skills" class=" shadow-lg shadow-slate-700 text-white my-2 text-center min-w-80 mx-auto p-2 px-4 rounded-xl bg-teal-600 border-2 hover:bg-teal-500 hover:border-2 hover:border-teal-900 hover:my-2 hover:text-[1.08em] hover:font-bold hover:text-black transition-all duration-300 " >
            <button class="">
                Skills & Knowledge</button></a>
        <a href="#consulting" class=" shadow-lg shadow-slate-700 text-white my-2 text-center min-w-80 mx-auto p-2 px-4 rounded-xl bg-teal-600 border-2 hover:bg-teal-500 hover:border-2 hover:border-teal-900 hover:my-2 hover:text-[1.08em] hover:font-bold hover:text-black transition-all duration-300 " >
            <button class="">
                Consulting Services</button></a> -->

    </div>
</div>
</div>


{#each jobFile as job, i}
<div transition:fade  id="experience{i}" class="flex flex-col h-svh lg:max-w-[1024px] lg:mx-auto bg-slate-300">
        <div class="w-full text-end pr-4 mx-auto text-[0.85em] sm:text-[1em] lg:text-lg mt-8 ">{job.start} - {job.end}</div>
    <div class=" w-full text-center bg-slate-400 mx-auto text-xl lg:text-3xl font-bold">{job.title}</div>
        <div class=" w-full text-center bg-slate-200 mx-auto font-bold text-purple-800 text-lg lg:text-2xl">{job.company}</div>

    
    <div id="body{i}" class="flex flex-col mx-auto h-full max-h-[600px] overflow-auto lg:overflow-clip">

        {#if mode === 'summary'}
        <div id="summary{i}" class="flex flex-col mx-6 my-2 lg:px-12">
            {#each job.summary as sentence}
                <div class="my-0.5 lg:my-2 p-1 text-[.87em] md:text-lg">{sentence}</div>
            {/each}
        
        <div id="skills{i}" class="flex flex-wrap mt-1 p-2 text-[0.75em] lg:mt-12 lg:text-lg lg:px-3 bg-slate-400 rounded-2xl ">
            <div class="w-full font-bold ">Skills & Technologies Used</div>
            { #each job.skills as skill }
                <div class="bg-slate-200 px-2 mx-0.5 my-1 p-0.5 rounded-lg">{skill}</div>
            {/each}
        </div>


        </div>

        {:else if mode === 'resp'}

        <div class="mx-6 my-2 {bdr?"border border-slate-800":""} lg:px-12">
            {#each job.responsibilities as responsibility}
            {#if responsibility.content !== ''}
                <div class="my-0.5 p-1 text-[0.9em] md:text-lg lg:m-1 lg:p-1 lg:rounded-xl lg:flex ">
                    <div class="hidden lg:block pr-4 text-2xl">&#9874;</div>
                    {responsibility.content}

                </div>
            {/if}
            {/each}
        </div>

        {:else if mode === 'successes'}

        <div class="mx-6 my-2 {bdr?"border border-slate-800":""} lg:px-12">
            {#each job.successes as success}
            {#if success.content !== ''}
                <div class="my-0.5 p-1 text-[.87em] md:text-lg lg:text-lg lg:flex ">
                    <div class="hidden lg:block pr-4 text-2xl">&#10032;</div>
                    {success.content}
                </div>
            {/if}
            {/each}
        </div>

        {/if}

    </div>



<div class="flex flex-row m-2 p-2 justify-between  {bdr?"border border-slate-800":""} align-middle">

    <div class="flex flex-col space-y-2 mt-6 -ml-8 {bdr?"border border-red-800":""}">
    
        
            { #if i > 0 }
                <a
                    on:click={()=> { mode = 'summary';}}
                    href="#experience{i-1}"
                    class=" pl-12 pr-4 py-2 bg-teal-500 rounded-sm rounded-r-2xl">
                    Prior
                </a>
            
            {:else}
            <a 
                on:click={()=> { mode = 'summary';}} 
                href="#index" 
                class=" pl-12 pr-4 py-2 bg-teal-600 rounded-r-2xl ">
                Home
            </a>
            
            {/if}
            
        

        
            { #if i < jobFile.length-1 }
            <a 
                on:click={()=> { mode = 'summary';}}
                href="#experience{i+1}" class=" pl-12 pr-4 py-2 bg-teal-500 rounded-sm rounded-r-2xl ">
                Next
            </a>
            
            {:else}
            
            <!-- <a 
                href="#skills" 
                class="pl-12 pr-4 py-2 bg-teal-600 rounded-md ">
                Skills & Knowledge
                </a>
             -->
            {/if}
        
    </div>


    <div class="flex flex-col space-y-2 overflow-visible {bdr?"border border-slate-800":""}">
        <!-- <div class="text-xs {bdr?"border border-red-800":""} pb-0">PAGE SELECTOR</div> -->
        
            <button 
                on:click={()=> { mode = 'summary';}}
                class="{mode==='summary'?'text-bold bg-purple-800 text-white':'bg-slate-400'} py-1 px-5 italic rounded-3xl text-center">
            Summary</button>
        
        
            <button 
                on:click={()=> { mode = 'resp';}}
                class="{mode==='resp'?'text-bold bg-purple-800 text-white':'bg-slate-400'} py-1 px-5 italic rounded-3xl text-center">
            The Work</button>
        
        
            <button
                on:click={()=> { mode = 'successes';}}
                class="{mode==='successes'?'text-bold bg-purple-800 text-white':'bg-slate-400'} py-1 px-5 italic rounded-3xl text-center">
            Achivements</button>
        

    </div>
</div>


</div>
{/each}

<div id="consulting" class="flex flex-col h-svh justify-center bg-slate-200">


</div>

<style>

	@import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200..1000;1,200..1000&display=swap');

	*{ font-family: Nunito, Helvetica, sans-serif;}


</style>