<script lang="ts">
  import Icon from "@iconify/svelte";
  import Nav from "./nav.svelte";
</script>

<section
  class="text-background relative h-[96vh] rounded-4xl bg-[url('/hero-bg.webp')] bg-cover bg-local px-16"
>
  <div
    class="absolute inset-0 -top-8 -left-14 z-20 scale-95 bg-[url('/hero-bg-mask.png')]"
  ></div>
  <Nav />
  <!-- top text -->
  <div class="mx-21.5 my-10 flex justify-between">
    <div class="relative max-w-2xl">
      <p class="text-[2.75rem] leading-15">
        <span class="align-middle text-xs">Since 2018</span>
        REVOLUTIONIZE YOUR LIFE WITH SMART HOME TECHNOLOGY
      </p>
      <span class="absolute right-22 bottom-3 w-1/3 text-xs"
        >We bring ease, security, and fun through intelligent innovations
      </span>
    </div>
    <span class="max-w-24 text-end text-xs"
      >Experience the future of living</span
    >
  </div>

  <!-- NEOHOME -->
  <p
    class="absolute inset-0 z-10 mb-2 w-full place-self-center text-center text-[17.6rem] font-semibold opacity-80"
  >
    NEOHOME
  </p>

  <!-- Stats -->
  <div
    class="absolute top-1/2 right-3/14 z-30 max-w-84 rounded-2xl border-t border-l p-10 backdrop-blur-sm"
  >
    <span class="text-4xl">5.5K+</span>
    <p class="text-base text-gray-400">
      innovative projects successfully completed worldwide.
    </p>
  </div>
  <div
    class="absolute top-3/4 right-1/12 z-30 max-w-84 rounded-2xl border-t border-l p-10 backdrop-blur-sm"
  >
    <span class="text-4xl">10K+</span>
    <p class="text-base text-gray-400">
      happy clients enjoying advanced living
    </p>
  </div>

  <!-- Button -->
  <div class="absolute inset-x-0 bottom-34 z-30 mx-auto w-max">
    <button
      class="bg-background text-foreground flex cursor-pointer items-center gap-2 rounded-4xl px-4 py-2 uppercase transition-transform hover:scale-110"
      >discover more
      <Icon
        icon="mdi:arrow-top-right"
        width="44"
        height="44"
        class="bg-foreground text-background -my-1 -mr-3 ml-2 rounded-full p-2"
      />
    </button>
  </div>
</section>
