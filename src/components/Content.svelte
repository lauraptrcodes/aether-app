<script>
    import tracks from "$lib/tracks.json";
    import { setContext } from "svelte";

    import Queue from "./Queue.svelte";
    import TrackInfo from "./TrackInfo.svelte";
    import Controls from "./Controls.svelte";
    import Button from "./Button.svelte";

    let currentTrackIndex = 1; // tracks brauchen vllt eindeutige id's weil der aktuelle track ja immer auf die erste stelle in der queue rutscht
    setContext("currentTrackIndex", currentTrackIndex);
    let totalTrackTime;


    const loadAndPlayTrack = () => {
        let audioFile = new Audio("https://download.pariyatti.org/free/_moIbLs95/along_the_path_audio/streaming/Lumbini.mp3");

        //let audioFile = new Audio( getCurrentAudioSrc() );
        audioFile.onloadedmetadata = () => {
            this.totalTrackTime = audioFile.duration;
            audioFile.play(); //promise überprüfen & ggf error catchen
        }

        //audio.ended
    }
    

    function getCurrentAudioSrc() {
        return tracks[currentTrackIndex].trackSrc;
    }

    setContext('audioMuted', true);
    //loadAndPlayTrack();
    function handleAudioMuted(e){
        console.log('whaddup');
        loadAndPlayTrack();
    }
</script>

<div class="aether-content">
    <div class="grid grid-cols-2 gap-4 h-screen mx-8">
        <Queue />
        <TrackInfo track={tracks[currentTrackIndex]} />
    </div>
    <Controls on:audio-muted-update = {handleAudioMuted}/>
    <!--<audio autoplay controls preload="metadata" src={getCurrentAudioSrc()}></audio>-->
</div>
