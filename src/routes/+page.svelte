<script lang="ts">
    import { onMount } from "svelte";

    // our cookie variable
    // variables are something that change over time
    // variable are usually one word, no spaces, or if multiple words, use camelCase
    // camel case is where the new word is capitalized in the middle instead of spaces
    let cookie = 0;
    let grandma = 0;
    let mine = 0;

    /**
     * add some number of cookies in the parameter
     * a function is a piece of code we can run over and over again
     */
    function addCookie(cookies: number) {
        console.log(cookies);
        cookie += cookies; // ++ adds one at a time to the original number
    }

    function addGrandma() {
        grandma++;
    }

    // arrow function
    // () => {}
    onMount(() => {
        setInterval(() => gameLoop(), 1000);
    });

    // key word function creates a new function
    // function signature (how you create a function) is what you see below
    // use the keyword, then the name of the function, and () {}
    // the things you see inside the curly braces is the code you want to run
    // when the function is called
    function gameLoop() {
        let grandmasCookies = grandma * 12;
        addCookie(grandmasCookies);
    }
</script>

<div> Cookies: {cookie} </div>
<div> Grandmas: {grandma} </div>

<button class="cookie" on:click={() => addCookie(1)}> Cookie </button>
<button on:click={() => addGrandma() }> Grandma </button>
<button class="mine"> Mine </button>

<style>
    .cookie {
        border: 1px solid;
        border-radius: 50%;
        height: 50px;
        width: 50px;
    }
</style>
