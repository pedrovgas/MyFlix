<script>
  import Icon from "../components/Icon.svelte";
  import { baseRemoveMedia, baseUpdateMedia } from "./Base.svelte";
  export let media;
  export let updateMediaList;

  function deleteRow() {
    baseRemoveMedia(media.id);
    updateMediaList();
  }

  function changeRow(field, value) {
    if (value < 0) return;
    baseUpdateMedia(media.id, field, value);
    updateMediaList();
  }
</script>

<li class="grid grid-cols-5 dark:text-gray-200">
  <div class="col-span-2">
    {media.nome}
  </div>
  <div class="ms-2">
    {media.temporada}
    <button
      class="cursor-pointer text-gray-500"
      on:click={() => changeRow("temporada", parseInt(media.temporada) + 1)}
    >
      <Icon name="arrow_upward" classe="text-sm" />
    </button>
    <button
      class="cursor-pointer text-gray-500"
      on:click={() => changeRow("temporada", parseInt(media.temporada) - 1)}
    >
      <Icon name="arrow_downward" classe="text-sm" />
    </button>
  </div>
  <div class="ms-2">
    {media.episodio}
    <button
      class="cursor-pointer text-gray-500"
      on:click={() => changeRow("episodio", parseInt(media.episodio) + 1)}
    >
      <Icon name="arrow_upward" classe="text-sm" />
    </button>
    <button
      class="cursor-pointer text-gray-500"
      on:click={() => changeRow("episodio", parseInt(media.episodio) - 1)}
    >
      <Icon name="arrow_downward" classe="text-sm" />
    </button>
  </div>
  <div class="text-end">
    <button class="ms-2 cursor-pointer text-gray-500" on:click={deleteRow}>
      <Icon name="Close" classe="text-lg" />
    </button>
  </div>
</li>

<style>
  li button {
    opacity: 0;
    transition: opacity 250ms ease-in;
  }

  li:hover button{
    opacity: 1;
  }
</style>
