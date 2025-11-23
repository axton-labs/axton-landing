<script lang="ts">
  import { onMount } from "svelte";
  import { browser } from "$app/environment";
  import { Zap, Wallet, Activity, Users } from "lucide-svelte";
  import Galaxy from "../components/Galaxy.svelte";
  import { Button } from "../components/ui/button";
  import * as Card from "../components/ui/card";
  import gsap from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";

  if (browser) {
    gsap.registerPlugin(ScrollTrigger);
  }

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
      ".hero-buttons",
      { opacity: 0, y: 30 },
      { opacity: 1, y: 0, duration: 0.8, delay: 0.8, ease: "power2.out" }
    );

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

    gsap.fromTo(
      ".team-description",
      { opacity: 0, y: 30 },
      {
        opacity: 1,
        y: 0,
        duration: 0.8,
        ease: "power2.out",
        scrollTrigger: {
          trigger: ".team-description",
          start: "top 85%",
        },
      }
    );

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
      ".cta-section",
      { opacity: 0, y: 50 },
      {
        opacity: 1,
        y: 0,
        duration: 1,
        ease: "power2.out",
        scrollTrigger: {
          trigger: ".cta-section",
          start: "top 85%",
        },
      }
    );
  });
</script>

<div class="min-h-screen bg-background text-foreground">
  <main>
    <!-- Hero -->
    <section class="relative overflow-hidden h-screen">
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

      <div class="bg-background/40 relative z-20 h-screen pointer-events-none">
        <div class="container mx-auto px-4 pt-50 md:pt-56">
          <div class="max-w-4xl mx-auto text-center">
            <h1
              class="hero-title text-5xl md:text-7xl font-azonix font-bold tracking-tight mb-6 text-balance"
            >
              AXTON LABS
            </h1>

            <p
              class="hero-description text-xl md:text-2xl text-muted-foreground mb-12 text-pretty leading-relaxed"
            >
              Self-custody wallet and supply chain infrastructure for traders
              who demand more.
            </p>

            <div
              class="hero-buttons flex flex-col sm:flex-row gap-4 justify-center pointer-events-auto"
            >
              <Button size="lg" variant="accent" href="/download"
                >Get Started</Button
              >
              <Button
                size="lg"
                variant="secondary"
                href="https://docs.axtonlabs.com">View Docs</Button
              >
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Products -->
    <section id="products" class="py-24 bg-muted/30">
      <div class="container mx-auto px-4">
        <h2
          class="section-title text-3xl md:text-5xl font-heading font-bold mb-16 text-center"
        >
          Axton Supply Chain
        </h2>

        <div class="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
          <!-- Wallet -->
          <Card.Root class="animate-card hover:border-accent transition-colors">
            <Card.Content>
              <div
                class="w-14 h-14 bg-accent/10 rounded-lg flex items-center justify-center mb-6"
              >
                <Wallet class="w-7 h-7 text-accent" />
              </div>
              <h3 class="text-2xl font-heading font-bold mb-4">Wallet</h3>
              <ul class="space-y-3 text-muted-foreground">
                <li class="flex items-start gap-2">
                  <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                  <span>Native rebates</span>
                </li>
                <li class="flex items-start gap-2">
                  <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                  <span>Trader optimized</span>
                </li>
                <li class="flex items-start gap-2">
                  <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                  <span>Web2 retail users friendly</span>
                </li>
              </ul>
            </Card.Content>
          </Card.Root>

          <!-- OFA -->
          <Card.Root class="animate-card hover:border-accent transition-colors">
            <Card.Content>
              <div
                class="w-14 h-14 bg-accent/10 rounded-lg flex items-center justify-center mb-6"
              >
                <Activity class="w-7 h-7 text-accent" />
              </div>
              <h3 class="text-2xl font-heading font-bold mb-4">
                Order Flow Auction
              </h3>
              <p class="text-muted-foreground leading-relaxed">
                Capture maximum value through sophisticated order flow auctions
                designed for optimal price discovery.
              </p>
            </Card.Content>
          </Card.Root>

          <!-- Settlement -->
          <Card.Root class="animate-card hover:border-accent transition-colors">
            <Card.Content>
              <div
                class="w-14 h-14 bg-accent/10 rounded-lg flex items-center justify-center mb-6"
              >
                <div class="w-7 h-7 text-accent">
                  <svg
                    viewBox="0 0 24 24"
                    fill="none"
                    stroke="currentColor"
                    stroke-width="2"
                  >
                    <path d="M12 2L2 7l10 5 10-5-10-5z" />
                    <path d="M2 17l10 5 10-5" />
                    <path d="M2 12l10 5 10-5" />
                  </svg>
                </div>
              </div>
              <h3 class="text-2xl font-heading font-bold mb-4">
                Settlement Infra
              </h3>
              <p class="text-muted-foreground leading-relaxed">
                Transaction and bundle onchain settlement infrastructure built
                for speed and reliability.
              </p>
            </Card.Content>
          </Card.Root>
        </div>
      </div>
    </section>

    <!-- Features: Keep Everything in One Place -->
    <section id="features" class="py-24">
      <div class="container mx-auto px-4">
        <div class="max-w-6xl mx-auto">
          <h2
            class="section-title text-3xl md:text-5xl font-heading font-bold mb-16 text-center"
          >
            Keep everything <span class="text-accent">in one place</span>
          </h2>

          <div class="grid md:grid-cols-2 gap-8">
            <Card.Root
              class="animate-card hover:border-accent transition-colors"
            >
              <Card.Content>
                <h3 class="text-xl font-heading font-bold mb-4">Your Wallet</h3>
                <ul class="space-y-3 text-muted-foreground">
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span>Multiple chains, one wallet. No more switching.</span>
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span
                      >Monitor activity with transaction history and
                      notifications.</span
                    >
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span
                      >Communicate with your addresses using the built-in chat.</span
                    >
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span>Create repeatable transactions with templates.</span>
                  </li>
                </ul>
              </Card.Content>
            </Card.Root>

            <Card.Root
              class="animate-card hover:border-accent transition-colors"
            >
              <Card.Content>
                <h3 class="text-xl font-heading font-bold mb-4">
                  Your MEV Hub
                </h3>
                <ul class="space-y-3 text-muted-foreground">
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span>Real-time MEV capture and rebate tracking.</span>
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span>Advanced transaction routing.</span>
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span>Priority fee optimization.</span>
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span>Bundle submission and tracking.</span>
                  </li>
                </ul>
              </Card.Content>
            </Card.Root>
          </div>
        </div>
      </div>
    </section>

    <!-- Features: Powerful Tools -->
    <section class="py-24 bg-muted/30">
      <div class="container mx-auto px-4">
        <div class="max-w-6xl mx-auto">
          <h2
            class="section-title text-3xl md:text-5xl font-heading font-bold mb-16 text-center"
          >
            Powerful <span class="text-accent">tools</span> made for everyone
          </h2>

          <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
            <Card.Root
              class="animate-card hover:border-accent transition-colors"
            >
              <Card.Content>
                <div
                  class="w-12 h-12 bg-accent/10 rounded-lg flex items-center justify-center mb-4"
                >
                  <Activity class="w-6 h-6 text-accent" />
                </div>
                <h3 class="text-xl font-heading font-bold mb-3">Smart Swaps</h3>
                <p class="text-muted-foreground">
                  Swap tokens super fast with MEV protection and optimal
                  routing.
                </p>
              </Card.Content>
            </Card.Root>

            <Card.Root
              class="animate-card hover:border-accent transition-colors"
            >
              <Card.Content>
                <div
                  class="w-12 h-12 bg-accent/10 rounded-lg flex items-center justify-center mb-4"
                >
                  <Wallet class="w-6 h-6 text-accent" />
                </div>
                <h3 class="text-xl font-heading font-bold mb-3">
                  Stake & Earn
                </h3>
                <p class="text-muted-foreground">
                  Store, stake, and earn rewards with your tokens effortlessly.
                </p>
              </Card.Content>
            </Card.Root>

            <Card.Root
              class="animate-card hover:border-accent transition-colors"
            >
              <Card.Content>
                <div
                  class="w-12 h-12 bg-accent/10 rounded-lg flex items-center justify-center mb-4"
                >
                  <Zap class="w-6 h-6 text-accent" />
                </div>
                <h3 class="text-xl font-heading font-bold mb-3">
                  Advanced Analytics
                </h3>
                <p class="text-muted-foreground">
                  Track your portfolio performance and MEV capture in real-time.
                </p>
              </Card.Content>
            </Card.Root>
          </div>
        </div>
      </div>
    </section>

    <!-- Features: Security -->
    <section id="security" class="py-24">
      <div class="container mx-auto px-4">
        <div class="max-w-6xl mx-auto">
          <h2
            class="section-title text-3xl md:text-5xl font-heading font-bold mb-16 text-center"
          >
            Controlled by you, <span class="text-accent">secured</span> by us
          </h2>

          <div class="grid md:grid-cols-2 gap-8">
            <Card.Root
              class="animate-card hover:border-accent transition-colors"
            >
              <Card.Content>
                <h3 class="text-xl font-heading font-bold mb-4">
                  Your Security
                </h3>
                <ul class="space-y-3 text-muted-foreground">
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span
                      >Self-custodial means you control your funds. We never
                      have access.</span
                    >
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span
                      >Private by design. No name, email, or phone number
                      required.</span
                    >
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span
                      >Scam detection flags malicious transactions instantly.</span
                    >
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span
                      >Connect your Ledger to keep your crypto even safer.</span
                    >
                  </li>
                </ul>
              </Card.Content>
            </Card.Root>

            <Card.Root
              class="animate-card hover:border-accent transition-colors"
            >
              <Card.Content>
                <h3 class="text-xl font-heading font-bold mb-4">
                  Your Support
                </h3>
                <ul class="space-y-3 text-muted-foreground">
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span>24/7 community support from MEV experts.</span>
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span>Comprehensive documentation and guides.</span>
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span>Active Discord community of traders.</span>
                  </li>
                  <li class="flex items-start gap-2">
                    <Zap class="w-5 h-5 text-accent mt-0.5 shrink-0" />
                    <span>Regular updates and new features.</span>
                  </li>
                </ul>
              </Card.Content>
            </Card.Root>
          </div>
        </div>
      </div>
    </section>

    <!-- Team -->
    <section id="team" class="py-24">
      <div class="container mx-auto px-4">
        <div class="max-w-4xl mx-auto text-center mb-16">
          <h2
            class="section-title text-3xl md:text-5xl font-heading font-bold mb-6"
          >
            Built by Experts
          </h2>
          <p
            class="team-description text-lg text-muted-foreground text-pretty leading-relaxed"
          >
            The team behind Axton Labs has over 6 years of experience in wallet
            security research. Bringing deep expertise across software
            development, hardware security, blockchain technology, and web3
            marketing.
          </p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8 max-w-6xl mx-auto">
          <!-- Alan -->
          <Card.Root
            class="animate-card text-center hover:border-accent transition-colors"
          >
            <Card.Content>
              <div
                class="w-20 h-20 bg-accent/10 rounded-full mx-auto mb-4 flex items-center justify-center"
              >
                <Users class="w-10 h-10 text-accent" />
              </div>
              <h3 class="text-xl font-heading font-bold mb-2">Alan</h3>
              <p class="text-sm text-accent mb-2">Co-Founder</p>
              <p class="text-sm text-muted-foreground mb-3">
                Product development & growth expert. Ex 1inch, eesee
              </p>
              <a
                href="https://x.com/solhandl"
                target="_blank"
                rel="noopener noreferrer"
                class="text-accent hover:underline font-mono text-xs"
              >
                @solhandl
              </a>
            </Card.Content>
          </Card.Root>
          <!-- Sarmat -->
          <Card.Root
            class="animate-card text-center hover:border-accent transition-colors"
          >
            <Card.Content>
              <div
                class="w-20 h-20 bg-accent/10 rounded-full mx-auto mb-4 flex items-center justify-center"
              >
                <Users class="w-10 h-10 text-accent" />
              </div>
              <h3 class="text-xl font-heading font-bold mb-2">Sarmat</h3>
              <p class="text-sm text-accent mb-2">Co-Founder</p>
              <p class="text-sm text-muted-foreground mb-3">
                Hardware, security & blockchain expert. Ex 1inch, bigwhalelabs
              </p>
              <a
                href="https://x.com/0xsarmat"
                target="_blank"
                rel="noopener noreferrer"
                class="text-accent hover:underline font-mono text-sm"
              >
                @0xsarmat
              </a>
            </Card.Content>
          </Card.Root>
          <!-- Dave -->
          <Card.Root
            class="animate-card text-center hover:border-accent transition-colors"
          >
            <Card.Content>
              <div
                class="w-20 h-20 bg-accent/10 rounded-full mx-auto mb-4 flex items-center justify-center"
              >
                <Users class="w-10 h-10 text-accent" />
              </div>
              <h3 class="text-xl font-heading font-bold mb-2">Dave</h3>
              <p class="text-sm text-accent mb-2">Head of Marketing</p>
              <p class="text-sm text-muted-foreground mb-3">
                Web3 marketing expert
              </p>
            </Card.Content>
          </Card.Root>
          <!-- Alex -->
          <Card.Root
            class="animate-card text-center hover:border-accent transition-colors"
          >
            <Card.Content>
              <div
                class="w-20 h-20 bg-accent/10 rounded-full mx-auto mb-4 flex items-center justify-center"
              >
                <Users class="w-10 h-10 text-accent" />
              </div>
              <h3 class="text-xl font-heading font-bold mb-2">Alex</h3>
              <p class="text-sm text-accent mb-2">Head of Design</p>
              <p class="text-sm text-muted-foreground mb-3">
                Web3 design expert
              </p>
            </Card.Content>
          </Card.Root>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="py-24 relative">
      <div class="absolute inset-0">
        <Galaxy
          hueShift={140}
          density={1}
          mouseRepulsion={true}
          transparent={true}
          disableAnimation={true}
        />
      </div>
      <div
        class="cta-section container mx-auto px-4 text-center relative z-20 pointer-events-none"
      >
        <h2
          class="text-3xl md:text-5xl font-heading font-bold mb-6 text-balance"
        >
          Ready to unleash the beast?
        </h2>
        <p
          class="text-lg md:text-xl mb-10 text-primary/80 max-w-2xl mx-auto text-pretty"
        >
          Join traders who are maximizing their MEV capture with Axton's
          complete infrastructure.
        </p>
        <Button
          size="lg"
          variant="accent"
          class="pointer-events-auto"
          href="/download">Get Early Access</Button
        >
      </div>
    </section>
  </main>
</div>
