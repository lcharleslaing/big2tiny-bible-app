<script>
  import "../styles/global.css";
  import Title from "$lib/components/Title.svelte";
  import Navbar from "$lib/components/Navbar.svelte";
  import SearchBar from "$lib/components/SearchBar.svelte";
</script>

<header>
  <Title title="Big2Tiny Bible" description="Your Free Bible Reference" />
  <Navbar />
  <SearchBar />
</header>
<main>
  <!-- page content -->
  <slot />
</main>

<footer>Copyright &copy; 2020 Big2Tiny Bible</footer>

<style>
  footer {
    text-align: center;
    display: block;
    margin-bottom: 20px;
  }
</style>
