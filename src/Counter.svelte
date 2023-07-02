<script>
  let count = 0;

  const changeCount = (n) => count = count + n;
</script>

<div class="counter">
  <button on:click={() => changeCount(-1)}>
    <svg aria-hidden="true" viewBox="0 0 1 1">
    <path d="M0,0.5 L1,0.5" />
    </svg>
  </button>
  <div class="counter-viewport">{count}</div>
  <button on:click={() => changeCount(+1)}>
    <svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
		</svg>
  </button>
</div>

<style>
  .counter {
    display: flex;
    margin: 1rem 0;
    border-top: 1px solid rgba(0,0,0,0.1);
    border-bottom: 1px solid rgba(0,0,0,0.1);
  }

  .counter button {
		width: 2em;
		padding: 0;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 0;
		touch-action: manipulation;
		font-size: 2rem;
    background: transparent;
	}

  .counter button:hover {
		background-color: var(--color-bg-1);
	}

  svg {
		width: 25%;
		height: 25%;
	}

	path {
		vector-effect: non-scaling-stroke;
		stroke-width: 2px;
		stroke: #444;
	}

  .counter-viewport {
    width: 8rem;
    height: 4rem;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 4rem;
  }
</style>
