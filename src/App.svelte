<script>
  import Header from "./containers/Header.svelte";
  import Register from "./containers/Register.svelte";
  import List from "./containers/List.svelte";
  import { baseGetMediaList } from "./components/Base.svelte";

  let medias = baseGetMediaList();

  function updateMediaList() {
    medias = baseGetMediaList();
  }
</script>

<main class="min-h-screen max-w-screen-lg m-auto flex flex-col gap-4 p-5">
  <Header />
  <Register {updateMediaList} />
  <List {medias} {updateMediaList} />
</main>

<style>
</style>
