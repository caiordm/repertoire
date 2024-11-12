<script>
	import '../app.css';
	import { IconMusic } from '@tabler/icons-svelte';
	let { children } = $props();
</script>

<div class="flex flex-col min-h-screen">
	<header class="px-4 lg:px-6 h-14 flex items-center">
        <a class="flex items-center justify-center" href="/">
            <IconMusic class="h-6 w-6 mr-2" />
            <span class="font-bold text-lg">Repertoire</span>
        </a>
        <nav class="ml-auto flex gap-4 sm:gap-6">
            <a
                class="text-sm font-medium hover:underline underline-offset-4"
                href="#funcionalidades"
            >
                Funcionalidades
            </a>
            <a
                class="text-sm font-medium hover:underline underline-offset-4"
                href="#precos"
            >
                Preços
            </a>
            <a
                class="text-sm font-medium hover:underline underline-offset-4"
                href="#footer"
            >
                Sobre
            </a>
        </nav>
    </header>

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
