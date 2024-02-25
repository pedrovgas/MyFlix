<script>
  import Icon from "../components/Icon.svelte";
  import Input from "../components/Input.svelte";
  import { baseAddMedia } from "../components/Base.svelte";

  let nome = "";
  let temporada = "";
  let episodio = "";
  export let updateMediaList;

  const addFlix = () => {
    if (!nome || !temporada || !episodio) return;
    baseAddMedia({ nome, temporada, episodio });
    clearInputs();
    updateMediaList();
  };

  const clearInputs = () => {
    nome = "";
    temporada = "";
    episodio = "";
  };
</script>

<header
  class="grid grid-cols-2 md:grid-cols-5 items-center gap-4 justify-between"
>
  <div class="col-span-2">
    <Input name="Nome" bind:value={nome} />
  </div>
  <Input name="Temporada" bind:value={temporada} />
  <Input name="Episódio" bind:value={episodio} />
  <div class="col-span-2 md:col-span-1">
    <button
      on:click={addFlix}
      class="border-black dark:border-white dark:text-white border flex items-center justify-center p-1 w-full"
    >
      <Icon name="Add" classe="text-lg bg-dark" />
    </button>
  </div>
</header>

<style>
  .gui-gay {
    background: black;
  }
</style>
