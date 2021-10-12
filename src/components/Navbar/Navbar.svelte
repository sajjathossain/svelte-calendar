<script>
  export let year
</script>

<style>
  .container {
    width: 80%;
    height: 100%;
    margin: 0.25vh auto;
    padding: 0.5vh 0.25vw;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 1.5em;
    font-weight: 500;
  }
</style>

<div class="container">
  <div>Calendar</div>
  <div>{year}</div>
</div>
