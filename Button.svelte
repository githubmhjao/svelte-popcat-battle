<script>
  export let buttonContent = 'Meow';
  export let disabled = false;
</script>

<button on:click on:pointerdown on:pointerup {disabled}>
  {buttonContent}
</button>

<style>
  button {
    color: #fff; 
    font-size: 2em;
    letter-spacing: 0.1em;
    padding: 0.2em 0.2em;
    margin: 0.2em;
    width: 100%;
    border-radius: 0.2em;
    border: none;
    outline: none;
    background: transparent;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    user-select: none;
  }

  button:before {
    content: '';
    position: absolute;
    width: 600px;
    height: 400px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: url('../images/galaxy.jpg');
    background-size: cover;
    z-index: -1;
    animation: galaxy 60s linear infinite;
  }

  button:hover {
    filter: brightness(1.2);
  }

  button:active {
    filter: brightness(0.8);
  }

  button:disabled {
    filter: grayscale(1);
    pointer-events: none;
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