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
</script>

<div class="index">
  <BookNameTag />
  <div class="text">
    <table>
      <tr>
        <td>
          <div class="btn btn-default btn-sm">1</div>
        </td>
        <td class="text px-3" id="copy-text">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Nesciunt
          adipisci non at aspernatur ipsa ea necessitatibus itaque placeat,
          veritatis explicabo praesentium alias sed asperiores cumque, natus
          tempore deleniti.
        </td>
        <td>
          <button
            class="btn btn-primary btn-sm"
            id="copy-text-btn"
            on:click={copyText}
          >
            <span class="iconify" data-icon="ci:copy" />
          </button>
        </td>
      </tr>
    </table>
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
</style>
