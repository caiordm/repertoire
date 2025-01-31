<script>
    import { goto } from "$app/navigation";

    let localUser = JSON.parse(localStorage.getItem("user") || {});

    async function logout() {
        let token = localStorage.getItem("authToken");

        if (!token) {
            throw new Error("Usuário não autenticado. Faça login novamente.");
        }
        try {
            const response = await fetch(
                "https://repertoire-api.fly.dev/logout",
                {
                    method: "DELETE",
                    headers: {
                        "Content-Type": "application/json",
                        Authorization: `${token}`,
                    },
                },
            );

            if (!response.ok) {
                throw new Error("Falhou");
            }

            const data = await response.json();
            console.log(data.message);

            if (data.message && data.message == "Logged out successfully.") {
                localStorage.removeItem("authToken");
                localStorage.removeItem("user");
                // authToken.set(null);
                // user.set(null);

                alert("Saiu com sucesso!");
                goto("/");
            } else {
                throw new Error("Token de autenticação não encontrado.");
            }
        } catch (error) {
            console.error("Erro ao sair", error.message);
            alert(error.message);
        }
    }

    async function fetchRepertories() {
        let token = localStorage.getItem();
    }
</script>

<h1>Dashboard!!</h1>
<h1>Olá {localUser.name || "Usuário"}</h1>
<button
    on:click={logout}
    class="px-8 py-2 bg-red-800 text-white rounded-xl font-bold"
    >Clique aqui para Sair</button
>
