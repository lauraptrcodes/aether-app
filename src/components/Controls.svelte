<script>
    import Button from "./Button.svelte";
    import { getContext } from "svelte";

    let isAudioMuted = getContext('audioMuted');

    function toggleMute(){
        $isAudioMuted = !isAudioMuted;
    }
</script>

<div class="fixed bottom-0 w-full h-20">
    <Button icon="mute" on:click={toggleMute}></Button>
</div>