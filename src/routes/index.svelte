<script context="module">
  export async function load({ fetch }) {
    const res = await fetch("https://jsonplaceholder.typicode.com/posts");
    const verses = await res.json();

    if (res.ok) {
      return {
        props: {
          verses,
        },
      };
    } else {
      throw new Error("Verses not currently available, try later");
    }
  }
</script>

<script>
  export let verses;
</script>

<div class="index">
  <ul>
    {#each verses as verse}
      <li>
        <a href={verse.id}>{verse.id} - {verse.title}</a>
      </li>
    {/each}
  </ul>
</div>
<br /><br />

<style>
  .index {
    text-align: center;
    display: block;
    margin-top: 20px;
  }
</style>
