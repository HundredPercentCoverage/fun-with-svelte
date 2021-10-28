<script lang="ts">
  import type { HNArticle } from "../types";

  export let article: HNArticle;
</script>

<div class="border-2 rounded-xl shadow-md w-full p-4 mx-4">
  <div class="flex flex-row items-center justify-between">
    <h2 class="font-bold tracking-tighter text-xl">
      <a
        href={article.url}
        rel="noopener noreferrer"
        target="_blank"
        class="hover:opacity-50"
      >
        {article.title}
      </a>
      <span class="font-normal text-xs tracking-normal">({article.domain})</span>
    </h2>
  </div>
  <div>
    <p>
      {article.points} points |
      <a
        href={`https://news.ycombinator.com/item?id=${article.id}`}
        target="_blank"
        rel="noopener noreferrer"
        class="hover:underline"
      >
        {article.comments_count} comments
      </a>
      | {article.time_ago} by {article.user}
    </p>
  </div>
</div>