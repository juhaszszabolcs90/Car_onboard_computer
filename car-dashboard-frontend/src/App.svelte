<script>
  let modes = ["normal"]; // Kezdő üzemmód
  let availableModes = ["eco", "sport"]; // Hozzáadható üzemmódok

  // Ellenőrizzük, hogy kevesebb mint 3 üzemmód van-e
  $: canAddMore = modes.length < 3;
</script>

<main>
  <h1>Autó fedélzeti számítógép</h1>
  <div class="modes-container">
      {#each modes as mode}
          <button class="mode-button">{mode}</button>
      {/each}
      <!-- Csak akkor jelenjen meg a "+" gomb, ha kevesebb mint 3 üzemmód van -->
      {#if canAddMore}
          <button class="add-button" on:click={() => {
              const nextMode = availableModes.shift(); // Következő elérhető mód
              modes = [...modes, nextMode]; // Új mód hozzáadása
          }}>
              +
          </button>
      {/if}
  </div>
</main>

<style>
  main {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 2rem;
  }
  .modes-container {
      display: flex;
      justify-content: center;
      gap: 1rem;
      margin-top: 1rem;
  }
  .mode-button {
      padding: 0.5rem 1rem;
      font-size: 1rem;
      font-weight: bold;
      border: 2px solid #007BFF;
      background-color: white;
      color: #007BFF;
      border-radius: 5px;
      cursor: pointer;
  }
  .mode-button:hover {
      background-color: #007BFF;
      color: white;
  }
  .add-button {
      padding: 0.5rem 1rem;
      font-size: 1rem;
      font-weight: bold;
      background-color: #28a745;
      color: white;
      border: none;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      cursor: pointer;
  }
  .add-button:hover {
      background-color: #218838;
  }
</style>
