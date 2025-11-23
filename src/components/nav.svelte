<script lang="ts">
  import Icon from "@iconify/svelte";

  const links = [
    { href: "", label: "Home" },
    { href: "#features", label: "Features" },
    { href: "#services", label: "Services" },
    { href: "#projects", label: "Projects" },
    { href: "#faq", label: "FAQ" },
  ];
  const socialLinks = [
    { href: "https://instagram.com", icon: "fa6-brands:instagram" },
    { href: "https://facebook.com", icon: "fa6-brands:facebook-f" },
    { href: "https://x.com", icon: "fa6-brands:x-twitter" },
  ];
  const mobileLink = { href: "#home", label: "+1(555)123-4567" };
</script>

<nav class="absolute z-40 flex h-22 w-[86vw] max-w-[1760px] lg:w-[90vw]">
  <div class="flex w-full items-center justify-between lg:mt-8 lg:w-1/2">
    <h3 class="text-background text-[2.5rem] font-normal lg:text-5xl">
      NeoHome
    </h3>
    <Icon
      icon="mdi:menu"
      width="36"
      height="36"
      class="text-background lg:hidden"
    />
    <ul class="hidden gap-1 lg:flex">
      {#each links as { href, label }}
        <li
          class="text-background border-background hover:bg-background hover:text-foreground cursor-pointer rounded-4xl border px-6 py-2 font-medium backdrop-blur-2xl transition"
        >
          <a {href}>{label}</a>
        </li>
      {/each}
    </ul>
  </div>
  <div class="mt-8 hidden w-1/2 items-center justify-end gap-4 lg:flex">
    <ul class="flex w-1/2 justify-center gap-1">
      {#each socialLinks as { href, icon }}
        <li
          class="text-background border-background hover:bg-background hover:text-foreground aspect-square rounded-full border p-2 transition"
        >
          <a {href}>
            <Icon {icon} width="20" height="20" />
          </a>
        </li>
      {/each}
    </ul>
    <a href={mobileLink.href} class="text-background text-4xl"
      >{mobileLink.label}</a
    >
  </div>
</nav>
