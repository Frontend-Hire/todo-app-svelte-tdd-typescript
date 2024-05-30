<script lang="ts">
  import { onMount } from 'svelte';

  let secondsPassed = 0;

  onMount(() => {
    const interval = setInterval(() => {
      secondsPassed += 1;
    }, 1000);

    return () => clearInterval(interval);
  });
</script>

<div>
  <slot name="header" />
  <p>Seconds passed: {secondsPassed}</p>
  <ul>
    <slot />
  </ul>
</div>
