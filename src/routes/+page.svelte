<script lang="ts">
    import { open } from '@tauri-apps/plugin-dialog'

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
</script>

<main class="w-full h-full flex justify-center items-center flex-col gap-10">
    <h1 class="text-4xl">Hebrew Markdown Notes</h1>
    <button class="btn btn-primary" on:click={openNotebook}>Open Notebook</button>
    <p class="debug text-warning">{ debug_message }</p>
</main>