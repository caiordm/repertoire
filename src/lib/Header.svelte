<script>
    import { IconMusic } from "@tabler/icons-svelte";
    import { Hamburger } from "svelte-hamburgers";
    import MenuHamburguer from "./MenuHamburguer.svelte";

    let open = $state(false);
</script>

<header
    class="fixed z-50 mt-4 w-11/12 px-4 lg:px-6 h-16 text-lg flex items-center justify-between bg-gray-100 bg-clip-padding backdrop-filter backdrop-blur-lg bg-opacity-80 border border-gray-50 rounded-2xl"
>
    <a class="flex items-center justify-center" href="/">
        <IconMusic class="h-6 w-6 mr-2" />
        <span class="font-bold text-lg lg:text-xl">Repertoire</span>
    </a>

    <nav class="flex gap-[0.4rem] sm:gap-6">
        <a
            class="font-medium hover:underline underline-offset-4"
            href="#funcionalidades"
        >
            Funcionalidades
        </a>
        <a
            class="font-medium hover:underline underline-offset-4"
            href="#como-funciona"
        >
            Como Funciona
        </a>
        <a
            class="font-medium hover:underline underline-offset-4"
            href="#footer"
        >
            Sobre
        </a>
    </nav>

    <a href="/login" class="hidden lg:block px-6 py-2 bg-purple-700 text-white font-medium rounded-lg"
        >Entrar</a
    >
    
    <div class="hamburguer-icon">
        <a href="/login" class="px-6 py-2 text-base bg-purple-700 text-white font-medium rounded-lg"
            >Entrar</a
        >
        
        <Hamburger
            class="hamburguer-icon"
            title="Toggle nav links"
            ariaControls="nav"
            type="spring"
            --layer-spacing="8px"
            --layer-height="2px"
            --border-radius="10px"
            --color="black"
            bind:open
        />
    </div>
</header>
<MenuHamburguer class="hamburguer-menu" bind:open />

<style>
    .hamburguer-icon {
        display: none;
        z-index: 1000;
        cursor: pointer;
    }

    /* Esconde o menu normal em telas menores */
    @media (max-width: 1000px) {
        nav {
            display: none;
        }

        .hamburguer-icon {
            display: block;
        }
    }
</style>
