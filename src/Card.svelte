<script>
  export let item = 'Count';
  export let value = '100';
</script>

<div class='card'>
  <div class='item'>{item}</div>
  <div class='value'>{value}</div>
</div>

<style>
  .card {
    width: 100%;
    padding: 1em;
    border-radius: 1em;
    background: var(--color-bg-3);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .item {
    font-size: 1.5rem;
  }

  .value {
    font-size: 2rem;
    font-weight: bold;
  }

  @media (max-width: 400px) {
    .card {
      flex-direction: row;
      justify-content: space-around;
    }
  }
</style>
