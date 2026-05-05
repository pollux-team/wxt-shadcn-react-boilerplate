# WXT + React + shadcn/ui Boilerplate

A modern browser extension boilerplate featuring WXT, React 19, Tailwind CSS v4, and shadcn/ui components. Built with Bun for blazing-fast development.

[![Release](https://github.com/pollux-team/wxt-shadcn-react-boilerplate/actions/workflows/release.yml/badge.svg)](https://github.com/pollux-team/wxt-shadcn-react-boilerplate/actions/workflows/release.yml)

## ✨ Features

- 🚀 **[WXT](https://wxt.dev/)** - Next-gen web extension framework
- ⚛️ **[React 19](https://react.dev/)** - Latest React with modern features
- 🎨 **[Tailwind CSS v4](https://tailwindcss.com/)** - Utility-first CSS framework
- 🧩 **[shadcn/ui](https://ui.shadcn.com/)** - Beautiful, accessible component library
- ⚡ **[Bun](https://bun.sh/)** - Fast all-in-one JavaScript runtime
- 🔧 **TypeScript** - Type-safe development
- 🎯 **Pre-configured** - Ready to use with sensible defaults
- 🔄 **CI/CD** - Automated releases with GitHub Actions

## 📦 What's Included

```
├── .github/workflows/    # CI/CD workflows
├── assets/              # Static assets (CSS, images)
├── components/          # React components
│   └── ui/             # shadcn/ui components
├── entrypoints/        # Extension entry points
│   └── popup/          # Popup UI
├── lib/                # Utility functions
├── public/             # Public assets (icons)
├── components.json     # shadcn/ui configuration
├── tsconfig.json       # TypeScript configuration
├── vite.config.ts      # Vite config (for tooling)
└── wxt.config.ts       # WXT configuration
```

## 🚀 Quick Start

### Prerequisites

- [Bun](https://bun.sh/) installed on your system
- Node.js 18+ (for compatibility)

### Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/pollux-team/wxt-shadcn-react-boilerplate.git
   cd wxt-shadcn-react-boilerplate
   ```

2. **Install dependencies:**

   ```bash
   bun install
   ```

3. **Start development:**

   ```bash
   bun run dev
   ```

   For Firefox:
   ```bash
   bun run dev:firefox
   ```

4. **Load the extension:**
   - **Chrome/Edge**: Navigate to `chrome://extensions`, enable "Developer mode", click "Load unpacked", and select the `.output/chrome-mv3` directory
   - **Firefox**: Navigate to `about:debugging#/runtime/this-firefox`, click "Load Temporary Add-on", and select any file in the `.output/firefox-mv2` directory

## 📜 Available Scripts

| Command | Description |
|---------|-------------|
| `bun run dev` | Start development server (Chrome) |
| `bun run dev:firefox` | Start development server (Firefox) |
| `bun run build` | Build for production (Chrome) |
| `bun run build:firefox` | Build for production (Firefox) |
| `bun run zip` | Create distributable ZIP (Chrome) |
| `bun run zip:firefox` | Create distributable ZIP (Firefox) |
| `bun run compile` | Type-check without emitting files |

## 🎨 Adding shadcn/ui Components

Add new components using the shadcn CLI:

```bash
bunx --bun shadcn@latest add button
bunx --bun shadcn@latest add card
bunx --bun shadcn@latest add dialog
```

Browse all available components at [ui.shadcn.com](https://ui.shadcn.com/).

## 🏗️ Project Structure

### Entry Points

WXT uses an entry point-based structure. Each file in the `entrypoints/` directory becomes a part of your extension:

- `popup/` - Extension popup UI
- `background.ts` - Background service worker (add if needed)
- `content.ts` - Content scripts (add if needed)

Learn more about [WXT entry points](https://wxt.dev/guide/essentials/entrypoints.html).

### Components

- `components/ui/` - shadcn/ui components (auto-generated)
- `components/` - Your custom components

### Styling

- `assets/tailwind.css` - Tailwind CSS imports
- Tailwind v4 uses `@import "tailwindcss"` syntax
- Import in your components: `import "@/assets/tailwind.css"`

## 🔧 Configuration

### Path Aliases

The project uses `@/` as an alias for the root directory:

```typescript
import { Button } from "@/components/ui/button"
import { cn } from "@/lib/utils"
```

Configured in:
- `tsconfig.json` - For TypeScript
- `wxt.config.ts` - For WXT/Vite resolution
- `vite.config.ts` - For shadcn CLI detection

### Tailwind CSS

Tailwind is configured via the Vite plugin in `wxt.config.ts`:

```typescript
import tailwindcss from "@tailwindcss/vite"

export default defineConfig({
  vite: () => ({
    plugins: [tailwindcss()],
  }),
})
```

### shadcn/ui

Configuration is stored in `components.json`. Customize:
- Component style (default: `radix-luma`)
- Color scheme (default: `zinc`)
- Icon library (default: `lucide`)

## 🚢 Deployment & Releases

### Automated Releases

This boilerplate includes a GitHub Actions workflow for automated releases:

1. **Update version** in `package.json`
2. **Commit and push** your changes
3. **Trigger release** via GitHub Actions:
   - Go to Actions → Release → Run workflow
   - Select branch (default: `main`)
   - Click "Run workflow"

The workflow will:
- Build extensions for Chrome and Firefox
- Create ZIP files
- Create a GitHub release with version tag
- Upload ZIP files as release assets

### Manual Build

```bash
# Build for production
bun run build
bun run build:firefox

# Create distribution ZIPs
bun run zip
bun run zip:firefox
```

Output files will be in `.output/` directory.

## 📝 Important Notes

### vite.config.ts

The `vite.config.ts` file exists solely for shadcn CLI compatibility. WXT uses its own Vite configuration from `wxt.config.ts` for building the extension. The standalone Vite config won't interfere with your builds.

### TypeScript Configuration

Due to current limitations in shadcn/ui's path resolution ([issue #6020](https://github.com/shadcn-ui/ui/issues/6020)), paths must be defined in both `tsconfig.json` and `wxt.config.ts`. This is a temporary workaround until the issue is resolved.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [WXT](https://wxt.dev/) - Amazing web extension framework
- [shadcn/ui](https://ui.shadcn.com/) - Beautiful component library
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS
- [React](https://react.dev/) - UI library
- [Bun](https://bun.sh/) - Fast JavaScript runtime

## 📚 Resources

- [WXT Documentation](https://wxt.dev/)
- [shadcn/ui Documentation](https://ui.shadcn.com/)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [React Documentation](https://react.dev/)
- [Chrome Extension Documentation](https://developer.chrome.com/docs/extensions/)
- [Firefox Extension Documentation](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions)

---

**Built with ❤️ by the Pollux Team**
