<script>
    import Button from "./Button.svelte";
    import { getContext } from "svelte";

    let isAudioMuted = getContext('audioMuted');

    function toggleMute(){
        console.log('clicked');
        isAudioMuted = !isAudioMuted;
        dispatch('audio-muted-update', isAudioMuted);
    }
</script>

<div class="fixed bottom-0 w-full h-20">
    <Button icon="mute" on:click={() => toggleMute()}></Button>
</div>