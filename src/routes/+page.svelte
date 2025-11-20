<script lang="ts">
  import { Zap, Wallet, Activity, Users } from "lucide-svelte";
  import Lightning from "../components/Lightning.svelte";
  import Galaxy from "../components/Galaxy.svelte";
  import { Button } from "../components/ui/button";
  import * as Card from "../components/ui/card";
</script>

<div class="min-h-screen bg-background text-foreground">
  <!-- Hero Section -->
  <header class="fixed top-4 left-0 right-0 z-50">
    <nav
      class="container mx-auto px-8 py-6 flex items-center justify-between border-b border-border/40 bg-background/40 backdrop-blur-md rounded-xl"
    >
      <a
        href="/"
        class="flex items-center gap-3 hover:scale-105 transition-transform"
      >
        <img src="/axton-logo.png" alt="Axton Labs" class="h-8 w-8" />
        <span class="font-heading text-xl tracking-wider">AXTON</span>
      </a>

      <div class="hidden md:flex items-center gap-8">
        <a
          href="#products"
          class="text-muted-foreground hover:text-foreground transition-colors font-medium"
        >
          Products
        </a>
        <a
          href="#mev"
          class="text-muted-foreground hover:text-foreground transition-colors font-medium"
        >
          About MEV
        </a>
        <a
          href="#team"
          class="text-muted-foreground hover:text-foreground transition-colors font-medium"
        >
          Team
        </a>
        <a
          href="https://docs.axtonlabs.com"
          class="text-muted-foreground hover:text-foreground transition-colors font-medium"
        >
          Docs
        </a>
      </div>

      <Button variant="accent" size="lg">Download</Button>
    </nav>
  </header>

  <main>
    <!-- Hero -->
    <section class="relative overflow-hidden h-screen">
      <div class="absolute inset-0">
        <Lightning hue={185} xOffset={0} speed={1} intensity={1} size={1} />
      </div>

      <div class="bg-background/40 relative z-20 h-screen">
        <div class="container mx-auto px-4 py-50 md:pt-56">
          <div class="max-w-4xl mx-auto text-center">
            <div
              class="inline-flex items-center gap-2 px-4 py-2 bg-muted/50 rounded-full text-sm mb-8 border border-border/40"
            >
              <div class="w-2 h-2 bg-accent rounded-full animate-pulse"></div>
              <span class="text-muted-foreground">The Power of MEV</span>
            </div>

            <h1
              class="text-5xl md:text-7xl font-heading font-bold tracking-tight mb-6 text-balance"
            >
              AXTON LABS
            </h1>

            <p
              class="text-xl md:text-2xl text-muted-foreground mb-12 text-pretty leading-relaxed"
            >
              MEV-enabled wallet and supply chain infrastructure for traders who
              demand more.
            </p>

            <div class="flex flex-col sm:flex-row gap-4 justify-center">
              <Button size="lg" variant="accent">Get Started</Button>
              <Button size="lg" variant="secondary">View Docs</Button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- What is MEV -->
    <section id="mev" class="py-20 bg-muted/30 border-y border-border/40">
      <div class="container mx-auto px-4">
        <div class="max-w-4xl mx-auto">
          <h2
            class="text-3xl md:text-4xl font-heading font-bold mb-6 text-center"
          >
            What is MEV?
          </h2>
          <p
            class="text-lg text-muted-foreground leading-relaxed mb-6 text-center text-pretty"
          >
            Maximal Extractable Value (MEV) is the value that can be extracted
            by manipulating transaction sequencing. This includes adding,
            removing, or reordering transactions within a block.
          </p>
          <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mt-12">
            {#each ["Arbitrage", "Sandwiching", "Backrun", "Liquidations"] as type}
              <div
                class="bg-background border border-border rounded-lg p-4 text-center"
              >
                <div class="text-sm font-mono text-accent">{type}</div>
              </div>
            {/each}
          </div>
        </div>
      </div>
    </section>

    <!-- Products -->
    <section id="products" class="py-24">
      <div class="container mx-auto px-4">
        <h2
          class="text-3xl md:text-5xl font-heading font-bold mb-16 text-center"
        >
          Axton Supply Chain
        </h2>

        <div class="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
          <!-- Wallet -->
          <Card.Root class="hover:border-accent transition-colors">
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
          <Card.Root class="hover:border-accent transition-colors">
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
          <Card.Root class="hover:border-accent transition-colors">
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

    <!-- Stats/Trust -->
    <section class="py-20 bg-muted/30 border-y border-border/40">
      <div class="container mx-auto px-4">
        <div class="grid md:grid-cols-3 gap-12 max-w-5xl mx-auto text-center">
          <div>
            <div
              class="text-4xl md:text-5xl font-heading font-bold text-accent mb-2"
            >
              2+
            </div>
            <div class="text-muted-foreground">Years MEV Experience</div>
          </div>
          <div>
            <div
              class="text-4xl md:text-5xl font-heading font-bold text-accent mb-2"
            >
              Solana
            </div>
            <div class="text-muted-foreground">Native Infrastructure</div>
          </div>
          <div>
            <div
              class="text-4xl md:text-5xl font-heading font-bold text-accent mb-2"
            >
              3
            </div>
            <div class="text-muted-foreground">Core Products</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Team -->
    <section id="team" class="py-24">
      <div class="container mx-auto px-4">
        <div class="max-w-4xl mx-auto text-center mb-16">
          <h2 class="text-3xl md:text-5xl font-heading font-bold mb-6">
            Built by MEV Experts
          </h2>
          <p class="text-lg text-muted-foreground text-pretty leading-relaxed">
            The team behind Axton Labs has over 2 years of experience MEV
            searching on Solana. Expertise in Distributed Systems, Full-Stack
            Development, MEV, and Hardware.
          </p>
        </div>

        <div class="grid md:grid-cols-2 gap-8 max-w-3xl mx-auto">
          <!-- Sarmat -->
          <Card.Root class="text-center hover:border-accent transition-colors">
            <Card.Content>
              <div
                class="w-20 h-20 bg-accent/10 rounded-full mx-auto mb-4 flex items-center justify-center"
              >
                <Users class="w-10 h-10 text-accent" />
              </div>
              <h3 class="text-xl font-heading font-bold mb-2">Sarmat</h3>
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

          <!-- Alan -->
          <Card.Root class="text-center hover:border-accent transition-colors">
            <Card.Content>
              <div
                class="w-20 h-20 bg-accent/10 rounded-full mx-auto mb-4 flex items-center justify-center"
              >
                <Users class="w-10 h-10 text-accent" />
              </div>
              <h3 class="text-xl font-heading font-bold mb-2">Alan</h3>
              <a
                href="https://x.com/solhandl"
                target="_blank"
                rel="noopener noreferrer"
                class="text-accent hover:underline font-mono text-sm"
              >
                @solhandl
              </a>
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
        />
      </div>
      <div
        class="container mx-auto px-4 text-center relative z-20 pointer-events-none"
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
        <Button size="lg" variant="accent" class="pointer-events-auto"
          >Get Early Access</Button
        >
      </div>
    </section>
  </main>

  <!-- Footer -->
  <footer class="border-t border-border/40 py-12">
    <div class="container mx-auto px-4">
      <div class="flex flex-col md:flex-row justify-between items-center gap-6">
        <a href="/" class="flex items-center gap-3 hover:scale-105">
          <img src="/axton-logo.png" alt="Axton Labs" class="h-8 w-8" />
          <span class="font-heading text-lg tracking-wider">AXTON LABS</span>
        </a>
        <div class="text-sm text-muted-foreground">
          © 2025 Axton Labs. All rights reserved.
        </div>
      </div>
    </div>
  </footer>
</div>
