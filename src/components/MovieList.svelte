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

    display: grid;
    grid-template-columns: repeat(3, 1fr);
    place-items: center;
    gap: 20px;
  }
</style>