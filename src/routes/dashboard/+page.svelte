<script>
  import { goto } from "$app/navigation";
  import DashHeader from "$lib/DashHeader.svelte";
  import { IconPlus, IconTrash, IconX } from "@tabler/icons-svelte";
  import { onMount } from "svelte";

  let localUser = JSON.parse(localStorage.getItem("user") || {});
  let repertoires = [];
  let selectedRepertoire = null;

  let showCreateModal = false;
  let showRepertoireModal = false;
  let showCreateMusicModal = false;

  let tunes = [
    "C",
    "C#",
    "D",
    "D#",
    "E",
    "F",
    "F#",
    "G",
    "G#",
    "A",
    "A#",
    "B",
    "Cm",
    "C#m",
    "Dm",
    "D#m",
    "Em",
    "Fm",
    "F#m",
    "Gm",
    "G#m",
    "Am",
    "A#m",
    "Bm",
  ];

  onMount(() => {
    fetchRepertories();
  });

  function formatDate(dateString) {
    const date = new Date(dateString);
    return date.toLocaleString("pt-BR", {
      day: "2-digit",
      month: "long",
      year: "numeric",
      hour: "2-digit",
      minute: "2-digit",
    });
  }

  async function fetchRepertories() {
    let token = localStorage.getItem("authToken");

    try {
      const response = await fetch(
        `https://repertoire-api.fly.dev/repertoires/`,
        {
          method: "GET",
          headers: {
            "Content-Type": "application/json",
            Authorization: `${token}`,
          },
        }
      );

      if (!response.ok) {
        throw new Error("Não conseguimos trazer seus repertórios.");
      }

      repertoires = await response.json();
    } catch (error) {
      console.error("Erro ao trazer repertórios", error.message);
      alert(error.message);
    }
  }

  async function openRepertoireModal(id) {
    let token = localStorage.getItem("authToken");

    try {
      const response = await fetch(
        `https://repertoire-api.fly.dev/repertoire/${id}`,
        {
          method: "GET",
          headers: {
            "Content-Type": "application/json",
            Authorization: `${token}`,
          },
        }
      );

      if (!response.ok) {
        throw new Error("Não conseguimos trazer seu repertório.");
      }

      selectedRepertoire = await response.json();
      showRepertoireModal = true;
    } catch (error) {
      console.error("Erro ao trazer repertórios", error.message);
      alert(error.message);
    }
  }

  let title = "";
  let band = "";
  async function createRepertoire(event) {
    event.preventDefault();

    let token = localStorage.getItem("authToken");

    try {
      const response = await fetch(
        "https://repertoire-api.fly.dev/repertoire",
        {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Authorization: `${token}`,
          },
          body: JSON.stringify({ title, band }),
        }
      );

      if (!response.ok) {
        throw new Error("Não conseguimos criar seu repertório");
      }

      const data = await response.json();
      showCreateModal = false;
      fetchRepertories();
      alert("Repertório criado com sucesso!");
    } catch (error) {
      console.error("Erro ao criar:", error.message);
      // Display error message to the user
      alert(`Não conseguimos criar o seu repertório: ${error.message}`);
    }
  }

  async function deleteRepertoire(id) {
    let token = localStorage.getItem("authToken");

    try {
      const response = await fetch(
        `https://repertoire-api.fly.dev/repertoire/${id}`,
        {
          method: "DELETE",
          headers: {
            "Content-Type": "application/json",
            Authorization: `${token}`,
          },
        }
      );

      console.log(token);
      if (!response.ok) {
        throw new Error(`Erro na requisição: ${response.status}`);
      }

      const data = await response.json();

      closeRepertoireModal();
      fetchRepertories();
      alert("Repertório deletado com sucesso!");
    } catch (error) {
      console.error("Erro ao deletar:", error.message);
      alert(`Catch error: ${error.message}`);
    }
  }

  function closeRepertoireModal() {
    showRepertoireModal = false;
    selectedRepertoire = null;
  }

  let name = "";
  let tune = "";
  let link = "";
  async function createMusic(event) {
    event.preventDefault();

    let token = localStorage.getItem("authToken");
    let repertoire_id = selectedRepertoire.repertoire.id;

    try {
      const response = await fetch("https://repertoire-api.fly.dev/music", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          Authorization: `${token}`,
        },
        body: JSON.stringify({ name, tune, link, repertoire_id }),
      });

      if (!response.ok) {
        throw new Error("Não conseguimos criar sua música");
      }

      const data = await response.json();
      showCreateMusicModal = false;
      fetchRepertories();
      openRepertoireModal(repertoire_id);
    } catch (error) {
      console.error("Erro ao criar:", error.message);
      // Display error message to the user
      alert(`Não conseguimos criar sua musica: ${error.message}`);
    }
  }

  async function deleteMusic(id) {
    let token = localStorage.getItem("authToken");

    try {
      const response = await fetch(
        `https://repertoire-api.fly.dev/music/${id}`,
        {
          method: "DELETE",
          headers: {
            "Content-Type": "application/json",
            Authorization: `${token}`,
          },
        }
      );

      console.log(token);
      if (!response.ok) {
        throw new Error(`Erro na requisição: ${response.status}`);
      }

      const data = await response.json();

      fetchRepertories();
      openRepertoireModal(selectedRepertoire.repertoire.id);
    } catch (error) {
      console.error("Erro ao deletar:", error.message);
      alert(`Catch error: ${error.message}`);
    }
  }
</script>

<DashHeader name={localUser.name} />
<section class="p-4 lg:p-6">
  {#if repertoires.length === 0}
  <div class="flex items-center justify-between">
      <h1 class="text-xl lg:text-3xl">Nenhum repertório por aqui ainda...</h1>
      <button
        onclick={() => (showCreateModal = true)}
        class="mt-4 flex gap-1 items-center bg-green-700 text-white px-4 py-2 rounded"
        >Novo repertório <IconPlus /></button
      >
    </div>
  {:else}
    <div class="flex items-center justify-between">
      <h1 class="text-xl lg:text-3xl">Seus Repertórios</h1>
      <button
        onclick={() => (showCreateModal = true)}
        class="mt-4 flex gap-1 items-center bg-green-700 text-white px-4 py-2 rounded"
        >Novo repertório <IconPlus /></button
      >
    </div>
    <div class="mt-4 flex flex-wrap gap-4">
      {#each repertoires as rep}
        <button
          onclick={() => openRepertoireModal(rep.id)}
          class="p-4 w-min-4/5 h-36 lg:w-min-40 lg:h-48 flex flex-col items-start text-lg border-2 border-gray-200 rounded-lg"
        >
          <div class="flex w-full items-center justify-between">
            <h2 class="text-xl lg:text-2xl text-start font-normal">
              {rep.title}
            </h2>
          </div>
          <div class="flex flex-col items-start leading-4 mt-2 text-zinc-700">
            <h3>{rep.band}</h3>
            <h3>{rep.show}</h3>
          </div>
          <span
            class="text-sm font-sans text-gray-500 self-end justify-self-end mt-auto"
            >{formatDate(rep.updated_at)}</span
          >
        </button>
      {/each}
    </div>
  {/if}
</section>

{#if showRepertoireModal}
  <div
    class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center"
  >
    <div class="bg-white px-8 py-4 lg:rounded-lg lg:shadow-lg w-full lg:w-2/3">
      <nav class="flex items-start justify-between">
        <div class="flex flex-col items-start">
          <h2 class="text-2xl font-semibold">
            {selectedRepertoire.repertoire.title}
          </h2>
          <div
            class="flex flex-col items-start justify-start leading-4 text-zinc-700"
          >
            <p>{selectedRepertoire.repertoire.band}</p>
            <p>{selectedRepertoire.repertoire.show}</p>
          </div>
        </div>
        <div class="flex items-center justify-center gap-2">
          <button
            onclick={() => deleteRepertoire(selectedRepertoire.repertoire.id)}
            aria-label="Delete"
          >
            <IconTrash color="#b91c1c" size="28" />
          </button>
          <button
            onclick={() => closeRepertoireModal()}
            class="bg-red-700 text-white px-2 py-2 rounded"
          >
            <IconX />
          </button>
        </div>
      </nav>

      {#if selectedRepertoire.musics.length === 0}
        <button
          onclick={() => (showCreateMusicModal = true)}
          class="mt-1 text-gray-500"
          aria-label="Nova música">Nova música...</button
        >
      {:else}
        <div class="my-4 flex flex-col items-start">
          <ul class="list-disc">
            {#each selectedRepertoire.musics as music}
              <li class="flex gap-2 items-center justify-between">
                <a href={music.link} target="_blank" class="text-zinc-800">
                  {music.name} - {music.tune}
                </a>
                <button
                  onclick={() => deleteMusic(music.id)}
                  aria-label="Delete"
                >
                  <IconTrash color="#b91c1c" size="18" />
                </button>
              </li>
            {/each}
          </ul>
          <button
            onclick={() => (showCreateMusicModal = true)}
            class="mt-1 text-gray-500"
            aria-label="Nova música">Nova música...</button
          >
        </div>
      {/if}

      <p class="font-sans text-sm text-gray-500">
        {formatDate(selectedRepertoire.repertoire.updated_at)}
      </p>
    </div>
  </div>
{/if}

{#if showCreateModal}
  <div
    class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center"
  >
    <div class="bg-white px-8 py-4 rounded-lg shadow-lg w-full lg:w-1/3">
      <div class="flex items-center justify-between w-full">
        <h2 class="text-2xl">Novo Repertório</h2>
        <button
          onclick={() => (showCreateModal = false)}
          class="mt-4 bg-red-700 text-white px-4 py-2 rounded"
          aria-label="Fechar"
        >
          <IconX />
        </button>
      </div>
      <form onsubmit={createRepertoire} class="mt-6 flex flex-col gap-4">
        <div class="flex flex-col gap-1">
          <label for="title" class="text-md text-green-800 font-medium"
            >Título:</label
          >
          <input
            class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
            placeholder="ex: Simplesmente Roupa Nova"
            type="text"
            name="title"
            bind:value={title}
            required
          />
        </div>
        <div class="flex flex-col gap-1">
          <label for="band" class="text-md text-green-800 font-medium"
            >Banda:</label
          >
          <input
            class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
            placeholder="ex: Banda O Disco"
            type="text"
            name="band"
            bind:value={band}
            required
          />
        </div>

        <button
          type="submit"
          class="px-8 py-2 bg-green-700 text-white rounded-lg font-bold"
          >Criar Repertório
        </button>
      </form>
    </div>
  </div>
{/if}

{#if showCreateMusicModal}
  <div
    class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center"
  >
    <div class="bg-white px-8 py-4 rounded-lg shadow-lg w-full lg:w-1/3">
      <div class="flex items-center justify-between w-full">
        <h2 class="text-2xl">Nova Música</h2>
        <button
          onclick={() => (showCreateMusicModal = false)}
          class="mt-4 bg-red-700 text-white px-4 py-2 rounded"
          aria-label="Fechar"
        >
          <IconX />
        </button>
      </div>
      <form onsubmit={createMusic} class="mt-6 flex flex-col gap-4">
        <div class="flex flex-col gap-1">
          <label for="name" class="text-md text-green-800 font-medium"
            >Nome:</label
          >
          <input
            class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
            placeholder="ex: Simplesmente Roupa Nova"
            type="text"
            name="name"
            bind:value={name}
            required
          />
        </div>
        <div class="flex flex-col gap-1">
          <label for="tune" class="text-md text-green-800 font-medium"
            >Tom:</label
          >
          <select
            class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
            name="tune"
            bind:value={tune}
            required
          >
            {#each tunes as tune}
              <option value={tune}>{tune}</option>
            {/each}
          </select>
        </div>
        <div class="flex flex-col gap-1">
          <label for="link" class="text-md text-green-800 font-medium"
            >Link para escutar a música:</label
          >
          <input
            class="max-w-full flex-1 px-4 py-2 bg-white text-zinc-900 border border-zinc-300 rounded-lg outline-none"
            placeholder="ex: linka O Disco"
            type="text"
            name="link"
            bind:value={link}
            required
          />
        </div>

        <button
          type="submit"
          class="px-8 py-2 bg-green-700 text-white rounded-lg font-bold"
          >Criar Música
        </button>
      </form>
    </div>
  </div>
{/if}
