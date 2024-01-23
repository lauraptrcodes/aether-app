<script>
    import Icon from "./Icon.svelte";

    export let icon;
    export let buttonText;

    const iconClasses = 'stroke-aether-white group-hover:text-aether-salmon'
</script>

<!-- markup (zero or more items) goes here -->
<div class="aether-button">
    <div
        class="group p-3
    hover:border-aether-salmon"
    >
        {#if icon}
            <Icon iconName={icon} tailwindClasses={iconClasses}/>
        {/if}
        {#if buttonText}
            <p class="group-hover:text-aether-salmon">
                {buttonText}
            </p>
        {/if}
    </div>
</div>