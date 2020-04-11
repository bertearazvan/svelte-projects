<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let player = {
    name: "",
    points: ""
  };

  const onSubmit = e => {
    e.preventDefault();
    dispatch("addplayer", player);
    player = {
      name: "",
      points: ""
    };
  };
</script>

<style>
  form {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    margin: 0 2rem;
  }
</style>

<form on:submit={onSubmit} class="grid-3">
  <input type="text" placeholder="Player name" bind:value={player.name} />
  <input type="number" placeholder="Player points" bind:value={player.points} />
  <input type="submit" class="btn" value="Add Player" />
</form>
