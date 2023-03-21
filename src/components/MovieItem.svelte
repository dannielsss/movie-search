<script>
  export let title;
  export let poster;
  export let year;
</script>

<div>
  <img src={poster} alt="" class="poster" />
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

  .title {
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
