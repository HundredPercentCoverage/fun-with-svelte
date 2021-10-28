<script lang="ts">
  import Article from "./components/Article.svelte";
  import Counter from "./components/Counter.svelte";
  import { count } from "./stores/Counter.store";
  import type { HNArticle } from "./types";

  const getData = async (): Promise<HNArticle[]> => {
    const res = await fetch("https://node-hnapi.herokuapp.com/news?page=1");
    const data = await res.json();

    return data;
  };

  let promise = getData();
</script>

<main class="max-w-screen-xl mx-auto">
  <div class="flex flex-col space-y-4 items-center justify-center mt-10 mb-10 mx-4">
    <h1 class="text-3xl tracking-tighter font-bold">Not Hacker News</h1>
    <div class="flex flex-col items-center">
      <p>Current value of super fun counter: {$count}</p>
      <Counter />
    </div>
    {#await promise}
      <p>Waiting</p>
    {:then articles}
      {#each articles as article}
        <Article {article} />
      {/each}
    {/await}
  </div>
</main>
