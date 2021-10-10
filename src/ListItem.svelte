<script>
  export let artist;
  export let supports;
  export let venue;
  export let date;
</script>

<div class="list-item">
  <div>
    <h2>{artist}</h2>
    <h6>Supports: {supports}</h6>
  </div>
  <div>
    <h4>{venue}</h4>
  </div>
  <div>
    <h4>{date}</h4>
  </div>
</div>

<style>
  .list-item {
    display: flex;
    width: 100%;
    align-items: center;
  }

  .list-item > div {
    flex: 1;
  }

  h2 {
    margin-bottom: 0;
  }

  h6 {
    margin-top: 1.5em;
  }
</style>
