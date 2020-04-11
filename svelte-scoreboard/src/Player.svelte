<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let playerName;
  export let points;
  let showControls = false;

  const addPoint = () => {
    points++;
  };

  const removePoint = () => {
    points--;
  };

  const toggleControls = () => {
    showControls = !showControls;
  };

  const remove = () => {
    dispatch("removeplayer", playerName);
  };
</script>

<style>
  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 2em;
    font-weight: 100;
  }

  h3 {
    margin-bottom: 1rem;
  }
</style>

<div class="card">
  <h1>
    {playerName}
    <button class="btn" on:click={toggleControls}>
      {#if showControls}-{:else}+{/if}
    </button>
    <button on:click={remove} class="btn">Remove</button>
  </h1>
  <h3>Points: {points}</h3>

  {#if showControls}
    <button class="btn" on:click={addPoint}>+1</button>
    <button class="btn" on:click={removePoint}>-1</button>
    <input type="number" bind:value={points} />
  {/if}
</div>
