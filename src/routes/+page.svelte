<script lang="ts">
    import Button from "$lib/components/ui/button/button.svelte";
    import { Input } from "$lib/components/ui/input";
  import { invoke } from "@tauri-apps/api/core";

  let name = $state("");
  let greetMsg = $state("");

  let logos = [
    { href: "https://vite.dev", src: "/vite.svg", alt: "Vite Logo", hoverColor: "#747bff" },
    { href: "https://tauri.app", src: "/tauri.svg", alt: "Tauri Logo", hoverColor: "#24c8db" },
    { href: "https://svelte.dev", src: "/svelte.svg", alt: "SvelteKit Logo", hoverColor: "#ff3e00" },
    { href: "https://tailwindcss.com", src: "/tailwind.png", alt: "Tailwind Logo", hoverColor: "#38bdf8" },
    { href: "https://shadcn.com", src: "/shadcn.png", alt: "Shadcn Logo", hoverColor: "#f9ab00" },
    { href: "https://svelte.dev", src: "/android.png", alt: "Android Logo", hoverColor: "#3ddc84" }
  ];

  async function greet(event: Event) {
    event.preventDefault();
    // Learn more about Tauri commands at https://tauri.app/develop/calling-rust/
    greetMsg = await invoke("greet", { name });
  }
</script>

<main class="m-0 pt-[10vh] flex flex-col justify-center text-center font-sans text-base leading-6 font-normal text-gray-900 bg-gray-50 antialiased dark:text-gray-50 dark:bg-gray-800">
  <h1 class="text-center">Welcome to Tauri + Svelte + Tailwind + Shadcn + Android</h1>

  <div class="flex flex-row justify-center items-center flex-wrap">
    {#each logos as logo}
      <a href={logo.href} target="_blank" class="font-medium text-blue-600 hover:text-blue-700 dark:hover:text-cyan-400 p-3">
        <img src={logo.src} class="w-16 h-16 rounded-md object-contain max-w-full max-h-full will-change-[filter] transition-[filter_0.75s] hover:drop-shadow-[0_0_2em_{logo.hoverColor}]" alt={logo.alt} />
      </a>
    {/each}
  </div>
  <p>Click on the Tauri, Vite, and SvelteKit logos to learn more.</p>

  <form class="flex justify-center items-center flex-wrap" onsubmit={greet}>
    <Input placeholder="Enter a name..." bind:value={name} class="w-auto" />
    <Button type="submit" class="ml-2.5">Greet</Button>
  </form>
  <p>{greetMsg}</p>
</main>
