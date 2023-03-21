<script>
  import MovieList from './components/MovieList.svelte';
  import MessageCenter from './components/MessageCenter.svelte';

  import SearchSymbol from './assets/search-symbol.png';

  let movieName = '';
  let moviesPromise;

  $: if (movieName.length > 2) {
    // Guardo la promesa
    moviesPromise = fetch(
      `https://www.omdbapi.com/?s=${movieName}&apikey=422350ff`
    )
      .then((res) => res.json())
      .then((apiResponse) => apiResponse.Search);
  }
</script>

<!-- ! Fata hacer la card para las peliculas -->
<main>
  <header>🎞 Movie Search</header>
  <div class="search-container">
    <input
      type="text"
      name="search-input"
      id="search-input"
      placeholder="Enter the movie name..."
      bind:value={movieName}
    />
    <img src={SearchSymbol} alt="" class="input-icon" />
  </div>
  <div class="result-container">
    {#if movieName.length > 2}
      {#await moviesPromise}
        <MessageCenter type="loading" />
      {:then data}
        {#if data}
          <MovieList {data} />
        {:else}
          <MessageCenter type="not found" />
        {/if}
      {:catch}
        <MessageCenter
          type="custom"
          customMessage="Network error. Please try later"
        />
      {/await}
    {:else}
      <MessageCenter type="title" />
    {/if}
  </div>

  <footer>
    <a href="https://github.com/dannielsss/movie-search">View in github</a>
  </footer>
</main>

<style>
  main {
    width: 70%;
    padding: 5rem;
    margin: auto;
  }

  footer {
    position: fixed;
    left: 0;
    bottom: 0;
    padding: 10px;
  }

  footer a {
    color: white;
    text-decoration: none;
  }

  footer a:hover {
    text-decoration: underline;
  }

  header {
    text-align: center;
    font-weight: 700;
    font-size: 2rem;
  }

  /* Estilos para el input */
  .search-container {
    margin-top: 25px;
    position: relative;
    width: 100%;
  }

  .search-container input {
    width: 100%;
    padding: 8px;
    font-size: 17px;
    border-radius: 3px;
    border: none;
    outline: none;
    color: #0e131b;
    text-indent: 40px;
  }

  .search-container .input-icon {
    position: absolute;
    width: 25px;
    height: 25px;
    left: 12px;
    top: 50%;
    transform: translateY(-50%);
  }

  @media screen and (max-width: 992px) {
    main {
      width: 100%;
      padding: 3rem;
    }
  }

  @media screen and (max-width: 600px) {
    header {
      font-size: 1.5rem;
    }
  }
</style>
