<script>
    import {
        IconMusic,
        IconList,
        IconShare,
        IconPdf,
        IconChecklist,
    } from "@tabler/icons-svelte";
    import Header from "$lib/Header.svelte";
</script>

<div class="absolute inset-0 -z-10 h-full w-full bg-white bg-[linear-gradient(to_right,#f0f0f0_1px,transparent_1px),linear-gradient(to_bottom,#f0f0f0_1px,transparent_1px)] bg-[size:6rem_4rem]"><div class="absolute bottom-0 left-0 right-0 top-0 bg-[radial-gradient(circle_800px_at_100%_200px,#d5c5ff,transparent)]"></div></div>

<div class="flex flex-col min-h-screen items-center">
    <Header></Header>

    <main class="mt-20 flex flex-col items-center">
        <section
            id="home"
            class="w-full px-4 lg:px-8 py-12 md:py-14 lg:py-24 xl:py-28"
        >
            <div
                class="grid gap-6 lg:grid-cols-[1fr_400px] lg:gap-12 xl:grid-cols-[1fr_600px]"
            >
                <div class="flex flex-col justify-center space-y-4">
                    <div
                        class="space-y-2 flex flex-col text-center lg:text-start"
                    >
                        <h1
                            class="text-3xl font-bold tracking-tighter sm:text-5xl xl:text-6xl/none"
                        >
                            Organize seu repertório musical com facilidade
                        </h1>
                        <p class="max-w-[600px] text-gray-500 md:text-xl">
                            Crie, organize e compartilhe seus setlists sem muito
                            esforço. Perfeito para bandas, artistas solos e
                            entusiastas.
                        </p>
                    </div>
                    <div class="flex flex-col gap-2 justify-center sm:justify-start min-[450px]:flex-row">
                        <a
                            href="/login"
                            class="px-8 py-3 bg-purple-700 text-white text-center font-medium rounded-lg animate-pulse"
                            >Comece Grátis</a
                        >
                        <a
                            href="/saiba-mais"
                            class="px-8 py-3 bg-white text-zinc-900 text-center font-medium border border-zinc-300 rounded-lg"
                        >
                            Saiba Mais
                        </a>
                    </div>
                </div>
                <img
                    alt="Hero"
                    src="https://cdn.pixabay.com/photo/2024/02/17/20/42/ai-generated-8580130_960_720.jpg"
                    class="mx-auto aspect-video overflow-hidden rounded-xl object-cover object-center sm:w-full lg:order-last"
                    height="550"
                    width="550"
                />
            </div>
        </section>

        

        <section
            id="funcionalidades"
            class="w-full px-4 py-12 md:py-24 lg:py-32 bg-gray-100"
        >
            <h2
                class="text-3xl font-bold tracking-tighter sm:text-5xl text-center mb-12"
            >
                Principais Funcionalidades
            </h2>
            <div class="grid gap-6 lg:grid-cols-4">
                <div class="flex flex-col items-center text-center space-y-4">
                    <IconList class="h-12 w-12 text-primary" />
                    <h3 class="text-xl font-bold">Criação de Setlists</h3>
                    <p class="text-gray-500">
                        Crie e manipule seus setlists para diferentes gigs e
                        ocasiões.
                    </p>
                </div>
                <div class="flex flex-col items-center text-center space-y-4">
                    <IconMusic class="h-12 w-12 text-primary" />
                    <h3 class="text-xl font-bold">Gerenciamento das músicas</h3>
                    <p class="text-gray-500">
                        Adicione músicas com detalhes como Tom, Tempo, e até as
                        Notas da música.
                    </p>
                </div>
                <div class="flex flex-col items-center text-center space-y-4">
                    <IconPdf class="h-12 w-12 text-primary" />
                    <h3 class="text-xl font-bold">Exportação de PDF</h3>
                    <p class="text-gray-500">
                        Gere um PDF para o seu repertório com um único clique.
                    </p>
                </div>
                <div class="flex flex-col items-center text-center space-y-4">
                    <IconShare class="h-12 w-12 text-primary" />
                    <h3 class="text-xl font-bold">
                        Colaborativo <strong
                            class="ml-2 font-bold text-sm bg-purple-100 text-purple-600 p-2 rounded-md"
                            >em breve...</strong
                        >
                    </h3>
                    <p class="text-gray-500">
                        Compartilhe seus repertórios com membros da banda ou
                        outras pessoas facilmente.
                    </p>
                </div>
            </div>
        </section>

        <section id="como-funciona" class="w-full px-4 py-12 md:py-24 lg:py-32">
            <h2
                class="text-3xl font-bold tracking-tighter sm:text-5xl text-center mb-12"
            >
                Como Funciona
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="flex flex-col items-center text-center">
                    <div class="rounded-full bg-purple-100 p-3 mb-4">
                        <IconMusic class="h-6 w-6 text-purple-600" />
                    </div>
                    <h3 class="text-xl font-bold mb-2">
                        1. Adicione Suas Músicas
                    </h3>
                    <p class="text-gray-600">
                        Insira suas performances e músicas com informações como tom, link etc.
                    </p>
                </div>
                <div class="flex flex-col items-center text-center">
                    <div class="rounded-full bg-purple-100 p-3 mb-4">
                        <IconChecklist class="h-6 w-6 text-purple-600" />
                    </div>
                    <h3 class="text-xl font-bold mb-2">
                        2. Organize & Gerencie
                    </h3>
                    <p class="text-gray-600">
                        Crie listas e repertórios personalizados e acompanhe sua trajetória
                    </p>
                </div>
                <div class="flex flex-col items-center text-center">
                    <div class="rounded-full bg-purple-100 p-3 mb-4">
                        <IconPdf class="h-6 w-6 text-purple-600" />
                    </div>
                    <h3 class="text-xl font-bold mb-2">
                        3. Exporte e Compartilhe
                    </h3>
                    <p class="text-gray-600">
                        Gere um PDF ou compartilhe seu repertório com outras
                        pessoas.
                    </p>
                </div>
            </div>
        </section>

        <section
            id="acesso-previo"
            class="w-full px-3 py-12 md:py-24 lg:py-32 flex flex-col items-center text-center gap-4 bg-gradient-to-r from-purple-600 to-purple-800"
        >
            <h2
                class="text-3xl font-bold text-white tracking-tighter sm:text-5xl"
            >
                Pronto pra organizar suas músicas?
            </h2>
            <p
                class="max-w-[900px] text-gray-200 text-[0.9rem] md:text-xl/relaxed lg:text-base/relaxed xl:text-xl/relaxed"
            >
                Junte-se a milhares de musicos e musicistas que confiam no
                Repertoire para gerenciar seus setlists.
            </p>
            <form class="flex space-x-2">
                <!-- <input
                    class="max-w-lg flex-1 px-4 py-3 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
                    placeholder="Digite seu email"
                    type="email"
                /> -->
                <a
                    href="/login"
                    class="px-12 py-3 bg-white text-purple-600 rounded-lg font-bold"
                    >Comece Grátis</a
                >
            </form>
            <p class="text-xs text-gray-200">
                Ao enviar, você concorda com nossos Termos de Serviço e
                Políticas de Privacidade
            </p>
        </section>
    </main>

    <footer
        id="footer"
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
