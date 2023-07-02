<script>
  const svelteLogo = './images/svelte-logo.svg';
  const githubLogo = './images/github-logo.svg';
</script>

<header>
  <div class="corner">
    <img src={svelteLogo} alt="svelte-logo">
  </div>
  <div class="nav">
    <svg viewBox='0 0 2 3'>
      <path d='M0,0 L1,2 C1.5,3 1.5,3 2,3 L2,0 Z'></path>
    </svg>

    <div class='tab'>Popcat Combat</div>
    
    <svg viewBox='0 0 2 3'>
      <path d='M0,0 L0,3 C0.5,3 0.5,3 1,2 L2,0 Z'></path>
    </svg>   
  </div>
  <div class="corner">
    <img src={githubLogo} alt="github-logo">
  </div>
</header>

<style>
  header {
    display: flex;
    justify-content: space-between;
  }

  .corner {
    width: 3em;
    height: 3em;
  }

  .corner img {
    padding: 0.2em;
    width: 100%;
    height: 100%;
  }

  .nav {
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
  }
  
  .nav .tab {
    font-size: 1.4em;
    font-weight: 700;
    text-transform: uppercase;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background: var(--color-bg-3);
  }

  .nav svg {
    position: absolute;
    height: 100%;
    top: 0;
  }

  .nav svg:nth-child(1) {
    left: 0;
    transform: translate(-99%, 0);
  }

  .nav svg:nth-child(3) {
    right: 0;
    transform: translate(99%, 0);
  }

  .nav svg path {
    fill: var(--color-bg-3);
  }
</style>
