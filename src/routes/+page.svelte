<script lang="ts">
    let player = 'x';
    let board = [
        ['', '', ''],
        ['', '', ''],
        ['', '', ''],
    ];

    function togglePlayer() {
        // === is comparison
        if (player === 'x') {
            // = is assignment operator
            player = 'o';
        } else {
            player = 'x';
        }
    }

    function check(x, y) {
        console.log(x, y);

        if (board[x][y] === '') {
            board[x][y] = player;
            togglePlayer();
        }
        console.log(player);
    }
</script>

<h1>Let's Make Tic Tac Toe</h1>

<!-- a div is just a box -->
<div>
    <button on:click={() => check(0, 0)}> { board[0][0] } </button>
    <button on:click={() => check(0, 1)}> { board[0][1] } </button>
    <button on:click={() => check(0, 2)}> { board[0][2] } </button>
</div>
<div>
    <button on:click={() => check(1, 0)}> { board[1][0] } </button>
    <button on:click={() => check(1, 1)}> { board[1][1] }</button>
    <button on:click={() => check(1, 2)}> { board[1][2] } </button>
</div>
<div>
    <button on:click={() => check(2, 0)}> { board[2][0] } </button>
    <button on:click={() => check(2, 1)}> { board[2][1] } </button>
    <button on:click={() => check(2, 2)}> { board[2][2] } </button>
</div>

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