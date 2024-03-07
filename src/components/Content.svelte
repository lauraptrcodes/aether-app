<script>
    import tracks from "$lib/tracks.json";
    import { setContext } from "svelte";

    import Queue from "./Queue.svelte";
    import TrackInfo from "./TrackInfo.svelte";

    let currentTrackIndex = 1;

    setContext("currentTrackIndex", currentTrackIndex);

    function getCurrentAudioSrc() {
        return tracks[currentTrackIndex].trackSrc;
    }
</script>

<div class="aether-content">
    <div class="grid grid-cols-2 gap-4 h-screen mx-8">
        <Queue />
        <TrackInfo track={tracks[currentTrackIndex]} />
    </div>
    <audio autoplay controls src={getCurrentAudioSrc()}></audio>
</div>
