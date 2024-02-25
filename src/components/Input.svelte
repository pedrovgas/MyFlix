<script>
    export let name = "";
    export let value = "";
    let focused = false;
    $: focused = !!value;

    function changeFocused(e) {
        if (e.target.value === "") {
            focused = !focused;
        }
    }
</script>

<div class="relative">
    <label
        for={name}
        class="absolute text-xs px-1 select-none dark:text-gray-200 {focused
            ? 'active'
            : ''}">{name}</label
    >
    <input
        on:focus={changeFocused}
        on:blur={changeFocused}
        bind:value
        type="text"
        {name}
        id={name}
        class="border border-black w-full p-1 ps-1 dark:border-white dark:text-white dark:bg-gray-800"
    />
</div>

<style>
    label {
        left: 2px;
        bottom: 10px;
        transition: 150ms ease-in-out;
    }
    label.active {
        margin: 0;
        display: absolute;
        transform: translateY(-21px);
        background-color: white;
    }

    input:focus-visible {
        outline: none;
    }

    @media (prefers-color-scheme: dark) {
        label.active {
            --tw-bg-opacity: 1;
            background-color: rgb(31 41 55 / var(--tw-bg-opacity));
        }
    }
</style>
