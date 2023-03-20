<script>
  export let title;
  export let poster;
  export let year;
</script>

<div>
  <img src={poster} alt="" class="poster" />
  <div class="title">{title} - <span>{year}</span></div>
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
  
  .title span {
    font-weight: 300;
  }
</style>
