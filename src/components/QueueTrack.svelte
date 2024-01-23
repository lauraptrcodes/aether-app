<script>
    import LikeButton from "./LikeButton.svelte";
    export let artist;
    export let title;
</script>

<div class="aether-queuetrack p-2 group">
    <div class="w-full flex">
        <p>
          {title} - {artist}  
        </p>
        <LikeButton icon='heart'></LikeButton>
    </div>
</div>