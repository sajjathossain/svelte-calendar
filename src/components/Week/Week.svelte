<script>
  export let weekday
</script>

<style>
  .container {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 5px;
  }

  .day {
    width: 100%;
    height: 100%;
    padding: 5px 10px;
    text-align: center;
    background-color: rgb(202, 200, 200);
    border-radius: 3px;
  }
</style>

<div class="container">
  {#each weekday as day}
    <div class="day">{day}</div>
  {/each}
</div>
