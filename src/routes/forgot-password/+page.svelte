<script>
    import { IconMusic } from "@tabler/icons-svelte";
</script>

<div
    class="absolute inset-0 -z-10 h-full w-full bg-white bg-[linear-gradient(to_right,#f0f0f0_1px,transparent_1px),linear-gradient(to_bottom,#f0f0f0_1px,transparent_1px)] bg-[size:6rem_4rem]"
>
    <div
        class="absolute bottom-0 left-0 right-0 top-0 bg-[radial-gradient(circle_800px_at_100%_200px,#d5c5ff,transparent)]"
    ></div>
</div>

<div class="flex flex-col lg:flex-row min-h-svh lg:min-h-screen w-full items-center justify-center">
    <div class="flex flex-col lg:flex-row items-start justify-center lg:gap-28 w-4/5">
        <div class="w-full lg:w-2/6 flex flex-col items-startlg:items-center justify-center lg:justify-between">
            <a class="flex items-center justify-start" href="/">
                <IconMusic class="h-8 w-8 mr-2" />
                <span class="font-bold text-xl lg:text-xl">Repertoire</span>
            </a>
            <span class="text-xl"><strong class="text-purple-600">Recupere sua senha.</span>
            <a href="/login" class="text-purple-900 font-medium">Digite seu email e enviaremos as instruções para recuperar sua senha.</a>
            <form class="mt-6 flex flex-col gap-4">

                <div class="flex flex-col gap-1">
                    <label for="email" class="text-md text-purple-800 font-medium">Email:</label>
                    <input
                        class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
                        placeholder="Digite seu email aqui"
                        type="email"
                        name="email"
                    />
                </div>

                <button    
                    type="submit"
                    class="px-8 py-2 bg-purple-700 text-white rounded-lg font-bold"
                    >Enviar email
                </button>
            </form>

        </div>
        <div class="w-full lg:w-2/3 mt-8 lg:mt-0">
            <img
                alt="Hero"
                src="https://aiwallpaperarts.com/static/images/wallpapers/original/3026879.jpg"
                class="mx-auto aspect-video overflow-hidden rounded-xl object-cover object-center sm:w-full lg:order-last"
                height="550"
                width="550"
            />
        </div>
    </div>
</div>
