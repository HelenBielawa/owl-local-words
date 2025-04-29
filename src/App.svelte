<script>
  import Wort from './Wort.svelte';
</script>

<main >
  <div class="batik"></div>
  <Wort />
</main>

<style>
  /* Fullscreen background */
  main {
    position: fixed;
    width: 100%;
    height: 100%;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
  }

  /* Batik effect */
  .batik {
    position: absolute;
    width: 200%;
    height: 200%;
    background: radial-gradient(circle at 20% 30%, #003566, transparent 50%),
                radial-gradient(circle at 70% 80%, #001d3d, transparent 50%),
                radial-gradient(circle at 50% 50%, #000814, transparent 50%);
    animation: batikFlow 20s infinite alternate;
    z-index: 1;
    opacity: 0.9;
    will-change: transform;
  }
  @keyframes batikFlow {
  0% {
    transform: translate3d(0, 0, 0) scale(1);
  }
  25% {
    transform: translate3d(10%, -15%, 0) scale(1.05);
  }
  50% {
    transform: translate3d(-10%, 20%, 0) scale(1.1);
  }
  75% {
    transform: translate3d(15%, -10%, 0) scale(1.05);
  }
  100% {
    transform: translate3d(-5%, 5%, 0) scale(1);
  }
}

</style>