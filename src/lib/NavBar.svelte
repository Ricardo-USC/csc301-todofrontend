<script>
  import Button from './Button.svelte';

</script>

<main>
  <nav class="navbar">
    <Button text="Home" navigateTo="/" isNav/>
    <Button text="Settings" navigateTo="/settings" isNav/>
    <Button text="Accounts" navigateTo="/accounts" isNav/>
  </nav>

</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
  .navbar {
    display: flex;
    justify-content: space-around;
    padding: 1em;
    background-color: #f0f0f0;
  }
</style>
