<script lang="ts">
    import { onDestroy } from 'svelte';
    import { todoStore } from "./stores";
    import Todo from "./Todo.svelte";
    import TodoPusher from "./TodoPusher.svelte";
    let todoList = []
    let todoListUnsub = todoStore.subscribe(val => todoList = val);

    onDestroy(() => todoListUnsub())
</script>

<main>
    <h1>RealtimeTodos</h1>
    <ul>
	{#each todoList as todo, idx}
        <Todo 
            title={todo.title} 
            description={todo.description} 
            complete={todo.complete}
            index={idx}
        />
    {/each}
    </ul>
    <TodoPusher/>
</main>

<style>
	h1 {
		font-size: 3em;
		font-weight: 100;
	}
</style>