<script>
  import { tweened } from 'svelte/motion';
  
  import Button from './Button.svelte';
  import Card from './Card.svelte';
  import Progress from './Progress.svelte';

  import popcatOpenMouth from './assets/popcatOpenMouth.png';
  import popcatCloseMouth from './assets/popcatCloseMouth.png';

  let closeMouthState = true;
  const statisticState = { 'count': 0, 'apm': 0, 'apm max': 0 };
  const apmTweened = tweened(0);
  $: statisticState.apm = Math.round($apmTweened);
  $: (statisticState.apm > statisticState['apm max']) && (statisticState['apm max'] = statisticState.apm);
  
  const apmInterval = 500;
  const progressState = tweened(100);
  
  let combatState = 0;
  let countdown = '';

  const handleStart = () => {
    combatState = 1;
    let prevCount = 0;
    let interval;
    [...Object.keys(statisticState)].forEach(key => statisticState[key] = 0);
    countdown = '5';
    
    setTimeout(() => countdown = '4', 1000);
    setTimeout(() => countdown = '3', 2000);
    setTimeout(() => countdown = '2', 3000);
    setTimeout(() => countdown = '1', 4000);

    setTimeout(() => {
      countdown = '';
      combatState = 2;
      progressState.set(0, { duration: 10000 });
      interval = setInterval(() => {
        $apmTweened = (statisticState.count - prevCount) / apmInterval * 1000 * 60;
        prevCount = statisticState.count;
      }, apmInterval);
    }, 5000);

    setTimeout(() => { 
      combatState = 0;
      $progressState = 100;
      clearInterval(interval);
    }, 15000);
  };
  const handleClick = () => (combatState === 2) && (statisticState.count += 1);
  const toggleMouth = () => closeMouthState = !closeMouthState;
</script>

<main>
  <div class="images">
    <div class='countdown'>{countdown}</div>
    {#if closeMouthState}
      <img src={popcatCloseMouth} alt='popcat close mouth'/>
    {:else}
      <img src={popcatOpenMouth} alt='popcat open mouth'/>
    {/if}      
  </div>
  <div class='progress'>
    <Progress progressState={$progressState}/>
  </div>
  <div class='buttons'>
    <Button 
      buttonContent='Start'
      on:click={handleStart}
      disabled={combatState !== 0}
    />
    <Button 
      on:click={handleClick} 
      on:pointerdown={toggleMouth} 
      on:pointerup={toggleMouth}
      disabled={combatState === 1}
    />
  </div>
  <div class='cards'>
    {#each Object.entries(statisticState) as [item, value]}
      <Card {item} {value}/>
    {/each}
  </div>
</main>

<style>
  main {
    display: flex;
    flex: 1;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    max-width: 30rem;
    margin: 0 auto;
  }

  main > div {
    margin: 0.2rem 0;
  }

  .images {
    width: 100%;
    height: 20rem;
    display: flex;
    justify-content: center;
    position: relative;
  }

  .countdown {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 20em;
    font-weight: bold;
    color: var(--color-bg-0);
    -webkit-text-stroke: 10px var(--color-text);
  }

  img {
    max-width: 100%;
    max-height: 100%;
  }

  .buttons {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: space-between;
  }

  .cards {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    column-gap: 1rem;
  }

  .progress {
    width: 100%;
    height: 2em;
  }

  @media (max-width: 400px) {
    main {
      max-width: 21rem;
    }

    .images {
      height: 14rem;
    }

    .countdown {
      font-size: 14em;
    }

    .cards {
      flex-direction: column;
      row-gap: 1rem;
    }
  }
</style>
