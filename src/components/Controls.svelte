<script>
    import Button from "./Button.svelte";
    import { getContext } from "svelte";
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    let isAudioMuted = getContext("audioMuted");
    let isAudioPlaying = false;
    let playPauseIcon = "play";

    function toggleMute() {
        isAudioMuted = !isAudioMuted;
        dispatch("audio-muted-update", isAudioMuted);
    }

    function togglePlay() {
        isAudioPlaying = !isAudioPlaying;
        playPauseIcon = isAudioPlaying ? "pause" : "play";
        dispatch("audio-playing-update", isAudioPlaying);
    }
</script>

<div class="fixed bottom-0 w-full h-20 flex justify-center px-8">
    <Button icon="mute" on:clicked={toggleMute}></Button>
    <Button icon={playPauseIcon} on:clicked={togglePlay}></Button>
</div>
