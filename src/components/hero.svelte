<script lang="ts">
  import Icon from "@iconify/svelte";
  import Nav from "./nav.svelte";
</script>

<main
  class="relative bg-[url('/hero-bg.webp')] rounded-4xl bg-cover h-[96vh] text-background px-16 bg-local"
>
  <div class="bg-[url('/hero-bg-mask.png')] absolute z-20 -top-7 -left-14 inset-0 scale-95"></div>
  <Nav />
  <!-- top text -->
  <div class="mx-21.5 my-10 flex justify-between">
    <div class="relative max-w-2xl">
      <p class="text-[2.75rem] leading-15">
        <span class="text-xs align-middle">Since 2018</span>
        REVOLUTIONIZE YOUR LIFE WITH SMART HOME TECHNOLOGY
      </p>
      <span class="text-xs absolute right-22 bottom-3 w-1/3"
        >We bring ease, security, and fun through intelligent innovations
      </span>
    </div>
    <span class="max-w-24 text-xs text-end"
      >Experience the future of living</span
    >
  </div>

  <!-- NEOHOME -->
  <p
    class="absolute z-10 text-[17.6rem] font-semibold w-full inset-0 text-center mb-2 place-self-center opacity-80"
  >
    NEOHOME
  </p>

  <!-- Stats -->
  <div
    class="p-10 backdrop-blur-sm z-30 border-t border-l max-w-84 absolute top-1/2 right-3/14 rounded-2xl"
  >
    <span class="text-4xl">5.5K+</span>
    <p class="text-base text-gray-400">
      innovative projects successfully completed worldwide.
    </p>
  </div>
  <div
    class="p-10 backdrop-blur-sm z-30 border-t border-l max-w-84 absolute top-3/4 right-1/12 rounded-2xl"
  >
    <span class="text-4xl">10K+</span>
    <p class="text-base text-gray-400">happy clients enjoying advanced living</p>
  </div>

  <!-- Button -->
  <div class="absolute inset-x-0 z-30 bottom-34 mx-auto w-max">
    <button
      class="bg-background flex items-center gap-2 cursor-pointer hover:scale-110 transition-transform text-foreground uppercase rounded-4xl px-4 py-2"
      >discover more
      <Icon
        icon="mdi:arrow-top-right"
        width="44"
        height="44"
        class="-my-1 -mr-3 ml-2 bg-foreground p-2 text-background rounded-full"
      />
    </button>
  </div>
</main>
