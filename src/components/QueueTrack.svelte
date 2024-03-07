<script>
    import LikeButton from "./LikeButton.svelte";
    export let artist;
    export let title;
    export let isCurrentTrack;

    let activeTailwindClasses = isCurrentTrack ? 'border-l-4 border-aether-salmon':'';
    let activeTailwindText = isCurrentTrack ? 'text-aether-salmon' : '';

</script>

<div class="p-2 {activeTailwindClasses}">
    <div class="w-full flex">
        <p class="{activeTailwindText}">
          {title} - {artist}  
        </p>
        <LikeButton icon='heart'></LikeButton>
    </div>
</div>