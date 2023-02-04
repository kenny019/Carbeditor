<script>
    import { onMount, onDestroy } from 'svelte'
    import { Editor } from '@tiptap/core'
    import StarterKit from '@tiptap/starter-kit'

    let element
    export let editor

    onMount(() => {
    editor = new Editor({
        element: element,
        extensions: [
        StarterKit.configure({
            heading: false,
        }),
        ],
        content: '<p>Hello World!</p>',
        onTransaction: () => {
        // force re-render so `editor.isActive` works as expected
        editor = editor
        },
    })
    })

    onDestroy(() => {
    if (editor) {
        editor.destroy()
    }
    })

    function handleClick() {
        if (editor.isEmpty) {
            editor.commands.focus('start');
        }
    }
</script>



<div id = "editor" on:click={handleClick} bind:this={element} />


<style>
    #editor {
        height: 100%;
        border-color: black;
        border-width: 2px;
        border-style: solid;
        border-radius: 1rem;
        padding: 1rem;
    }
</style>