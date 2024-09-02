<script>

    import { writable } from 'svelte/store';
    
    import { fade, slide, fly } from 'svelte/transition';
    
    $: heroString = writable("Smith Hayward");

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


<div class="flex flex-row h-svh bg-slate-200">
{#key $heroString}
    <div class=" text-nowrap mx-auto my-auto text-4xl">{$heroString}</div>
{/key}
</div>