<script lang="ts">
    import Button from "$lib/button.svelte";
    import Input from "$lib/input.svelte";
    import type { Todo } from "$lib/todo";
    import { onMount } from "svelte";
    import { v4 } from 'uuid';

    let description: string;
    const _todoKeys = 'applings-todo-keys';
    let todos: Todo[] = [];
    let keys: string[] = [];

    function newItem() {
        // new TODO
        const todo: Todo = {
            done: false,
            description: description,
            key: v4()
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
        todos = keys.map((key) => {
            return JSON.parse(localStorage.getItem(key) as string);
        });

        console.log(todos);
    })

    function doneItem() {

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

<Input bind:value={description}>New TODO</Input>
<Button on:click={() => newItem() }>Create Todo</Button>

{#each todos as item}
    <div>
        {item.description}
        <Button on:click={() => deleteItem(item.key)}>Delete</Button>
    </div>
{:else}
    You've completed all your tasks!
{/each}