<script>
    import './app.scss';
    import { Card } from 'artesgo-holokit';
</script>

<nav>
    <a href="/">home</a>
    <a href="/todo">todo</a>
    <a href="/tictactoe">tic tac toe</a>
</nav>

<main>
    <Card>
        <slot />
    </Card>
</main>

<style>
    nav {
        display: flex;
        justify-content: space-evenly;
    }

    a {
        /* margin: 100px; */
        border: 1px dashed;
        padding: 10px 20px;
    }

    main {
        width: 80%;
        margin: 10px auto;
    }
</style>