<script>
    import QueueTrack from "./QueueTrack.svelte";
    import tracks from "$lib/tracks.json";

    export let currentTrackIndex;
    
</script>

<div class="aether-queue">
    <div class="divide-y divide-aether-dark-gray">
        {#each tracks as track, index}
            <QueueTrack
                artist={track.artist}
                title={track.title}
                trackIndex = {index}
                trackAmount = {tracks.length}
                {currentTrackIndex}
            ></QueueTrack>
        {/each}
    </div>
</div>
