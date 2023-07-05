<script lang="ts">
    import { fly } from 'svelte/transition';

    export let player = '';
</script>


{#if player === 'x'}
    <img transition:fly={{ x: 100, y: 0 }} src="./corgi.png" alt="player x" />
{:else if player === 'o'}
    <img transition:fly={{ x: -100, y: 0 }} src="./french-bulldog.png" alt="player o" />
{/if}

<style>
    img {
        width: 64px;
        height: 64px;
    }
</style>