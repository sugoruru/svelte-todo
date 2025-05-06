<script lang="ts">
import { priorityTypes } from "./constants";
import type { TODO } from "./types";

export let todoList: TODO[];
export let deleteToDo: (id: number) => void = () => {};
</script>

<div class="p-4 bg-gray-50 rounded-lg shadow">
    {#if todoList.length === 0}
    <p class="text-gray-500 text-center py-4">TODOがありません</p>
    {:else}
    <ul class="space-y-3">
        {#each todoList as todo}
        <li class="flex items-center justify-between p-3 bg-white rounded-md shadow-sm hover:shadow transition-shadow duration-200">
            <div class="flex items-center">
                <span class={`px-2 py-1 rounded text-white font-semibold text-xs ${priorityTypes[todo.priority].color}`}>
                    {priorityTypes[todo.priority].name}
                </span>
                <span class="text-gray-800 mx-5">{todo.title}</span>
            </div>
            <button
                class="w-8 h-8 flex-shrink-0 flex items-center justify-center bg-red-500 hover:bg-red-600 text-white rounded-full transition-colors duration-200"
                on:click={() => deleteToDo(todo.id)}
                aria-label="削除">
                ×
            </button>
        </li>
        {/each}
    </ul>
    {/if}
</div>
