<script>
  import Icon from "@iconify/svelte";
  import { SERVICES } from "../constants/services.constants";
  import { cn } from "../lib/utils";

  let selectedService = $state("smart lighting");
</script>

<section class="bg-foreground text-background lg:p-20">
  <div class="mx-auto flex max-w-[1920px] gap-10">
    <!-- Left side with buttons -->
    <div class="mt-16 flex w-1/3 flex-col items-start justify-between">
      <!-- Heading and description -->
      <div class="space-y-5">
        <h3 class="text-background inline-block text-6xl uppercase">
          the solutions we offer
        </h3>
        <p class="w-[25vw] text-sm text-slate-300/60">
          From installation to setup and support, we ensure your home is
          equipped with the latest technology, working smoothly and effortlessly
          - just the way you want it.
        </p>
      </div>
      <!-- Buttons for each service -->
      <div class="flex flex-col gap-4">
        {#each SERVICES as service, i}
          <button
            class={`cursor-pointer text-start`}
            onclick={() => (selectedService = service.name)}
          >
            <p
              class={cn(
                "text-2xl uppercase",
                selectedService === service.name && "text-secondary",
              )}
            >
              <span class="mr-10">{i < 10 ? `0${i + 1}` : i + 1}</span>
              {service.name}
            </p>
          </button>
        {/each}
      </div>
      <!-- Learn more button -->
      <button
        class="bg-background text-foreground flex w-max scale-110 cursor-pointer items-center gap-2 rounded-4xl px-4 py-2 uppercase transition-transform hover:scale-110 lg:scale-100"
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

    <!-- Image with descriptions -->
    <div
      class="relative aspect-7/5 w-full rounded-3xl bg-[url('/services/services-photo.webp')] bg-cover bg-center"
    >
      <span class="absolute top-10 right-10 text-end text-xs opacity-90"
        >Our services are tailored <br /> to fit your lifestyle</span
      >
      <span class="absolute bottom-10 left-10 text-xs opacity-90"
        >We are ready to simplify <br /> your life and enhance <br /> your living
        experience</span
      >
      {#each SERVICES as service}
        <div
          class={cn(
            "absolute max-w-88 rounded-4xl border-t border-r border-white text-start backdrop-blur-md transition-all duration-300",
            service.classAbsolute,
            selectedService === service.name ? "p-6" : "px-8 py-2 text-center",
          )}
        >
          <h3
            class={cn(
              "mb-2",
              selectedService === service.name
                ? "text-2xl uppercase"
                : "text-sm capitalize",
            )}
          >
            {service.name}
          </h3>
          <p
            class={cn(
              "text-xs opacity-80",
              selectedService === service.name ? "block" : "hidden",
            )}
          >
            {service.description}
          </p>
          <a
            href={service.link}
            class={cn(
              "mt-4 inline-block text-sm underline",
              selectedService === service.name ? "block" : "hidden",
            )}
          >
            Learn More...
          </a>
          <span
            class={cn(
              "top-11 h-20 rounded-bl-3xl border-b border-l border-white bg-transparent",
              service.classLine,
              selectedService === service.name ? "hidden" : "absolute",
            )}
          ></span>
        </div>
      {/each}
    </div>
  </div>
</section>
