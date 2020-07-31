<script lang="ts">
import type { space } from "svelte/internal";

    export let title: string;
    export let description: string;
    export let complete: boolean = false;
    export let index: number;
</script>

<li class="todo">
    <span class="text">
        <span class="title">{title}</span><br/>
        <span class="description">{description}</span>
    </span>
    
    <span>
        <span class="complete">{complete ? "✅" : "❌"}</span>
        <button on:click={() => console.log("Delete", index)}>Delete</button>
    </span>
</li>

<style>
    li {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    .todo {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 20vw;
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