<script>
    import Button from "./Button.svelte";
</script>

<!-- markup (zero or more items) goes here -->
<div class="aether-navigation w-full justify-center flex">
    <div class="flex justify-center items-center space-x-4 max-w-3xl my-6">
        <Button icon='globe'>local settings</Button>
        <h1 class="text-3xl">aether</h1>
        <Button icon='add'>add a track</Button>
‚    </div>
</div>

<style lang="postcss">
    /* styles go here */
    .aether-navigation {
    }
</style>
