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
            <span class="text-xl">Cadastre-se no Repertoire!</span>
            <a href="/login" class="text-purple-900 font-medium">Caso já tenha uma conta, faça seu login por aqui.</a>
            <form class="mt-6 flex flex-col gap-3">

                <div class="flex flex-col gap-1">
                    <label for="name" class="text-md text-purple-800 font-medium">Nome:</label>
                    <input
                        class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
                        placeholder="Digite seu nome"
                        type="text"
                        name="name"
                    />
                </div>
                <div class="flex flex-col gap-1">
                    <label for="email" class="text-md text-purple-800 font-medium">Email:</label>
                    <input
                        class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
                        placeholder="Digite seu email"
                        type="email"
                        name="email"
                    />
                </div>
                <div class="flex flex-col gap-1">
                    <label for="password" class="text-md text-purple-800 font-medium">Senha:</label>
                    <input
                        class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
                        placeholder="Digite sua senha"
                        type="password"
                        name="password"
                    />
                </div>

                <button    
                    type="submit"
                    class="px-8 py-2 bg-purple-700 text-white rounded-lg font-bold"
                    >Cadastrar
                </button>
            </form>

        </div>
        <div class="w-full lg:w-2/3 mt-8 lg:mt-0">
            <img
                alt="Hero"
                src="https://img.freepik.com/free-photo/full-shot-ninja-wearing-equipment_23-2150960878.jpg?t=st=1731701555~exp=1731705155~hmac=dba1f8bcdb706d8d07eb6e28de96722c304a33aae8bde6547010dc4f84df2b0d"
                class="mx-auto aspect-video overflow-hidden rounded-xl object-cover object-center sm:w-full lg:order-last"
                height="550"
                width="550"
            />
        </div>
    </div>
</div>
