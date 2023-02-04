<script lang="ts">
  import Tiptap from './lib/Tiptap.svelte';
  import Shell from './lib/Shell.svelte';

  let editor
</script>

<main>
  <Shell editor= {editor}>
    <Tiptap bind:editor={editor}/>
  </Shell>
</main>
