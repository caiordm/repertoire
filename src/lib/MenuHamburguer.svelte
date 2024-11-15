<script>
    let { open = $bindable() } = $props()
</script>


{#if open}
    <nav class="fixed z-40 mt-24 w-11/12 bg-gray-100 bg-clip-padding backdrop-filter backdrop-blur-lg bg-opacity-90 border border-gray-100 rounded-2xl flex flex-col items-center p-4 gap-4 lg:gap-8 text-lg lg:text-xl font-regular">
        <a
            class="text-sm font-medium hover:underline underline-offset-4"
            href="#funcionalidades"
        >
            Funcionalidades
        </a>
        <a
            class="text-sm font-medium hover:underline underline-offset-4"
            href="#como-funciona"
        >
            Como Funciona
        </a>
        <a
            class="text-sm font-medium hover:underline underline-offset-4"
            href="#footer"
        >
            Sobre
        </a>
    </nav>
{/if}