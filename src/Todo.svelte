<script lang="ts">
    import { todoStore } from './stores.js';
    export let title: string;
    export let description: string;
    export let complete: boolean = false;
    export let index: number;

    function deleteTodo() {
        todoStore.update(list => {
            list.splice(index,1);
            return list;
        });
    }
</script>

<li class="todo">
    <span class="text">
        <span class="title">{title}</span><br/>
        <span class="description">{description}</span>
    </span>
    
    <span>
        <span class="complete">{complete ? "✅" : "❌"}</span>
        <button on:click={deleteTodo}>Delete</button>
    </span>
</li>

<style>
    li {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        padding: 1em;
        background: #ffffff;
        border-radius: 1em;
        border: 1px solid #d3d3d3;
        width: 100%;
    }
    .todo {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }
    .text {
        display: flex;
        flex-direction: column;
    }
    .title {
        font-weight: 600;
        font-size: larger;
    }
    .description {
        font-size: smaller;
        color: grey;
    }
    .complete {
        margin: 0.25em;
    }
</style>