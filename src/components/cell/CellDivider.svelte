<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import FaPlus from "svelte-icons/fa/FaPlus.svelte";

  const dispatch = createEventDispatcher();

  export let visible: boolean = false;
</script>

<div class="divider" class:visible>
  <hr />
  <button on:click={() => dispatch("create", { type: "code" })} tabindex="-1">
    <div class="h-3 w-3 mr-[4px]"><FaPlus /></div>
    <span>Code Cell</span>
  </button>
  <button
    on:click={() => dispatch("create", { type: "markdown" })}
    tabindex="-1"
    class="ml-4"
  >
    <div class="h-3 w-3 mr-[4px]"><FaPlus /></div>
    <span>Markdown Cell</span>
  </button>
  <button
    on:click={() => dispatch("create", { type: "plot" })}
    tabindex="-1"
    class="ml-4"
  >
    <div class="h-3 w-3 mr-[4px]"><FaPlus /></div>
    <span>Plot Cell</span>
  </button>
</div>

<style lang="postcss">
  .divider {
    @apply h-2 relative flex justify-center items-center transition-opacity
      opacity-0 hover:opacity-100 focus:opacity-100;
  }

  .divider.visible {
    @apply opacity-100;
  }

  .divider > hr {
    @apply absolute w-full border-dotted border-gray-300;
  }

  .divider > button {
    @apply flex items-center bg-white z-10 px-2.5 py-1 text-xs rounded-md shadow
      transition-colors hover:bg-gray-50 active:bg-gray-200;
  }
</style>
