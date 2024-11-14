<script>
    import { IconMusic } from "@tabler/icons-svelte";
    import { Hamburger } from "svelte-hamburgers";
    import MenuHamburguer from "./MenuHamburguer.svelte";

    let open = $state(false);
</script>

<header class="fixed z-50 mt-4 w-11/12 px-4 lg:px-6 h-16 flex items-center justify-between bg-gray-300 bg-clip-padding backdrop-filter backdrop-blur-lg bg-opacity-20 border border-gray-100 rounded-2xl">
    <a class="flex items-center justify-center" href="/">
        <IconMusic class="h-6 w-6 mr-2" />
        <span class="font-bold text-lg">Repertoire</span>
    </a>

    <nav class="flex gap-[0.4rem] sm:gap-6">
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

    <div class="hamburguer-icon">
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
    .hamburguer-menu {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 80%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.9);
        flex-direction: column;
        justify-content: center;
        align-items: center;
        z-index: 999;
        transition: 0.3s ease;
    }

    .hamburguer-icon {
        display: none;
        z-index: 1000;
        cursor: pointer;
        color: wheat;
    }

    .hamburguer-menu a {
        color: white;
        font-size: 24px;
        margin: 1rem 0;
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
