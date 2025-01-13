<script lang="ts">
  import "../app.css";
  let { children } = $props();
</script>

<div class="navbar bg-base-200 min-h-4 h-10">
  <div class="flex-1">
    Jan-Tauri
  </div>
</div>

<div class="flex h-[calc(100vh-2.5rem)] bg-base-200">
  <div class="ml-12 mb-10 flex-grow bg-base-100 border-solid border-2 border-gray-700 rounded-tl-2xl rounded-bl-2xl relative">
    {@render children()}
  </div>
</div>
