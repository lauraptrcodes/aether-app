<script>
    import Icon from "./Icon.svelte";

    let tailwindClasses = 'fill-none stroke-aether-dark-gray hover:stroke-aether-white group:hover';

    let likeIsActive = false;
    function toggleLike() {
        if(!likeIsActive) {
            tailwindClasses = 'transition-all fill-aether-salmon stroke-aether-salmon';
        } else {
            tailwindClasses = 'transition-all fill-none stroke-aether-dark-gray hover:stroke-aether-white group:hover';
        }
        likeIsActive = !likeIsActive;
    }
</script>

<!-- markup (zero or more items) goes here -->
<div class="aether-likebutton px-2 group" on:click={toggleLike}>
    <div>
        <Icon iconName='heart' tailwindClasses={tailwindClasses}/>
    </div>
</div>