<script>
  import { onMount } from 'svelte'
  import Month from '../Month/Month.svelte'
  export let currentYear
  $: months = [
    {
      name: 'January',
      days: 30,
    },
    {
      name: 'February',
      days: 28,
    },
    {
      name: 'March',
      days: 30,
    },
    {
      name: 'April',
      days: 30,
    },
    {
      name: 'May',
      days: 30,
    },
    {
      name: 'June',
      days: 30,
    },
    {
      name: 'July',
      days: 30,
    },
    {
      name: 'August',
      days: 30,
    },
    {
      name: 'September',
      days: 30,
    },
    {
      name: 'October',
      days: 30,
    },
    {
      name: 'November',
      days: 30,
    },
    {
      name: 'December',
      days: 30,
    },
  ]

  onMount(() => {
    if (
      (parseInt(currentYear % 400) === 0 &&
        parseInt(currentYear % 100) !== 0) ||
      parseInt(currentYear % 4) === 0
    ) {
      months[1].days = 29
    }
  })
</script>

<style>
  .container {
    width: 80%;
    height: 100%;
    margin: 0 auto;
    padding: 0.25vh 0;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1vh 1vw;
  }
</style>

<div class="container">
  {#each months as month, idx}
    <Month
      monthNumber={idx}
      isCurrentMonth={new Date().getMonth() === idx ? true : false}
      month={month.name}
      days={month.days} />
  {/each}
</div>
