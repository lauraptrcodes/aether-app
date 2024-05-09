<script>
    import { createEventDispatcher } from "svelte";
    import LikeButton from "./LikeButton.svelte";

    export let artist;
    export let title;
    export let currentTrackIndex;
    export let trackIndex;
    export let trackAmount;
    const dispatch = createEventDispatcher();

    let finishedPlaying = false;
    let fadingClass = "opacity-100";

    // falls neuer current trackd der danach ist
    $: if (currentTrackIndex === (trackIndex + 1) % trackAmount) {
        finishedPlaying = true;
        fadingClass = "opacity-0";
        setTimeout(() => {
            dispatch("updateQueue");
            //fadingClass = "opacity-100";
        }, 500);
        // maybe isAboutToEnd prop der auf true gesetzt wird wenn nur noch 0.5s vom song über sind
    }
    //sonst finisched playing = false & dispatch dass track neu eingeordnet werden soll?
</script>

<div class="p-2 transition-all duration-500 {fadingClass}">
    <div class="w-full flex">
        <p
            class="transition-all duration-500
        {currentTrackIndex === trackIndex ? 'text-aether-salmon' : ''}"
        >
            {title} - {artist}
        </p>
        <LikeButton></LikeButton>
    </div>
</div>
