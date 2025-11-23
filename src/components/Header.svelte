<script lang="ts">
  import { Button } from "./ui/button";
</script>

<header class="fixed top-4 left-0 right-0 z-50">
  <nav
    class="container mx-auto px-8 py-6 flex items-center justify-between border-b border-border/40 bg-background/40 backdrop-blur-md rounded-xl"
  >
    <a
      href="/"
      class="flex items-center gap-3 hover:scale-105 transition-transform"
    >
      <img src="/axton-logo.png" alt="Axton Labs" class="h-8 w-8" />
      <span class="font-azonix text-xl tracking-wider">AXTON</span>
    </a>

    <div class="hidden md:flex items-center gap-8">
      <a
        href="/#products"
        class="text-muted-foreground hover:text-foreground transition-colors font-medium"
      >
        Products
      </a>
      <a
        href="/#features"
        class="text-muted-foreground hover:text-foreground transition-colors font-medium"
      >
        Features
      </a>
      <a
        href="/#security"
        class="text-muted-foreground hover:text-foreground transition-colors font-medium"
      >
        Security
      </a>
      <a
        href="/#team"
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

    <div class="flex items-center gap-4">
      <div class="hidden md:flex items-center gap-3">
        <a
          href="https://twitter.com/axtonlabs"
          target="_blank"
          rel="noopener noreferrer"
          class="text-muted-foreground hover:text-accent transition-colors"
          aria-label="X (Twitter)"
        >
          <svg
            class="w-5 h-5"
            viewBox="0 0 24 24"
            fill="currentColor"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"
            />
          </svg>
        </a>
        <a
          href="https://discord.gg/axtonlabs"
          target="_blank"
          rel="noopener noreferrer"
          class="text-muted-foreground hover:text-accent transition-colors"
          aria-label="Discord"
        >
          <svg
            class="w-5 h-5"
            viewBox="0 0 24 24"
            fill="currentColor"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M20.317 4.492c-1.53-.69-3.17-1.2-4.885-1.49a.075.075 0 0 0-.079.036c-.21.369-.444.85-.608 1.23a18.566 18.566 0 0 0-5.487 0 12.36 12.36 0 0 0-.617-1.23A.077.077 0 0 0 8.562 3c-1.714.29-3.354.8-4.885 1.491a.07.07 0 0 0-.032.027C.533 9.093-.32 13.555.099 17.961a.08.08 0 0 0 .031.055 20.03 20.03 0 0 0 5.993 2.98.078.078 0 0 0 .084-.026c.462-.62.874-1.275 1.226-1.963.021-.04.001-.088-.041-.104a13.201 13.201 0 0 1-1.872-.878.075.075 0 0 1-.008-.125c.126-.093.252-.19.372-.287a.075.075 0 0 1 .078-.01c3.927 1.764 8.18 1.764 12.061 0a.075.075 0 0 1 .079.009c.12.098.245.195.372.288a.075.075 0 0 1-.006.125c-.598.344-1.22.635-1.873.877a.075.075 0 0 0-.041.105c.36.687.772 1.341 1.225 1.962a.077.077 0 0 0 .084.028 19.963 19.963 0 0 0 6.002-2.981.076.076 0 0 0 .032-.054c.5-5.094-.838-9.52-3.549-13.442a.06.06 0 0 0-.031-.028zM8.02 15.278c-1.182 0-2.157-1.069-2.157-2.38 0-1.312.956-2.38 2.157-2.38 1.21 0 2.176 1.077 2.157 2.38 0 1.312-.956 2.38-2.157 2.38zm7.975 0c-1.183 0-2.157-1.069-2.157-2.38 0-1.312.955-2.38 2.157-2.38 1.21 0 2.176 1.077 2.157 2.38 0 1.312-.946 2.38-2.157 2.38z"
            />
          </svg>
        </a>
        <a
          href="https://t.me/axtonlabs"
          target="_blank"
          rel="noopener noreferrer"
          class="text-muted-foreground hover:text-accent transition-colors"
          aria-label="Telegram"
        >
          <svg
            class="w-5 h-5"
            viewBox="0 0 24 24"
            fill="currentColor"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm4.64 6.8c-.15 1.58-.8 5.42-1.13 7.19-.14.75-.42 1-.68 1.03-.58.05-1.02-.38-1.58-.75-.88-.58-1.38-.94-2.23-1.5-.99-.65-.35-1.01.22-1.59.15-.15 2.71-2.48 2.76-2.69a.2.2 0 0 0-.05-.18c-.06-.05-.14-.03-.21-.02-.09.02-1.49.95-4.22 2.79-.4.27-.76.41-1.08.4-.36-.01-1.04-.2-1.55-.37-.63-.2-1.12-.31-1.08-.66.02-.18.27-.36.74-.55 2.92-1.27 4.86-2.11 5.83-2.51 2.78-1.16 3.35-1.36 3.73-1.36.08 0 .27.02.39.12.1.08.13.19.14.27-.01.06.01.24 0 .38z"
            />
          </svg>
        </a>
      </div>
      <Button variant="accent" size="lg" href="/download">Download</Button>
    </div>
  </nav>
</header>
