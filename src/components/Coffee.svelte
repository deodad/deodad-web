<script lang="ts">
  const values = [...Array(20).keys()].map((i) => i + 24);

  let ratio = $state(16);
  let bloomRatio = $state(2);
  let grams = $state(44);

  const bloom = (g: number) => Math.round(g * bloomRatio);
  const water = (g: number) => g * ratio;
  const total = (g: number) => water(g) + g;
</script>

<table>
  <thead>
    <tr>
      <th>coffee (g)</th>
      <th>bloom (g)</th>
      <th>water (g)</th>
      <th>total (g)</th>
    </tr>
  </thead>
  <tbody>
    {#each values as g}
      <tr>
        <td>{g}</td>
        <td>{bloom(g)}</td>
        <td>{water(g)}</td>
        <td>{total(g)}</td>
      </tr>
    {/each}
    <tr>
      <td><input type="number" bind:value={grams} /></td>
      <td>{bloom(grams)}</td>
      <td>{water(grams)}</td>
      <td>{total(grams)}</td>
    </tr>
  </tbody>
</table>

<section>
  <h3>Adjust the ratios to your liking:</h3>
  <div>water ratio = <input type="number" bind:value={ratio} /></div>
  <div>
    bloom ratio = <input type="number" bind:value={bloomRatio} step="0.1" />
  </div>
</section>

<section>
  <h3>Equations:</h3>
  <div>bloom(coffee) = coffee * bloom ratio</div>
  <div>water(coffee) = coffee * water ratio</div>
  <div>total(coffee) = water(coffee) + coffee</div>
</section>
