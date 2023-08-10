<script>
    import { base } from '$app/paths';
    import './app.scss';
    import { Card } from 'artesgo-holokit';
</script>

<nav>
    <a href="{base}/">home</a>
    <a href="{base}/todo">todo</a>
    <a href="{base}/portfolio">Portfolio</a>
    <a href="{base}/tictactoe">tic tac toe</a>
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