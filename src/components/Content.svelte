<script>
    import tracks from "$lib/tracks.json";
    import { setContext } from "svelte";

    import Queue from "./Queue.svelte";
    import TrackInfo from "./TrackInfo.svelte";
    import Controls from "./Controls.svelte";

    let currentTrackIndex = 0; // tracks brauchen vllt eindeutige id's weil der aktuelle track ja immer auf die erste stelle in der queue rutscht
    let totalTrackTime;

    let audioFile; // = new Audio(tracks[currentTrackIndex].trackSrc);
    let audioPaused = true;
    $: console.log(audioPaused);

    const loadAndPlayTrack = () => {
        //let audioFile = new Audio(tracks[currentTrackIndex].trackSrc);
        //
        /* audioFile.onloadedmetadata = () => {
            this.totalTrackTime = audioFile.duration;
            audioFile.play(); //promise überprüfen & ggf error catchen
        }*/
        audioFile = new Audio(tracks[currentTrackIndex].trackSrc);
        audioFile.play();
        audioPaused = false;
        audioFile.onloadedmetadata = () => {
            totalTrackTime = audioFile.duration;
            console.log(totalTrackTime);
        };
        audioFile.onended = () => {
            handleNextTrack();
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
                audioPaused = false;
                audioFile.play();
            } else {
                audioPaused = true;
                audioFile.pause();
            }
        } else{
            loadAndPlayTrack();
        }
    }

    function handleNextTrack(){
        currentTrackIndex = (currentTrackIndex + 1) % tracks.length;
        loadAndPlayTrack();
    }
</script>

<div class="aether-content">
    <div class="grid grid-cols-2 gap-4 h-screen mx-8">
        <Queue {currentTrackIndex}/>
        <TrackInfo track={tracks[currentTrackIndex]} paused={audioPaused} trackDuration={totalTrackTime}/>
    </div>
    <Controls
        on:audio-muted-update={handleAudioMuted}
        on:audio-playing-update={handlePlayPause}
    />
    <!--<audio autoplay controls preload="metadata" src={getCurrentAudioSrc()}></audio>-->
</div>
