<script>
  export let progressState = 100;
</script>

<div class='progress-bar' style="--progress-state: {progressState}%"></div>

<style>
  .progress-bar {
    width: 100%;
    height: 100%;
    border-radius: 1em;
    background: transparent;
    position: relative;
    overflow: hidden;
  }

  .progress-bar:before {
    content: '';
    position: absolute;
    width: 1200px;
    height: 800px;
    top: 50%;
    left: 50%;
    background: url('../images/galaxy.jpg');
    background-size: cover;
    z-index: -1;
    animation: galaxy 120s linear infinite;
  }

  .progress-bar:after {
    content: '';
    width: 100%;
    height: 100%;
    position: absolute;
    background: var(--color-bg-0);
    transform: translateX(var(--progress-state));
  }

  @keyframes galaxy {
    0% {
      transform: translate(-50%, -45%) rotate(0deg);
    }
    25% {
      transform: translate(-55%, -50%) rotate(90deg);
    }
    50% {
      transform: translate(-50%, -55%) rotate(180deg);
    }
    75% {
      transform: translate(-45%, -50%) rotate(270deg);
    }
    100% {
      transform: translate(-50%, -45%) rotate(360deg);
    }
  }
</style>
