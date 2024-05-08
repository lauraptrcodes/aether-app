<script>
    import LikeButton from "./LikeButton.svelte";
    export let artist;
    export let title;
    export let currentTrackIndex;
    export let trackIndex;
    export let trackAmount;
    let isCurrentTrack;

    isCurrentTrack = currentTrackIndex === trackIndex;
    let fadingClass = '';

    $: () => {
        if(currentTrackIndex = (currentTrackIndex + 2) % trackAmount){

        }
    }
</script>

<div class="p-2">
    <div class="w-full flex ">
        <p class="{currentTrackIndex === trackIndex ? 'text-aether-salmon' : ''} {fadingClass}">
          {title} - {artist}  
        </p>
        <LikeButton></LikeButton>
    </div>
</div>