<script>
    import { onMount } from "svelte";
    import Button from "./Button.svelte";

    export let trackTitle = "Title";
    export let trackArtist = "Artist";
    export let imgSrc;
    
    export let track = {};
</script>

<div class="aether-trackinfo overflow-hidden h-5/6 rounded-lg border-aether-dark-gray w-full">
    <div class="aether-trackinfo-cover w-full aspect-square relative">
        <img src="./img/testimg.png" class="absolute h-full object-center object-cover blur-3xl z-0"/>

        <img src="./img/testimg.png" class="absolute h-full object-center object-cover z-10"/>
    </div>
    <div class="aether-trackinfo-description p-4 flex justify-between rounded-md border-aether-white">
        <p>
            {track.title} <br> 
            <span class="text-aether-salmon">{track.artist}</span> 
        </p>
        <Button icon='info' />
    </div>
</div>