<script>
    import "../app.css"
    import Nav from '../components/Nav.svelte'
</script>

<Nav></Nav>
<slot></slot>

<svelte:head>
    <style>
        html, body {
            height: 100%;
            overflow-x: hidden;
        }
    </style>
</svelte:head>