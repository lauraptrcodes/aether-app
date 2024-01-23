<script>
    import QueueTrack from "./QueueTrack.svelte";

    const tracks = [
        {
            title: "titel",
            artist: "interpret",
        },
        {
            title: "babedibubedi",
            artist: "delivery",
        },
        {
            title: "intro",
            artist: "bay laurel",
        },
    ];
</script>

<div class="aether-queue">
    <div class="divide-y divide-aether-dark-gray">
        {#each tracks as track}
            <QueueTrack artist={track.artist} title={track.title}></QueueTrack>
        {/each}
    </div>
</div>
