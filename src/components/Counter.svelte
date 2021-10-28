<script>
  import { count } from '../stores/Counter.store';

  const increment = () => count.update(currentValue => currentValue + 1);
  const decrement = () => count.update(currentValue => currentValue - 1);
</script>

<div class="flex flex-row space-x-4 items-center">
  <button on:click={increment}><span>&plus;</span></button>
  <button on:click={decrement}>-</button>
</div>