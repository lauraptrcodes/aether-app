<script>
    import QueueTrack from "./QueueTrack.svelte";
    import tracks from "$lib/tracks.json";

    export let currentTrackIndex;

    let sortedTracks = tracks;
    let translateClass = '-translate-y-0';

    function sortTrackInList(){

        //let trackToRecue = sortedTracks.shift();
        // console.log(trackToRecue);
        // in unsichtbare liste einordnen die nach & nach sichtbar wird, 
        // in sichtbarer liste passiert kein weiteres ranking
        // in unsichtbarer liste wird sortiert nach anzahl likes & zwischendurch neue tracks gesprinkelt
        //sortedTracks.push(trackToRecue);
        //sortedTracks = sortedTracks;
        //translatey -40
        let translateAmount = 2.5 * currentTrackIndex;
        console.log(translateAmount);
        //translateClass = `-translate-y-[${translateAmount}px]`;
        translateClass = `-translate-y-[${translateAmount}rem]`;
    }
    
</script>

<div class="aether-queue">
    <div class="divide-y divide-aether-dark-gray {translateClass} transition-all duration-500">
        {#each sortedTracks as track, index}
            <QueueTrack
                artist={track.artist}
                title={track.title}
                trackIndex = {index}
                trackAmount = {tracks.length}
                {currentTrackIndex}
                on:updateQueue = {sortTrackInList}
            ></QueueTrack>
        {/each}
    </div>
</div>
