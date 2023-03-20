<script>
  import LoadingSymbol from '../assets/loading-symbol.svg';
  import MovieSymbol from '../assets/movie-symbol.svg';

  export let type;
  export let customMessage = '';
</script>

<div class="center">
  {#if type === 'loading'}
    <img src={LoadingSymbol} alt="" class="rotate" /> Loading...
  {:else if type === 'title'}
    <img src={MovieSymbol} alt="" /> Find your movie
  {:else if type === 'not found'}
    <div class="not-found">
      <span>Not found</span>
      <h1>404</h1>
    </div>
  {:else if type === 'custom'}
    <span>{customMessage}</span>
  {:else}
    <i>Error loading the component...</i>
  {/if}
</div>

<style>
  .center {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    height: 50vh;
    font-size: 20px;
    font-weight: 500;
  }

  .center img {
    width: 40px;
  }

  .center .rotate {
    animation-duration: 1s;
    animation-name: rotateItem;
    animation-iteration-count: infinite;
  }

  .center .not-found {
    text-align: center;
  }

  .center span {
    font-weight: 300;
  }

  /* Animacion para el simbolo de loading... */
  @keyframes rotateItem {
    from {
      transform: rotate(0deg);
    }

    to {
      transform: rotate(360deg);
    }
  }
</style>
