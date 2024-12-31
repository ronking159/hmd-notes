<script lang="ts">
    import { open } from '@tauri-apps/plugin-dialog'
    import './tiny-dme.css'

    let debug_message = $state('DEBUG')

    async function openNotebook() {
        let path
        try {
            path = await open({
                multiple: false,
                directory: true
            })
        } catch(e) {
            debug_message = JSON.stringify(e)
            return
        }

        if (path == null) {
            debug_message = 'User selection canceled'
            return
        }

        debug_message = path
    }

    async function openFile() {
        let path
        try {
            path = await open({
                multiple: false,
                directory: false
            })
        } catch(e) {
            debug_message = JSON.stringify(e)
            return
        }

        if (path == null) {
            debug_message = 'User selection canceled'
            return
        }

        debug_message = path

        location.href = `/file?path=${path}`
    }
</script>

<main class="w-full h-full flex justify-center items-center flex-col gap-10">
    <h1 class="text-4xl">Hebrew Markdown Notes</h1>
    <div class="flex gap-4">
        <button class="btn btn-primary" onclick={openNotebook}>Open Notebook</button>
        <button class="btn btn-primary" onclick={openFile}>Open File</button>
    </div>
    <p class="debug text-warning">{ debug_message }</p>
    <div id="editor" class="w-10 h-10"></div>
</main>