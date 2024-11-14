<script>
	import '../app.css';
	import Header from '$lib/Header.svelte';
	let { children } = $props();
</script>

<div class="flex flex-col min-h-screen items-center">
    <Header></Header>

	{@render children()}

	<footer
        class="flex flex-col gap-2 sm:flex-row py-6 w-full shrink-0 items-center px-4 md:px-6 border-t"
    >
        <p class="text-xs text-gray-500">
            © 2024 Repertoire. All rights reserved.
        </p>
        <nav class="sm:ml-auto flex gap-4 sm:gap-6">
            <a class="text-xs hover:underline underline-offset-4" href="/">
                Termos de Serviço
            </a>
            <a class="text-xs hover:underline underline-offset-4" href="/">
                Privacidade
            </a>
        </nav>
    </footer>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Familjen+Grotesk:ital,wght@0,400..700;1,400..700&display=swap');

    :global(html) {
        font-family: "Familjen Grotesk", sans-serif;
    }

    :global(h1::selection) {
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
    }
</style>
