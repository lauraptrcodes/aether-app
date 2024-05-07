<script>
    import Icon from "./Icon.svelte";
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    export let icon;
    export let buttonText;
    export let appearance = 'primary';

    let isActive = false;
    const primaryClasses = 'hover:bg-aether-dark-gray';
    const primaryIconClasses = 'stroke-aether-white';

    const skeletonActiveClasses =
        'stroke-aether-salmon';
    const skeletonClasses =
        'stroke-aether-dark-gray hover:stroke-aether-white group:hover';

    let appearanceClass = '';
    let iconClass = '';
    function setAppearanceClass(appearance) {
        switch (appearance) {
            case 'skeleton':
                iconClass = isActive ? skeletonActiveClasses : skeletonClasses;
                break;
            default:
                appearanceClass = primaryClasses;
                iconClass = primaryIconClasses;
                break;
        }
    }

    function handleClick() {
        isActive = !isActive;
        setAppearanceClass(appearance);
        dispatch("clicked");
    }

    setAppearanceClass(appearance);
</script>

<!-- markup (zero or more items) goes here -->
<div class="aether-button" role="button" on:click={handleClick}>
    <div class="{appearanceClass} group p-2 rounded-md">
        {#if icon}
            <Icon iconName={icon} tailwindClasses={iconClass} />
        {/if}
        {#if buttonText}
            <p class="group-hover:text-aether-salmon">
                {buttonText}
            </p>
        {/if}
    </div>
</div>
