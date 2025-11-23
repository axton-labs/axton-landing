<script lang="ts">
  import { onMount } from "svelte";
  import { browser } from "$app/environment";
  import { Download, ChevronDown } from "lucide-svelte";
  import Galaxy from "../../components/Galaxy.svelte";
  import { Button } from "../../components/ui/button";
  import * as Card from "../../components/ui/card";
  import gsap from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";

  if (browser) {
    gsap.registerPlugin(ScrollTrigger);
  }

  const scrollToContent = () => {
    const nextSection = document.querySelector("#desktop-section");
    if (nextSection) {
      nextSection.scrollIntoView({ behavior: "smooth" });
    }
  };

  onMount(() => {
    gsap.fromTo(
      ".hero-badge",
      { opacity: 0, y: -20 },
      { opacity: 1, y: 0, duration: 0.6, delay: 0.2, ease: "power2.out" }
    );

    gsap.fromTo(
      ".hero-title",
      { opacity: 0, y: 30 },
      { opacity: 1, y: 0, duration: 0.8, delay: 0.4, ease: "power2.out" }
    );

    gsap.fromTo(
      ".hero-description",
      { opacity: 0, y: 30 },
      { opacity: 1, y: 0, duration: 0.8, delay: 0.6, ease: "power2.out" }
    );

    gsap.fromTo(
      ".scroll-indicator",
      { opacity: 0, y: -10 },
      { opacity: 1, y: 0, duration: 0.8, delay: 1, ease: "power2.out" }
    );

    gsap.to(".scroll-indicator", {
      y: 10,
      duration: 0.8,
      repeat: -1,
      yoyo: true,
      ease: "power1.inOut",
    });

    gsap.utils.toArray(".section-title").forEach((elem: any) => {
      gsap.fromTo(
        elem,
        { opacity: 0, y: 50 },
        {
          opacity: 1,
          y: 0,
          duration: 0.8,
          ease: "power2.out",
          scrollTrigger: {
            trigger: elem,
            start: "top 85%",
          },
        }
      );
    });

    gsap.utils.toArray(".animate-card").forEach((elem: any, index: number) => {
      gsap.fromTo(
        elem,
        { opacity: 0, y: 50 },
        {
          opacity: 1,
          y: 0,
          duration: 0.6,
          delay: index * 0.05,
          ease: "power2.out",
          scrollTrigger: {
            trigger: elem,
            start: "top 85%",
          },
        }
      );
    });

    gsap.fromTo(
      ".support-section",
      { opacity: 0, y: 50 },
      {
        opacity: 1,
        y: 0,
        duration: 1,
        ease: "power2.out",
        scrollTrigger: {
          trigger: ".support-section",
          start: "top 85%",
        },
      }
    );
  });
</script>

<div class="min-h-screen bg-background text-foreground">
  <main>
    <!-- Hero Section -->
    <section class="relative overflow-hidden pt-32 pb-16">
      <div class="absolute inset-0">
        <Galaxy
          hueShift={140}
          density={1}
          mouseRepulsion={true}
          transparent={true}
          saturation={0.4}
          starSpeed={0.4}
          speed={0.1}
        />
      </div>

      <div
        class="bg-background/40 relative z-20 pointer-events-none py-16 md:py-24"
      >
        <div class="container mx-auto px-4">
          <div class="max-w-4xl mx-auto text-center">
            <div
              class="hero-badge inline-flex items-center gap-2 px-4 py-2 bg-muted/50 rounded-full text-sm mb-8 border border-border/40"
            >
              <Download class="w-4 h-4 text-accent" />
              <span class="text-muted-foreground">Available Now</span>
            </div>

            <h1
              class="hero-title text-4xl md:text-6xl font-azonix font-bold tracking-tight mb-6 text-balance"
            >
              Download Axton
            </h1>

            <p
              class="hero-description text-lg md:text-xl text-muted-foreground mb-12 text-pretty leading-relaxed"
            >
              Get started with Axton wallet on your preferred platform.
              Available for desktop browsers and mobile devices.
            </p>
          </div>
        </div>

        <button
          on:click={scrollToContent}
          class="scroll-indicator absolute bottom-8 left-1/2 -translate-x-1/2 pointer-events-auto cursor-pointer bg-accent/10 hover:bg-accent/20 w-12 h-12 rounded-full flex items-center justify-center transition-colors z-30"
          aria-label="Scroll to content"
        >
          <ChevronDown class="w-6 h-6 text-accent" />
        </button>
      </div>
    </section>

    <!-- Desktop Section -->
    <section id="desktop-section" class="py-16 relative z-20">
      <div class="container mx-auto px-4">
        <div class="max-w-5xl mx-auto">
          <h2
            class="section-title text-3xl md:text-4xl font-heading font-bold mb-12 text-center"
          >
            Browser <span class="text-accent">Extensions</span>
          </h2>

          <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
            <!-- Chrome -->
            <Card.Root
              class="animate-card hover:border-accent transition-all hover:shadow-lg hover:shadow-accent/10"
            >
              <Card.Content class="text-center">
                <div
                  class="w-20 h-20 bg-accent/10 rounded-2xl mx-auto mb-6 flex items-center justify-center"
                >
                  <img src="/chrome-logo.svg" alt="Chrome" class="w-12 h-12" />
                </div>
                <h3 class="text-xl font-heading font-bold mb-3">Chrome</h3>
                <p class="text-sm text-muted-foreground mb-6">
                  Most popular browser
                </p>
                <Button
                  variant="accent"
                  class="w-full"
                  href="https://chrome.google.com/webstore"
                >
                  Add to Chrome
                </Button>
              </Card.Content>
            </Card.Root>

            <!-- Firefox -->
            <Card.Root
              class="animate-card hover:border-accent transition-all hover:shadow-lg hover:shadow-accent/10"
            >
              <Card.Content class="text-center">
                <div
                  class="w-20 h-20 bg-accent/10 rounded-2xl mx-auto mb-6 flex items-center justify-center"
                >
                  <img
                    src="/firefox-logo.svg"
                    alt="Firefox"
                    class="w-12 h-12"
                  />
                </div>
                <h3 class="text-xl font-heading font-bold mb-3">Firefox</h3>
                <p class="text-sm text-muted-foreground mb-6">
                  Privacy-focused browser
                </p>
                <Button
                  variant="accent"
                  class="w-full"
                  href="https://addons.mozilla.org"
                >
                  Add to Firefox
                </Button>
              </Card.Content>
            </Card.Root>

            <!-- Brave -->
            <Card.Root
              class="animate-card hover:border-accent transition-all hover:shadow-lg hover:shadow-accent/10"
            >
              <Card.Content class="text-center">
                <div
                  class="w-20 h-20 bg-accent/10 rounded-2xl mx-auto mb-6 flex items-center justify-center"
                >
                  <img src="/brave-logo.svg" alt="Brave" class="w-12 h-12" />
                </div>
                <h3 class="text-xl font-heading font-bold mb-3">Brave</h3>
                <p class="text-sm text-muted-foreground mb-6">
                  Privacy & rewards
                </p>
                <Button
                  variant="accent"
                  class="w-full"
                  href="https://chrome.google.com/webstore"
                >
                  Add to Brave
                </Button>
              </Card.Content>
            </Card.Root>

            <!-- Edge -->
            <Card.Root
              class="animate-card hover:border-accent transition-all hover:shadow-lg hover:shadow-accent/10"
            >
              <Card.Content class="text-center">
                <div
                  class="w-20 h-20 bg-accent/10 rounded-2xl mx-auto mb-6 flex items-center justify-center"
                >
                  <img src="/edge-logo.svg" alt="Edge" class="w-12 h-12" />
                </div>
                <h3 class="text-xl font-heading font-bold mb-3">Edge</h3>
                <p class="text-sm text-muted-foreground mb-6">
                  Microsoft's browser
                </p>
                <Button
                  variant="accent"
                  class="w-full"
                  href="https://microsoftedge.microsoft.com/addons"
                >
                  Add to Edge
                </Button>
              </Card.Content>
            </Card.Root>
          </div>
        </div>
      </div>
    </section>

    <!-- Mobile Section -->
    <section class="py-16 bg-muted/30 relative z-20">
      <div class="container mx-auto px-4">
        <div class="max-w-5xl mx-auto">
          <h2
            class="section-title text-3xl md:text-4xl font-heading font-bold mb-12 text-center"
          >
            Mobile <span class="text-accent">Apps</span>
          </h2>

          <div class="grid md:grid-cols-2 gap-8 max-w-3xl mx-auto">
            <!-- iOS -->
            <Card.Root
              class="animate-card hover:border-accent transition-all hover:shadow-lg hover:shadow-accent/10"
            >
              <Card.Content class="text-center">
                <div
                  class="w-24 h-24 bg-accent/10 rounded-3xl mx-auto mb-6 flex items-center justify-center"
                >
                  <svg
                    class="w-16 h-16"
                    viewBox="0 0 24 24"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M17.05 20.28c-.98.95-2.05.8-3.08.35-1.09-.46-2.09-.48-3.24 0-1.44.62-2.2.44-3.06-.35C2.79 15.25 3.51 7.59 9.05 7.31c1.35.07 2.29.74 3.08.8 1.18-.24 2.31-.93 3.57-.84 1.51.12 2.65.72 3.4 1.8-3.12 1.87-2.38 5.98.48 7.13-.57 1.5-1.31 2.99-2.53 4.09l-.01-.01zM12.03 7.25c-.15-2.23 1.66-4.07 3.74-4.25.29 2.58-2.34 4.5-3.74 4.25z"
                      fill="currentColor"
                      class="text-foreground"
                    />
                  </svg>
                </div>
                <h3 class="text-2xl font-heading font-bold mb-3">iOS</h3>
                <p class="text-muted-foreground mb-6">
                  Download for iPhone and iPad
                </p>
                <Button
                  variant="accent"
                  size="lg"
                  class="w-full"
                  href="https://apps.apple.com"
                >
                  <svg
                    class="w-5 h-5 mr-2"
                    viewBox="0 0 24 24"
                    fill="currentColor"
                  >
                    <path
                      d="M17.05 20.28c-.98.95-2.05.8-3.08.35-1.09-.46-2.09-.48-3.24 0-1.44.62-2.2.44-3.06-.35C2.79 15.25 3.51 7.59 9.05 7.31c1.35.07 2.29.74 3.08.8 1.18-.24 2.31-.93 3.57-.84 1.51.12 2.65.72 3.4 1.8-3.12 1.87-2.38 5.98.48 7.13-.57 1.5-1.31 2.99-2.53 4.09l-.01-.01zM12.03 7.25c-.15-2.23 1.66-4.07 3.74-4.25.29 2.58-2.34 4.5-3.74 4.25z"
                    />
                  </svg>
                  App Store
                </Button>
                <p class="text-xs text-muted-foreground mt-4">
                  iOS 14.0 or later
                </p>
              </Card.Content>
            </Card.Root>

            <!-- Android -->
            <Card.Root
              class="animate-card hover:border-accent transition-all hover:shadow-lg hover:shadow-accent/10"
            >
              <Card.Content class="text-center">
                <div
                  class="w-24 h-24 bg-accent/10 rounded-3xl mx-auto mb-6 flex items-center justify-center"
                >
                  <svg
                    class="w-16 h-16"
                    viewBox="0 0 24 24"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M17.6 9.48l1.84-3.18c.16-.31.04-.69-.26-.85a.637.637 0 0 0-.83.22l-1.88 3.24a11.43 11.43 0 0 0-8.94 0L5.65 5.67a.643.643 0 0 0-.87-.2c-.28.18-.37.54-.22.83L6.4 9.48A10.81 10.81 0 0 0 1 18h22a10.81 10.81 0 0 0-5.4-8.52zM7 15.25a1.25 1.25 0 1 1 0-2.5 1.25 1.25 0 0 1 0 2.5zm10 0a1.25 1.25 0 1 1 0-2.5 1.25 1.25 0 0 1 0 2.5z"
                      fill="currentColor"
                      class="text-foreground"
                    />
                  </svg>
                </div>
                <h3 class="text-2xl font-heading font-bold mb-3">Android</h3>
                <p class="text-muted-foreground mb-6">
                  Download for Android devices
                </p>
                <Button
                  variant="accent"
                  size="lg"
                  class="w-full"
                  href="https://play.google.com"
                >
                  <svg
                    class="w-5 h-5 mr-2"
                    viewBox="0 0 24 24"
                    fill="currentColor"
                  >
                    <path
                      d="M3,20.5V3.5C3,2.91 3.34,2.39 3.84,2.15L13.69,12L3.84,21.85C3.34,21.6 3,21.09 3,20.5M16.81,15.12L6.05,21.34L14.54,12.85L16.81,15.12M20.16,10.81C20.5,11.08 20.75,11.5 20.75,12C20.75,12.5 20.53,12.9 20.18,13.18L17.89,14.5L15.39,12L17.89,9.5L20.16,10.81M6.05,2.66L16.81,8.88L14.54,11.15L6.05,2.66Z"
                    />
                  </svg>
                  Google Play
                </Button>
                <p class="text-xs text-muted-foreground mt-4">
                  Android 8.0 or later
                </p>
              </Card.Content>
            </Card.Root>
          </div>
        </div>
      </div>
    </section>

    <!-- Support Section -->
    <section class="py-16 relative z-20">
      <div class="container mx-auto px-4">
        <div class="support-section max-w-3xl mx-auto text-center">
          <h2 class="text-2xl md:text-3xl font-heading font-bold mb-6">
            Need Help?
          </h2>
          <p class="text-muted-foreground mb-8">
            Check out our documentation or reach out to our support team for
            assistance with installation and setup.
          </p>
          <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <Button
              size="lg"
              variant="secondary"
              href="https://docs.axtonlabs.com"
            >
              View Documentation
            </Button>
            <Button size="lg" variant="secondary" href="https://discord.gg">
              Join Discord
            </Button>
          </div>
        </div>
      </div>
    </section>
  </main>
</div>
