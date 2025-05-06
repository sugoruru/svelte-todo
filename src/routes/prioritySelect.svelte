<script lang="ts">
import { priorityTypes } from "./constants";
export let priority: number;
export let className = "";
</script>

<div class={className}>
    <label for="selectInput">
        Priority
        <select id="selectInput" class="w-full rounded" bind:value={priority}>
            {#each priorityTypes as type,index}
            <option value={index}>{type.name}</option>
            {/each}
        </select>
    </label>
</div>
