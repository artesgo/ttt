<script lang="ts">
    import Button from "$lib/button.svelte";
    import Checkbox from "$lib/checkbox.svelte";
    import Input from "$lib/input.svelte";

    import Player from "./player.svelte";
    import { slide } from 'svelte/transition';

    let player = 'x';
    let gameover = false;
    let emptyBoard = [
        ['', '', ''],
        ['', '', ''],
        ['', '', ''],
    ];

    // copy the empty board via Clone
    let board = structuredClone(emptyBoard);

    //#region hide this
    function togglePlayer() {
        // === is comparison
        if (player === 'x') {
            // = is assignment operator
            player = 'o';
        } else {
            player = 'x';
        }
    }

    function check(x: number, y: number) {
        if (gameover) return; // just end here // early return;

        console.log(x, y);
        if (board[x][y] === '') {
            board[x][y] = player;
            togglePlayer();
        }
        console.log(player);

        let rowMatch = checkRowMatch(x);
        let colMatch = checkColumnMatch(y);
        let diagMatch = checkDiagonals();
        console.log('row', rowMatch);
        console.log('col', colMatch);
        console.log('diag', diagMatch);

        if (rowMatch || colMatch || diagMatch) {
            gameover = true;
        }
    }

    // Last time, we got to a point where we can 
    // sort of play a game of tic tac toe, but manually
    function checkRowMatch(row: number) {
        let item1 = board[row][0];
        let item2 = board[row][1];
        let item3 = board[row][2];
        if (item1 === item2 && item2 === item3) {
            return true;
        }
        return false;
    }
    // npm run dev
    function checkColumnMatch(col: number) {
        let item1 = board[0][col];
        let item2 = board[1][col];
        let item3 = board[2][col];
        if (item1 === item2 && item2 === item3) {
            return true;
        }
        return false;
    }

    function checkDiagonals() {
        let item1 = board[0][0];
        let item2 = board[1][1];
        let item3 = board[2][2];
        
        if (item1 !== '' && item1 === item2 && item2 === item3) {
            return true;
        }

        item1 = board[0][2];
        item2 = board[1][1];
        item3 = board[2][0];
        
        if (item1 !== '' && item1 === item2 && item2 === item3) {
            return true;
        }

        return false;
    }

    //#endregion
    function restartGame() {
        // restart game
        // gameover reset
        // data reset
        board = structuredClone(emptyBoard);
        gameover = false;
    }
</script>

<h1>Let's Make Tic Tac Toe</h1>

<!-- a div is just a box -->
<div>
    <button on:click={() => check(0, 0)}> <Player player={ board[0][0] }></Player> </button>
    <button on:click={() => check(0, 1)}> <Player player={ board[0][1] }></Player> </button>
    <button on:click={() => check(0, 2)}> <Player player={ board[0][2] }></Player> </button>
</div>
<div>
    <button on:click={() => check(1, 0)}> <Player player={ board[1][0] }></Player> </button>
    <button on:click={() => check(1, 1)}> <Player player={ board[1][1] }></Player> </button>
    <button on:click={() => check(1, 2)}> <Player player={ board[1][2] }></Player> </button>
</div>
<div>
    <button on:click={() => check(2, 0)}> <Player player={ board[2][0] }></Player> </button>
    <button on:click={() => check(2, 1)}> <Player player={ board[2][1] }></Player> </button>
    <button on:click={() => check(2, 2)}> <Player player={ board[2][2] }></Player> </button>
</div>

{#if gameover}
    <button transition:slide on:click={restartGame}>Restart</button>
{/if}

<!-- just added this -->
<Button>Hello</Button>
<Input>World</Input>
<Checkbox>Hi Again</Checkbox>

<style>
    button {
        width: 100px;
        height: 100px;
        color: #333333;
        background: lightgreen;
    }

    div {
        display: flex;
    }
</style>