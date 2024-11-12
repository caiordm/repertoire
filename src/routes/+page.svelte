<script>
    import { IconMusic, IconList, IconShare } from "@tabler/icons-svelte";
</script>

<main class="flex flex-col items-center">
    <section class="w-full px-4 lg:px-8 py-12 md:py-14 lg:py-24 xl:py-28">
        <div
            class="grid gap-6 lg:grid-cols-[1fr_400px] lg:gap-12 xl:grid-cols-[1fr_600px]"
        >
            <div class="flex flex-col justify-center space-y-4">
                <div class="space-y-2">
                    <h1
                        class="text-3xl font-bold tracking-tighter sm:text-5xl xl:text-6xl/none"
                    >
                        Organize seu repertório musical com facilidade
                    </h1>
                    <p class="max-w-[600px] text-gray-500 md:text-xl">
                        Crie, organize e compartilhe seus setlists sem muito esforço. Perfeito para bandas, artistas solos e entusiastas.
                    </p>
                </div>
                <div class="flex flex-col gap-2 min-[400px]:flex-row">
                    <button class="px-4 py-3 bg-zinc-900 text-white rounded-md"
                        >Comece Grátis</button
                    >
                    <button
                        class="px-4 py-3 bg-white text-zinc-900 border border-zinc-300 rounded-md"
                    >
                        Saiba Mais
                    </button>
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
    <section id="funcionalidades" class="w-full px-2 py-12 md:py-24 lg:py-32 bg-gray-100">
        <h2
            class="text-3xl font-bold tracking-tighter sm:text-5xl text-center mb-12"
        >
            Principais Funcionalidades
        </h2>
        <div class="grid gap-6 lg:grid-cols-3">
            <div class="flex flex-col items-center text-center space-y-4">
                <IconList class="h-12 w-12 text-primary" />
                <h3 class="text-xl font-bold">Criação de Setlists</h3>
                <p class="text-gray-500">
                    Crie e manipule seus setlists para diferentes gigs e ocasiões.
                </p>
            </div>
            <div class="flex flex-col items-center text-center space-y-4">
                <IconMusic class="h-12 w-12 text-primary" />
                <h3 class="text-xl font-bold">Gerenciamento das músicas</h3>
                <p class="text-gray-500">
                    Adicione músicas com detalhes como Tom, Tempo, e até as Notas da música.
                </p>
            </div>
            <div class="flex flex-col items-center text-center space-y-4">
                <IconShare class="h-12 w-12 text-primary" />
                <h3 class="text-xl font-bold">Colaborativo</h3>
                <p class="text-gray-500">
                    Compartilhe seus repertórios com membros da banda ou outras pessoas facilmente.
                </p>
            </div>
        </div>
    </section>
    <section
        class="w-11/12 lg:w-full py-12 md:py-24 lg:py-32 flex flex-col items-center text-center gap-4"
    >
        <h2 class="text-3xl font-bold tracking-tighter sm:text-5xl">
            Pronto pra organizar suas músicas?
        </h2>
        <p
            class="max-w-[900px] text-gray-500 md:text-xl/relaxed lg:text-base/relaxed xl:text-xl/relaxed"
        >
            Junte-se a milhares de musicos e musicistas que confiam no Repertoire para gerenciar seus setlists.
        </p>
        <form class="flex space-x-2">
            <input
                class="max-w-lg flex-1 px-4 py-3 bg-white text-zinc-900 border border-zinc-300 rounded-md outline-none"
                placeholder="Digite seu email"
                type="email"
            />
            <button
                type="submit"
                class="px-4 py-3 bg-zinc-900 text-white rounded-md"
                >Enviar</button
            >
        </form>
        <p class="text-xs text-gray-500">
            Ao enviar, você concorda com nossos Termos de Serviço e Políticas de Privacidade
        </p>
    </section>
</main>
