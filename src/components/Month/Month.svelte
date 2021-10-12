<script>
  import { onMount } from 'svelte'
  import Week from '../Week/Week.svelte'
  export let month
  export let days
  export let isCurrentMonth
  export let monthNumber
  let today = 0
  $: startingDay = 0
  const weekday = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']

  onMount(() => {
    const date = new Date(new Date().getFullYear(), monthNumber, 1)
    startingDay = date.getDay()

    today = parseInt(new Date().toLocaleDateString().split('/')[1])
  })
</script>

<style>
  .month {
    width: 100%;
    height: 100%;
    background-color: #fff;
    border-radius: 5px;
    padding: 10px 15px;
    display: flex;
    flex-direction: column;
    gap: 10px 0;
  }

  .month-name {
    font-weight: 600;
  }

  .days {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    grid-template-rows: repeat(auto, 1fr);
    gap: 5px;
  }

  .day {
    width: 100%;
    height: 100%;
    padding: 5px 10px;
    text-align: center;
    background-color: #eee;
    border-radius: 3px;
  }

  .currentDay {
    background-color: rgb(202, 200, 200);
  }
</style>

<div class="month">
  <div class="month-name">{month}</div>
  <Week {weekday} />
  <div class="days">
    {#each Array(days + startingDay) as _, day}
      {#if day < startingDay}
        <div class="day" />
      {:else}
        <div
          class={`day ${isCurrentMonth && today === day + 1 - startingDay ? 'currentDay' : ''}`}>
          {day + 1 - startingDay}
        </div>
      {/if}
    {/each}
  </div>
</div>
