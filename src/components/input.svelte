<script lang="ts">
    export let value: string | number;
</script>

<label><slot /></label>
<input bind:value type="text" />

<style>
    input {
        border: 1px solid;
        background: white;
        font-size: 16px;
    }
</style>