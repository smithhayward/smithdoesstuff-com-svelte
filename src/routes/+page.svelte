<script>

    import { writable } from 'svelte/store';
    
    import { fade, slide, fly } from 'svelte/transition';
    
    $: heroString = writable("Smith Hayward");

    setTimeout(()=> {
        $heroString = "Business Analyst";
    }, 2000);

</script>


<div class="flex flex-row h-svh bg-slate-200">

    <div transition:fade={{duration:800}} class=" text-nowrap mx-auto my-auto text-4xl">{$heroString}</div>

</div>