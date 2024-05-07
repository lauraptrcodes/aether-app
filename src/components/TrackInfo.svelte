<script>
    import Button from "./Button.svelte";

    export let track;
    let infoIsOpen = false;

    let infoOpenClass = infoIsOpen ? "w-24 rounded-lg" : "w-full";
    let infoTextClass = "opacity-0";

    function toggleInfoOpen() {
        infoIsOpen = !infoIsOpen;
        infoOpenClass = infoIsOpen ? "w-24 rounded-lg m-2" : "w-full";
        infoTextClass = infoIsOpen ? "opacity-100" : "opacity-0";
    }
</script>

<div
    class="relative aether-trackinfo overflow-hidden h-5/6 rounded-lg border-aether-dark-gray"
>
    <div class="absolute h-24 w-full flex justify-end m-2">
        <div class="mr-6 self-center align-middle text-right transition-all duration-700 {infoTextClass}">
            <p>
                {track.title} <br />
                <span class="text-aether-salmon">{track.artist}</span>
            </p>
        </div>
    </div>
    <div class="aether-trackinfo-cover aspect-square p-2 relative">
        <div
            class="absolute top-0 left-0 rounded-none transition-all ease-in-out duration-500 {infoOpenClass}"
        >
            <img
                src={track.trackImg}
                class="absolute object-center object-cover w-full aspect-square blur-3xl z-0"
            />

            <img
                src={track.trackImg}
                class="absolute object-center object-cover z-10  w-full aspect-square transition-all {infoIsOpen
                    ? 'rounded-lg'
                    : 'rounded-none'}"
            />
        </div>
        <div
            class="absolute top-24 left-0 ml-2 mr-2 mt-8 transition-all duration-700 {infoTextClass}"
        >
            <p class="text-aether-mid-gray">
                A text about the making of the song and the interpret - perhaps
                links to find the interpret elsewhere
            </p>
        </div>
    </div>
    <div
        class="aether-trackinfo-description p-4 flex justify-between"
    >
        <p class="transition-all duration-500 {infoIsOpen
            ? 'opacity-0'
            : 'opacity-100'}">
            {track.title} <br />
            <span class="text-aether-salmon">{track.artist}</span>
        </p>
        <Button icon="info" appearance="skeleton" on:clicked={toggleInfoOpen} />
    </div>
</div>
