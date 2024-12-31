<script lang="ts">
    const params = new URLSearchParams(location.search)

    import '../tiny-dme.css'

    import { Editor, CommandBar } from 'tiny-markdown-editor'
    import { onMount } from 'svelte'

    let content = $state('')

    onMount(() => {
        let editor = new Editor({
            element: 'editor',
            content
        })

        editor.addEventListener('change', () => {
            content = editor.getContent()
        })

        let commandBar = new CommandBar({
            editor,
            element: 'toolbar'
        })

        window.addEventListener('keydown', e => {
            if (e.key == 's' && e.ctrlKey)
                alert('Will save some day')
        })
    })
</script>

<svelte:head>
    <style>
        html, body {
            height: 100%
        }
    </style>
</svelte:head>

<div class="flex flex-col h-full">
    <div class="header">
        <a href="/">Back</a> <span>Editing: { params.get('path') }</span>
    </div>

    <div class="content">
        <div id="toolbar"></div>
        <div id="editor" class="right-0 left-0 h-full"></div>
    </div>
</div>

<p>{ content }</p>

<style>
    .header {
        flex: 0 1 auto;
    }

    .content {
        flex: 1 1 auto;
    }
</style>