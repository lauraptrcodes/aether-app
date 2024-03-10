<script>
    import tracks from "$lib/tracks.json";
    import { setContext } from "svelte";

    import Queue from "./Queue.svelte";
    import TrackInfo from "./TrackInfo.svelte";
    import Controls from "./Controls.svelte";

    let currentTrackIndex = 1; // tracks brauchen vllt eindeutige id's weil der aktuelle track ja immer auf die erste stelle in der queue rutscht
    setContext("currentTrackIndex", currentTrackIndex);
    let totalTrackTime;

    const loadAndPlayTrack = () => {
        let audio = new Audio( getCurrentAudioSrc() );
        audio.onloadedmetadata = () => {
            totalTrackTime = audio.duration;
            audio.play(); //promise überprüfen & ggf error catchen
        }

        //audio.ended
    }
    

    function getCurrentAudioSrc() {
        return tracks[currentTrackIndex].trackSrc;
    }

    setContext('audioMuted', true);
    loadAndPlayTrack();
</script>

<div class="aether-content">
    <div class="grid grid-cols-2 gap-4 h-screen mx-8">
        <Queue />
        <TrackInfo track={tracks[currentTrackIndex]} />
    </div>
    <audio autoplay controls preload="metadata" src={getCurrentAudioSrc()}></audio>
</div>
