<script>
    import Button from "./Button.svelte";
    import { getContext } from "svelte";
    import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

    let isAudioMuted = getContext('audioMuted');

    function toggleMute(){
        isAudioMuted = !isAudioMuted;
        dispatch('audio-muted-update', isAudioMuted);
    }
</script>

<div class="fixed bottom-0 w-full h-20">
    <Button icon="mute" on:clicked={toggleMute}></Button>
</div>