<script>
  import { IconLogout, IconMusic } from "@tabler/icons-svelte";
  import { Hamburger } from "svelte-hamburgers";
  import MenuHamburguer from "./MenuHamburguer.svelte";
  import { goto } from "$app/navigation";

  let open = $state(false);
  let { name } = $props();

  let localUser = JSON.parse(localStorage.getItem("user") || {});

  async function logout() {
    let token = localStorage.getItem("authToken");

    if (!token) {
      throw new Error("Usuário não autenticado. Faça login novamente.");
    }
    try {
      const response = await fetch("https://repertoire-api.fly.dev/logout", {
        method: "DELETE",
        headers: {
          "Content-Type": "application/json",
          Authorization: `${token}`,
        },
      });

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
</script>

<header
  class="w-full px-4 lg:px-6 h-16 text-lg flex items-center justify-between border-b-2 border-gray-200"
>
  <span class="text-lg lg:text-xl">Olá, {name}!</span>
  <a class="flex items-center justify-center" href="/">
    <IconMusic class="h-6 w-6 mr-2" />
    <span class="font-bold text-lg lg:text-xl">Repertoire</span>
  </a>
  <button
    onclick={logout}
    class="flex items-center justify-center gap-2 p-4 text-lg text-red-800 font-normal"
    >Sair <IconLogout color="#991b1b" /></button
  >
</header>
