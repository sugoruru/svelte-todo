<script lang="ts">
export let text = "Button";
export let onClick = () => {
  console.log("Button clicked!");
};
export let className = "";
export let disabled = false;
</script>

<div class={className}>
    <button class="rounded px-3 py-1 my-5 bg-sky-500 hover:bg-sky-600 text-white font-bold transition disabled:bg-gray-500"
        on:click={onClick}
        disabled={disabled}
        >
        {text}
    </button>
</div>
