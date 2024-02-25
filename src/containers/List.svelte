<script>
    import MediaRow from "../components/MediaRow.svelte";

    export let medias = [];
    export let updateMediaList;
</script>

<ol>
    {#each medias as media}
        <li>
            <MediaRow {media} {updateMediaList} />
        </li>
    {/each}
</ol>
