<script>
    import Icon from "./Icon.svelte";

    let tailwindClasses = 'fill-none stroke-aether-dark-gray hover:stroke-aether-white group:hover'

    function likeTrack() {
        tailwindClasses = 'transition-all fill-aether-salmon stroke-aether-salmon';
    }
</script>

<!-- markup (zero or more items) goes here -->
<div class="aether-likebutton px-2 group" on:click={likeTrack}>
    <div>
        <Icon iconName='heart' tailwindClasses={tailwindClasses} class="stroke-aether-white group-hover:stroke-aether-salmon"/>
    </div>
</div>