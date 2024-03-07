<script>
    import { getContext } from "svelte";
    import QueueTrack from "./QueueTrack.svelte";
    import tracks from "$lib/tracks.json";

    let trackIndex = getContext("currentTrackIndex");
</script>

<div class="aether-queue">
    <div class="divide-y divide-aether-dark-gray">
        {#each tracks as track, index}
            {#if index === trackIndex}
                <QueueTrack
                    artist={track.artist}
                    title={track.title}
                    isCurrentTrack="true"
                ></QueueTrack>
            {:else}
                <QueueTrack artist={track.artist} title={track.title}
                ></QueueTrack>
            {/if}
        {/each}
    </div>
</div>
