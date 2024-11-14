<script>
    let { open = $bindable() } = $props()
</script>


{#if open}
    <nav class="absolute z-50 bg-zinc-50 w-full pt-4 pb-8 border-b-2 border-zinc-200 text-zinc-700 flex flex-col items-center gap-4 lg:gap-8 text-lg lg:text-xl font-regular">
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
{/if}