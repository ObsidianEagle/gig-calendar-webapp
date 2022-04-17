<script>
  export let label;
  export let subLabel;
  export let link;
</script>

<a href={link}>
  <div>
    <h1>{label}</h1>
    <h2>{subLabel}</h2>
  </div>
</a>

<style>
  a {
    text-decoration: none;
    color: #ddd;
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 1rem;
    min-width: 15rem;
    margin: 0 1rem;
  }

  a:hover {
    background-color: #333;
  }

  h1, h2 {
    margin: 0;
  }

  h1 {
    font-size: 1.2rem;
    margin: 0 0 0.5rem;
  }

  h2 {
    margin: 0;
    font-size: 0.8rem;
    opacity: 0.7;
  }
</style>
