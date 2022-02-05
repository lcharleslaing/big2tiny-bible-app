<script context="module">
  export async function load({ fetch }) {
    const res = await fetch("http://getbible.net/json?p=James");
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
  import BookNameTag from "$lib/components/BookNameTag.svelte";

  const copyText = function (text) {
    document.getElementById("copy-text-btn").onclick = function () {
      const _this = this;
      navigator.clipboard
        .writeText(document.getElementById("copy-text").innerText)
        .then(function () {
          // toggle class
          _this.classList.remove("btn-primary");
          _this.classList.add("btn-success");

          _this.innerText = "Copied!";
          setTimeout(function () {
            _this.classList.remove("btn-success");
            _this.classList.add("btn-primary");

            // add html icon to button
            _this.innerHTML = '<span class="iconify" data-icon="ci:copy" />';
          }, 1000);
        });
    };
  };

  export let verses;
</script>

<div class="index">
  <BookNameTag name="Old Testament" />
  <div class="text">
    <!-- create a colored tag that has a width that matched the text -->
    <div class="tag tag-primary">
      <span class="tag-text"><a href="/books/genesis">Genesis</a></span>
    </div>
  </div>
</div>
<div class="index">
  <BookNameTag name="New Testament" />
  <div class="text">
    <!-- create a colored tag that has a width that matched the text -->
    <div class="tag tag-primary">
      <span class="tag-text"><a href="#">Mathew</a></span>
    </div>
    <div class="tag tag-primary">
      <span class="tag-text"><a href="#">Mark</a></span>
    </div>
    <div class="tag tag-primary">
      <span class="tag-text"><a href="#">Luke</a></span>
    </div>
    <div class="tag tag-primary">
      <span class="tag-text"><a href="#">John</a></span>
    </div>
  </div>
</div>

<style>
  .index {
    text-align: center;
    display: block;
    margin-top: 20px;
  }
  .text {
    /* display: flex;
    text-align: justify; */
    text-align: justify;
    flex-direction: row;
    margin: 20px;
    font-size: small;
  }
  .verse {
    font-size: xx-small;
    font-weight: bold;
    background-color: gray;
    color: white;
    padding: 2px 5px;
    margin: 0px;
    /* radius */
    border-radius: 5px;
    box-shadow: 2px 2px 2px #afafaf;
  }
  .tag {
    display: inline-block;
    margin: 0px;
    padding: 0px;
    border-radius: 5px;
    box-shadow: 2px 2px 2px #afafaf;
    background-color: lightgray;
    color: white;
  }
  .tag-primary {
    background-color: #007bff;
  }
  a {
    color: inherit;
    text-decoration: none;
    padding: 2px;
  }
  .tag-text {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 100%;
  }
</style>
