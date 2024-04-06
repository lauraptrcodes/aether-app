<script>
    import Icon from "./Icon.svelte";
    import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

    export let icon;
    export let buttonText;

    const iconClasses = 'stroke-aether-white'
</script>

<!-- markup (zero or more items) goes here -->
<div class="aether-button" role="button" on:click={() => dispatch('clicked')}>
    <div class="group p-2 rounded-md hover:bg-aether-dark-gray">
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