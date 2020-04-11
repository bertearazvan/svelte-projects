<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    {
      name: "Razvan",
      points: 54
    },
    {
      name: "Andrei",
      points: 22
    },
    {
      name: "Cassandra",
      points: 100
    }
  ];

  const addPlayer = e => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const removePlayer = e => {
    console.log(e.detail);
    players = players.filter(player => player.name !== e.detail);
  };
</script>

<main>
  <Navbar />
  <AddPlayer on:addplayer={addPlayer} />
  <div class="container">
    {#if players.length === 0}
      <p>No players</p>
    {:else}
      {#each players as player}
        <Player
          playerName={player.name}
          points={player.points}
          on:removeplayer={removePlayer} />
      {/each}
    {/if}
  </div>

</main>
