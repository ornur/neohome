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

<nav class="flex">
  <div class="flex w-1/2 mt-8 justify-between items-center">
    <h3 class="text-5xl font-normal text-background">NeoHome</h3>
    <ul class="flex gap-1">
      {#each links as { href, label }}
        <li>
          <a
            {href}
            class="font-medium text-background border border-background backdrop-blur-2xl rounded-4xl px-6 py-2 hover:bg-background hover:text-foreground transition"
            >{label}</a
          >
        </li>
      {/each}
    </ul>
  </div>
  <div class="flex w-1/2 mt-8 items-center justify-end gap-4">
    <ul class="flex gap-1 justify-center w-1/2">
      {#each socialLinks as { href, icon }}
        <li
          class="text-background border border-background rounded-full aspect-square p-2 hover:bg-background hover:text-foreground transition"
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
