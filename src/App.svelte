<script>
  import Navbar from './components/Navbar/Navbar.svelte'
  import Year from './components/Year/Year.svelte'
  import Footer from './components/Footer/Footer.svelte'

  const currentYear = new Date().getFullYear()
</script>

<style>
  main {
    width: 100%;
    height: auto;
    display: grid;
    grid-template-rows: auto 93% 3%;
    gap: 10px;
  }
</style>

<main>
  <Navbar />
  <Year />
  <Footer />
</main>
