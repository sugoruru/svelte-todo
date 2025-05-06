<script lang="ts">
export let label: string;
export let ID: string;
export let value: string;
export let className = "";
</script>

<div class={className}>
    <label for={ID}>
        {label}
        <input
            type="text"
            id={ID}
            class="rounded w-full my-2"
            bind:value={value}
            />
    </label>
</div>
