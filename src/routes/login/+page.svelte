<script>
    import { enhance } from "$app/forms";
    import { goto } from "$app/navigation";
    import { IconMusic } from "@tabler/icons-svelte";

    let email = $state("");
    let password = $state("");

    async function handleSubmit(event) {
        // Impede o comportamento padrão do formulário
        event.preventDefault();

        // console.log(JSON.stringify({user: { email, password }})); // Debug para verificar os valores
        try {
            const response = await fetch(
                "http://repertoire-api.fly.dev/login",
                {
                    method: "POST",
                    body: JSON.stringify({
                        user: {
                            email,
                            password,
                        },
                    }),
                    headers: { "Content-Type": "application/json" },
                },
            );

            if (!response.ok) {
                throw new Error(
                    "Login failed. Please check your email and password.",
                );
            }

            const loginData = await response.json();
            const authHeader = response.headers.get("Authorization");
            console.log(loginData.message, authHeader);

            if (authHeader && authHeader.startsWith("Bearer ")) {
                // Armazenar o token e os dados do usuário no LocalStorage
                localStorage.setItem("authToken", authHeader);
                localStorage.setItem(
                    "user",
                    JSON.stringify(loginData.data.user),
                );

                alert("Entrou com sucesso!");
                goto("/dashboard");
            } else {
                throw new Error("Token de autenticação não encontrado.");
            }
        } catch (error) {
            console.error("Login error:", error.message);
            // Display error message to the user
            alert(error.message);
        }
    }
</script>

<div
    class="absolute inset-0 -z-10 h-full w-full bg-white bg-[linear-gradient(to_right,#f0f0f0_1px,transparent_1px),linear-gradient(to_bottom,#f0f0f0_1px,transparent_1px)] bg-[size:6rem_4rem]"
>
    <div
        class="absolute bottom-0 left-0 right-0 top-0 bg-[radial-gradient(circle_800px_at_100%_200px,#d5c5ff,transparent)]"
    ></div>
</div>

<div
    class="flex flex-col lg:flex-row min-h-svh lg:min-h-screen w-full items-center justify-center"
>
    <div
        class="flex flex-col lg:flex-row items-start justify-center lg:gap-28 w-4/5"
    >
        <div
            class="w-full lg:w-2/6 flex flex-col items-startlg:items-center justify-center lg:justify-between"
        >
            <a class="flex items-center justify-start" href="/">
                <IconMusic class="h-8 w-8 mr-2" />
                <span class="font-bold text-xl lg:text-xl">Repertoire</span>
            </a>
            <span class="text-xl"
                ><strong class="text-purple-600">Olá!</strong> Entre na sua conta.</span
            >
            <a href="/signup" class="text-purple-900 font-medium"
                >Não tem uma conta ainda? Crie agora.</a
            >

            <form on:submit={handleSubmit} class="mt-6 flex flex-col gap-4">
                <div class="flex flex-col gap-1">
                    <label
                        for="email"
                        class="text-md text-purple-800 font-medium"
                        >Email:</label
                    >
                    <input
                        class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
                        placeholder="Digite seu email"
                        type="email"
                        name="email"
                        bind:value={email}
                        required
                    />
                </div>
                <div class="flex flex-col gap-1">
                    <label
                        for="password"
                        class="text-md text-purple-800 font-medium"
                        >Senha:</label
                    >
                    <input
                        class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
                        placeholder="Digite sua senha"
                        type="password"
                        name="password"
                        bind:value={password}
                        required
                    />
                </div>

                <button
                    type="submit"
                    class="px-8 py-2 bg-purple-700 text-white rounded-lg font-bold"
                    >Entrar
                </button>
            </form>
            <a href="/forgot-password" class="text-purple-700 font-medium"
                >Esqueceu a senha?</a
            >
        </div>
        <div class="w-full lg:w-2/3 mt-8 lg:mt-0">
            <img
                alt="Hero"
                src="https://image.cdn2.seaart.me/2023-11-08/22128187776449541/458ab5ce4d6312eab68799b824ba4f2642e50c0a_high.webp"
                class="mx-auto aspect-video overflow-hidden rounded-xl object-cover object-center sm:w-full lg:order-last"
                height="550"
                width="550"
            />
        </div>
    </div>
</div>
