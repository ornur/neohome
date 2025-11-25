<script lang="ts">
  import Icon from "@iconify/svelte";
  import { features } from "../constants/features.constants";
  import gsap from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";
  import { onMount } from "svelte";

  gsap.registerPlugin(ScrollTrigger);

  let headerTextEl: HTMLHeadingElement;
  let rightTextEl: HTMLDivElement;
  let bottomTextEl: HTMLParagraphElement;

  onMount(() => {
    const tl = gsap.timeline({
      scrollTrigger: {
        trigger: headerTextEl,
        start: "top 80%",
      },
      defaults: { duration: 1, ease: "power2.out" },
    });

    // Initial states for header
    gsap.set([headerTextEl, rightTextEl], { autoAlpha: 0 });
    gsap.set(headerTextEl, { x: -100 });
    gsap.set(rightTextEl, { x: 100 });

    tl.to(headerTextEl, { x: 0, autoAlpha: 1 }).to(
      rightTextEl,
      { x: 0, autoAlpha: 1 },
      "-=0.8",
    );

    // Animate feature items and photo individually
    const items: HTMLElement[] = gsap.utils.toArray(
      ".feature-item, .feature-photo",
    );

    items.forEach((item) => {
      gsap.fromTo(
        item,
        { autoAlpha: 0, y: 50 },
        {
          autoAlpha: 1,
          y: 0,
          duration: 1,
          ease: "power2.out",
          scrollTrigger: {
            trigger: item,
            start: "top 85%",
          },
        },
      );
    });

    // Animate bottom text
    gsap.fromTo(
      bottomTextEl,
      { autoAlpha: 0, y: -50 },
      {
        autoAlpha: 1,
        y: 0,
        duration: 1,
        ease: "power2.out",
        scrollTrigger: {
          trigger: bottomTextEl,
          start: "top 85%",
        },
      },
    );
  });
</script>

<section class="mx-auto mt-40 max-w-[1760px] px-3 lg:mb-20 lg:px-0">
  <!-- Header top texts -->
  <div
    class="flex flex-col-reverse items-end justify-between gap-30 lg:flex-row lg:gap-0"
  >
    <h3
      bind:this={headerTextEl}
      class="text-[2.5rem] leading-12 lg:w-1/3 lg:text-[3.5rem] lg:leading-16"
    >
      THE KEY BENEFITS OF SMART LIVING
    </h3>
    <div
      bind:this={rightTextEl}
      class="flex flex-col items-end justify-end text-2xl lg:w-1/3 lg:text-[2.1rem] lg:leading-10"
    >
      <p class="w-fit">
        IMAGINE <span class="text-secondary italic">A HOME THAT</span> IS SO IN TUNE
        WITH YOU.
      </p>
      <p class="place-self-end text-end">
        IT <span class="text-secondary italic">KNOWS YOUR NEEDS</span> BEFORE YOU
        DO
      </p>
    </div>
  </div>

  <!-- List texts and photo -->
  <div class="text-background mt-14 lg:my-20 lg:flex lg:gap-16">
    <!-- List texts -->
    <div class="text-foreground lg:w-3/5">
      <ul
        class="divide-y-2 divide-gray-300 border-gray-300 first:border-t-2 last:border-b-2"
      >
        {#each features as feature, i}
          <li
            class="feature-item items-center justify-between space-y-2 py-12 lg:flex"
          >
            <div class="inline-flex gap-7 lg:gap-14">
              <span class="text-secondary text-3xl lg:text-4xl">0{i + 1}</span>
              <h3 class="text-2xl text-nowrap lg:text-[2.4rem] lg:leading-10">
                {feature.title}
              </h3>
            </div>
            <p
              class="ml-17 w-80 text-sm text-gray-400 lg:ml-0 lg:justify-self-end lg:text-justify"
            >
              {feature.description}
            </p>
          </li>
        {/each}
      </ul>
    </div>

    <!-- Photo -->
    <div
      class="feature-photo mt-20 flex aspect-3/4 items-end justify-end rounded-[2.5rem] bg-[url('/features/features-photo.webp')] bg-cover bg-center p-4 lg:mt-0 lg:aspect-3/5 lg:w-2/5 lg:justify-between lg:rounded-4xl lg:p-8"
    >
      <!-- Stats -->
      <div class="hidden flex-col gap-4 lg:flex">
        <div
          class="z-30 max-w-84 space-y-3 rounded-3xl p-10 text-center shadow-[1px_-1px_0.01px_rgba(0,0,0,0.25)] shadow-amber-50 backdrop-blur-md transition-all delay-150 duration-300 hover:scale-105 hover:backdrop-blur-xl"
        >
          <p class="uppercase">Energy savings</p>
          <span class="text-4xl">20%</span>
        </div>
        <div
          class="z-30 max-w-84 space-y-3 rounded-3xl p-10 text-center shadow-[1px_-1px_0.01px_rgba(0,0,0,0.25)] shadow-amber-50 backdrop-blur-md transition-all delay-150 duration-300 hover:scale-105 hover:backdrop-blur-xl"
        >
          <p class="uppercase">Home Security</p>
          <span class="text-4xl">24/7</span>
        </div>
        <div
          class="z-30 max-w-84 space-y-3 rounded-3xl p-10 text-center shadow-[1px_-1px_0.01px_rgba(0,0,0,0.25)] shadow-amber-50 backdrop-blur-md transition-all delay-150 duration-300 hover:scale-105 hover:backdrop-blur-xl"
        >
          <p class="uppercase">Cost Saved</p>
          <span class="text-4xl">15%</span>
        </div>
      </div>

      <!-- Button learn more -->
      <div class="mr-2 flex w-56 flex-col justify-end gap-4 lg:mr-0">
        <h3 class="text-end text-xl uppercase">
          do you want to know more pros?
        </h3>
        <button
          class="bg-background text-foreground flex w-max scale-110 cursor-pointer items-center gap-2 place-self-end rounded-4xl px-4 py-2 uppercase transition-transform hover:scale-110 lg:scale-100"
        >
          learn more
          <Icon
            icon="mdi:arrow-top-right"
            width="44"
            height="44"
            class="bg-foreground text-background -my-1 -mr-3 ml-2 rounded-full p-2"
          />
        </button>
      </div>
    </div>
  </div>

  <!-- Bottom texts with images -->
  <div class="mt-40 hidden lg:block">
    <h3 class="text-center text-2xl text-gray-400">NeoHome</h3>
    <p
      class="my-10 text-center text-xl leading-24 lg:text-7xl"
      bind:this={bottomTextEl}
    >
      <span
        class="mr-5 rounded-xl bg-[url('/features/1.webp')] bg-cover bg-position-[center_top_-3.5rem] px-22"
      ></span>
      A <span class="text-secondary">SMART HOME</span> ADAPTS TO YOU!
      <span
        class="ml-5 rounded-xl bg-[url('/features/2.webp')] bg-cover bg-position-[center_top_rem] px-22"
      ></span>
      EFFORTLESS
      <span class="text-secondary">COMFORT</span>,
      <span
        class="mx-5 rounded-xl bg-[url('/features/3.webp')] bg-cover bg-position-[center_top_-2rem] px-24"
      ></span>
      <span class="text-secondary">SECURITY</span>, <br />
      AND
      <span
        class="mx-5 rounded-xl bg-[url('/features/4.webp')] bg-cover bg-position-[center_top_-2rem] px-24"
      ></span>
      <span class="text-secondary">EFFICIENCY</span>
      - PERFECTLY AND <br />
      <span
        class="mx-5 rounded-xl bg-[url('/features/5.webp')] bg-cover bg-position-[center_top_-4rem] px-24"
      ></span>
      SEAMLESSLY
      <span
        class="mx-5 rounded-xl bg-[url('/features/6.webp')] bg-cover bg-position-[center_top_-1rem] px-24"
      ></span>
      CONNECTED
      <span
        class="mx-5 rounded-xl bg-[url('/features/7.webp')] bg-cover bg-position-[center_top_-1rem] px-24"
      ></span>
    </p>
    <h3 class="text-center text-xl text-gray-300">We build homes that think</h3>
  </div>
</section>
