<script>
  import ImageNotFoundSymbol from '../assets/image-notfund-symbol.svg';

  export let title;
  export let poster;
  export let year;
</script>

<div>
  {#if poster === 'N/A'}
    <div class="poster poster-notfound">
      <img src={ImageNotFoundSymbol} alt="" /> Poster not found
    </div>
  {:else}
    <img src={poster} alt="" class="poster" />
  {/if}
  <div class="title">
    <p>{title}</p>
    <span>{year}</span>
  </div>
</div>

<style>
  .poster {
    height: 400px;
    width: 100%;
    object-fit: cover;
    border-radius: 5px;
  }

  .poster-notfound {
    background: #090c10;

    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 5px;
    font-weight: 300;
    font-size: 18px;
  }

  .poster-notfound img {
    width: 25px;
  }

  .title {
    margin-top: 6px;
    font-weight: 500;
    text-align: center;
  }

  .title p {
    width: 250px;
    margin: auto;
    text-overflow: ellipsis;
    overflow: hidden;
    margin: auto;
    white-space: nowrap;
  }

  .title span {
    font-weight: 300;
  }
</style>
