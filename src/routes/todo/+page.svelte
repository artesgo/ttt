<script lang="ts">
    import type { Todo } from "$lib/todo";
    import { Button, Checkbox, TextInput } from "carbon-components-svelte";
    import { onMount } from "svelte";
    import { v4 } from 'uuid'; // <<<<<<

    let description: string;
    const _todoKeys = 'applings-todo-keys';
    let todos: Todo[] = [];
    let keys: string[] = [];

    function newItem() {
        // new TODOs
        const todo: Todo = {
            done: false,
            description: description,
            key: v4() // <<<<<<
        }

        // spread operation
        todos = [...todos, todo];
        keys = [...keys, todo.key];

        // localStorage
        localStorage.setItem(todo.key, JSON.stringify(todo));
        localStorage.setItem(_todoKeys, JSON.stringify(keys));
    }

    onMount(() => {
        keys = JSON.parse(localStorage.getItem(_todoKeys) as string);

        // maps are tranformation
        if (keys && keys.length) {
            todos = keys.map((key) => {
                return JSON.parse(localStorage.getItem(key) as string);
            });
        }
    })

    function doneItem(todo: Todo) {
        // console.log(todo);
        localStorage.setItem(todo.key, JSON.stringify(todo)); // from newItem(...);
    }

    function deleteItem(key: string) {
        // use the key parameter to look inside our keys / todos array to remove item
        keys = keys.filter((_key) => {
            // filter loops through the keys array and each _key is then compared against our func param
            return key !== _key;
        });

        todos = todos.filter(_todo => {
            return key !== _todo.key;
        });
        
        localStorage.removeItem(key);
        localStorage.setItem(_todoKeys, JSON.stringify(keys));
    }
</script>

<div class="flex controls">
    <TextInput bind:value={description}>New TODO</TextInput>
    <Button size="field" on:click={() => newItem() }>Create Todo</Button>
</div>

{#each todos as item}
    <div class="flex">
        <Checkbox
            bind:checked={item.done}
            on:change={() => doneItem(item)}
            labelText={item.description}
        >
        </Checkbox>
        <Button on:click={() => deleteItem(item.key)}>Delete</Button>
    </div>
{:else}
    You've completed all your tasks!
{/each}

<style>
    .flex {
        display: flex;
        justify-content: flex-start;
        /* centers things vertically */
        align-items: center;
        margin-bottom: 10px;
    }

    .controls {
        margin-bottom: 20px;
    }
</style>