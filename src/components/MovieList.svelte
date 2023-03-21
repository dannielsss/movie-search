<script>
  import MovieItem from './MovieItem.svelte';

  export let data;
</script>

<div class="movie-list">
  {#each data as item}
    <MovieItem title={item.Title} poster={item.Poster} year={item.Year} />
  {/each}
</div>

<style>
  .movie-list {
    margin-top: 20px;
    width: 100%;

    display: grid;
    grid-template-columns: repeat(3, 1fr);
    place-items: center;
    gap: 20px;
  }

  @media screen and (max-width: 992px) {
    .movie-list {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media screen and (max-width: 600px) {
    .movie-list {
      grid-template-columns: repeat(1, 1fr);
    }
  }
</style>