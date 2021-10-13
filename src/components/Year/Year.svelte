<script>
  import { store } from '../../store/store'
  import { onMount } from 'svelte'
  import Month from '../Month/Month.svelte'
  $: currentYear = $store.currentYear
  $: months = $store.months

  onMount(() => {
    if (
      (currentYear % 400 === 0 && currentYear % 100 !== 0) ||
      currentYear % 4 === 0
    ) {
      store.update((store) => {
        return {
          ...store,
          months: store.months.filter((month) => {
            return month.name === 'February' ? (month.days = 29) : month.days
          }),
        }
      })

      console.log($store)
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
  @media (max-width: 1024px) {
    .container {
      width: 90%;
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (max-width: 830px) {
    .container {
      grid-template-columns: repeat(1, 1fr);
      gap: 2vh 0;
    }
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
