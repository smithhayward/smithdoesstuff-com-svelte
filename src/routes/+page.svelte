<script>

    import { writable } from 'svelte/store';
    
    import { fade, slide, fly } from 'svelte/transition';
    
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

    <div class="flex flex-col mx-auto my-auto sm:flex-row">
    <div class="flex flex-col my-auto mx-auto sm:min-w-[560px]">
        <div class="text-5xl">Smith Hayward</div>
    
        <div class=" h-10 text-3xl italic">{$heroString}</div>

    </div>

<div class="flex flex-col my-6 sm:my-auto ">
    <a href="/resume.pdf" class=" text-white my-2 text-center min-w-80 mx-auto p-2 px-4 rounded-xl bg-teal-600 border-2 hover:bg-teal-500 hover:border-2 hover:border-teal-900 hover:my-2 hover:text-[1.1em] hover:font-bold hover:text-black transition-all duration-300 " >
        <button class="">
            Download Resume</button></a>
    <a href="#experience" class=" text-white my-2 text-center min-w-80 mx-auto p-2 px-4 rounded-xl bg-teal-600 border-2 hover:bg-teal-500 hover:border-2 hover:border-teal-900 hover:my-2 hover:text-[1.1em] hover:font-bold hover:text-black transition-all duration-300 " >
        <button class="">
            Job Experience Walkthrough</button></a>
    <a href="#consulting" class=" text-white my-2 text-center min-w-80 mx-auto p-2 px-4 rounded-xl bg-teal-600 border-2 hover:bg-teal-500 hover:border-2 hover:border-teal-900 hover:my-2 hover:text-[1.1em] hover:font-bold hover:text-black transition-all duration-300 " >
        <button class="">
            Consulting Services</button></a>
</div>
</div>
</div>

<div id="experience" class="flex flex-col h-svh justify-center bg-slate-400">


</div>

<div id="consulting" class="flex flex-col h-svh justify-center bg-slate-200">


</div>

<style>

	@import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200..1000;1,200..1000&display=swap');

	*{ font-family: Nunito, Helvetica, sans-serif;}

div {
    border: 1px solid pink;
}
</style>