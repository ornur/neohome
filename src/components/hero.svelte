<script lang="ts">
  import Icon from "@iconify/svelte";
  import Nav from "./nav.svelte";
  import { onMount } from "svelte";
  import gsap from "gsap";

  let neohomeEl: HTMLParagraphElement;
  let navEl: HTMLDivElement;
  let topTextEl: HTMLDivElement;
  let stats1El: HTMLDivElement;
  let stats2El: HTMLDivElement;
  let buttonEl: HTMLDivElement;

  onMount(() => {
    const tl = gsap.timeline({
      defaults: { duration: 1, ease: "power1.out" },
    });

    // Initial states to prevent FOUC
    gsap.set([neohomeEl, navEl, topTextEl, stats1El, stats2El, buttonEl], {
      autoAlpha: 0,
      scale: 0.8,
    });

    // 1st appearance: NEOHOME
    tl.to(neohomeEl, { autoAlpha: 1, scale: 1 })
      // 2nd appearance: Nav and top text
      .to([navEl, topTextEl], { autoAlpha: 1, scale: 1 }, "-=0.5")
      // 3rd appearance: Stats and button
      .to([stats1El, stats2El, buttonEl], { autoAlpha: 1, scale: 1 }, "-=0.5");
  });
</script>

<section class="m-3 lg:m-4">
  <div
    class="text-background relative mx-auto h-[96vh] max-w-[1920px] rounded-[3rem] bg-[url('/hero-bg.webp')] bg-cover bg-local bg-position-[center_right_-26rem] px-3 lg:rounded-4xl lg:bg-top lg:px-16"
  >
    <!-- Mask for center -->
    <div
      class="absolute inset-0 z-20 hidden scale-100 bg-[url('/hero-bg-mask.png')] bg-cover bg-no-repeat min-[1920px]:block"
    ></div>

    <!-- 2nd appearance animation, nav and bottom texts -->
    <div bind:this={navEl}>
      <Nav />
    </div>
    <!-- top text -->
    <div bind:this={topTextEl} class="flex justify-between py-30 lg:mx-21.5">
      <div class="relative max-w-2xl">
        <p class="text-4xl lg:text-[2.75rem] lg:leading-15">
          <span class="hidden align-middle text-xs lg:block">Since 2018</span>
          REVOLUTIONIZE YOUR LIFE WITH SMART HOME TECHNOLOGY
          <span class="align-middle text-lg lg:hidden">Since 2018</span>
        </p>
        <span class="absolute right-22 bottom-3 hidden w-1/3 text-xs lg:block"
          >We bring ease, security, and fun through intelligent innovations
        </span>
      </div>
      <span class="hidden max-w-24 text-end text-xs lg:block"
        >Experience the future of living</span
      >
    </div>

    <!-- NEOHOME  -->
    <!-- 1st appearance animation only this text -->
    <p
      bind:this={neohomeEl}
      class="absolute inset-0 z-10 mb-2 hidden w-full place-self-center text-center text-[17.6rem] font-semibold opacity-80 lg:block"
    >
      NEOHOME
    </p>

    <!-- 3rd appearance animation, stats and button -->
    <!-- Stats -->
    <div
      bind:this={stats1El}
      class="absolute bottom-4/9 z-30 h-fit max-w-55 rounded-2xl border-t border-l p-5 backdrop-blur-sm lg:top-1/2 lg:right-3/14 lg:max-w-84 lg:p-10"
    >
      <span class="text-4xl">5.5K+</span>
      <p class="text-background/75 text-xs lg:text-base">
        innovative projects successfully completed worldwide.
      </p>
    </div>
    <div
      bind:this={stats2El}
      class="absolute right-3 bottom-2/9 z-30 h-fit max-w-45 rounded-2xl border-t border-l p-5 backdrop-blur-sm lg:top-3/4 lg:right-1/12 lg:max-w-84 lg:p-10"
    >
      <span class="text-4xl">10K+</span>
      <p class="text-background/75 text-xs lg:text-base">
        happy clients enjoying advanced living
      </p>
    </div>

    <!-- Button -->
    <div
      bind:this={buttonEl}
      class="absolute inset-x-0 bottom-12 z-30 mx-auto w-max scale-120 lg:bottom-34 lg:scale-100"
    >
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
  </div>
</section>
