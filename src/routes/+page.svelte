<script>
    let cookie = 0;
    function rnjesus() {
        cookie++;
    }
</script>

Changes in a branch
<div> Cookies: {cookie} </div>

<button class="cookie" on:click={() => rnjesus()}> Cookie </button>
<button> Grandma </button>
<button> Mine </button>

<style>
    .cookie {
        border: 1px solid;
        border-radius: 50%;
        height: 50px;
        width: 50px;
    }
</style>