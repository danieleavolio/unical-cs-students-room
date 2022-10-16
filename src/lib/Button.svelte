<script>
  export let text = "Text";
  export let type ='submit'
</script>

<div class="md:flex md:items-center">
  <div class="w-full">
    <button on:click
      class="w-full shadow bg-purple-500 hover:bg-purple-400 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded"
      {type}
    >
      {text}
    </button>
  </div>
</div>

<style>
</style>
