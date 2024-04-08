<script>
    import tracks from "$lib/tracks.json";
    import { setContext } from "svelte";

    import Queue from "./Queue.svelte";
    import TrackInfo from "./TrackInfo.svelte";
    import Controls from "./Controls.svelte";

    let currentTrackIndex = 2; // tracks brauchen vllt eindeutige id's weil der aktuelle track ja immer auf die erste stelle in der queue rutscht
    setContext("currentTrackIndex", currentTrackIndex);
    let totalTrackTime;

    let audioFile; // = new Audio(tracks[currentTrackIndex].trackSrc);

    const loadAndPlayTrack = () => {
        //let audioFile = new Audio(tracks[currentTrackIndex].trackSrc);
        //
        /* audioFile.onloadedmetadata = () => {
            this.totalTrackTime = audioFile.duration;
            audioFile.play(); //promise überprüfen & ggf error catchen
        }*/
        audioFile = new Audio(tracks[currentTrackIndex].trackSrc);
        audioFile.play();
        audioFile.onended = () => {
            handleNextTrack();
            console.log("ended");
        };

        //audio.ended
    };

    setContext("audioMuted", true);

    function handleAudioMuted() {
        audioFile.muted = !audioFile.muted;
    }

    function handlePlayPause() {
        if (audioFile) {
            if (audioFile.paused) {
                audioFile.play();
            } else {
                audioFile.pause();
            }
        } else{
            loadAndPlayTrack();
        }
    }

    function handleNextTrack(){
        console.log(tracks.length);
        currentTrackIndex = (currentTrackIndex + 1) % tracks.length;
        console.log(currentTrackIndex);
        loadAndPlayTrack();
    }
</script>

<div class="aether-content">
    <div class="grid grid-cols-2 gap-4 h-screen mx-8">
        <Queue />
        <TrackInfo track={tracks[currentTrackIndex]} />
    </div>
    <Controls
        on:audio-muted-update={handleAudioMuted}
        on:audio-playing-update={handlePlayPause}
    />
    <!--<audio autoplay controls preload="metadata" src={getCurrentAudioSrc()}></audio>-->
</div>
