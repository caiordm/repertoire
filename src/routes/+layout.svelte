<script>
    import "../app.css";
    import Header from "$lib/Header.svelte";
    let { children } = $props();
</script>

{@render children()}

<style>
    @import url("https://fonts.googleapis.com/css2?family=Familjen+Grotesk:ital,wght@0,400..700;1,400..700&display=swap");

    :global(html) {
        font-family: "Familjen Grotesk", sans-serif;
        scroll-behavior: smooth;
    }

    /* :global(h1::selection) {
        background-color: #9333ea;
    }

    :global(h2::selection) {
        background-color: #9333ea;
    }

    :global(h3::selection) {
        background-color: #9333ea;
    }

    :global(p::selection) {
        background-color: #9333ea;
    }

    :global(span::selection) {
        background-color: #9333ea;
    } */
</style>
