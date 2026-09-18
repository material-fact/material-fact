# Material Fact

A static Astro website matching the Figma homepage, with semantic HTML, plain CSS, local Archivo fonts, and responsive WebP portraits. No client-side framework is needed.

## Preview

On a new computer, install Node.js 22.12 or newer, open the project folder, and run `npm ci` to install the locked dependencies.

Run `npm run dev -- --background`, then open http://localhost:4321.

- Status: `npm run astro -- dev status`
- Logs: `npm run astro -- dev logs`
- Stop: `npm run astro -- dev stop`
- Production build: `npm run build`

## Working together and launching

Pull the latest changes before editing. Use a separate branch for changes, commit and push it, then open a pull request for your partner to review. The main writing is in `src/pages/index.astro`; visual styles are in `src/styles/global.css`.

For hosting, this is a static Astro site: use `npm ci` to install dependencies, `npm run build` to build, and `dist` as the publish directory. No environment variables are currently required. The person launching the site should connect the repository to the hosting account and configure the custom domain there. Publishing the repository does not itself deploy the website.

## Design and source

Reference: [Material Fact - Research Recruiting Site](https://www.figma.com/design/WuNLrS4OBGxaXk3TUViIzY/?node-id=86-3), page `Homepage Design`, frame `home - 04 index` (86:3).

- `src/pages/index.astro`: page content, profile and FAQ data, Calendly and LinkedIn links.
- `src/styles/global.css`: Figma typography, color tokens, spacing, image crops, and responsive layouts.
- `public/design/`: exact portraits and SVG assets downloaded through Figma MCP. Astro generates responsive WebP variants of the portraits.
- `public/fonts/`: local Archivo weights 400, 500, 700, and 800, with the SIL Open Font License in `OFL.txt`.
- `public/favicon.svg`: Material Fact favicon.

At the 1440px reference width, the content is 972px wide, standard section padding is 100px, and the hero and conversation sections use a 104px inset and 176px vertical padding. Desktop typography is slightly smaller than the original Figma: 52px hero, 36px section headings, 20px body, 21px profile/row headings, and 17px smaller text. Small labels and mobile typography retain their original sizes; unitless line heights scale with the text. Text remains free to reflow; the page does not use fixed section heights. Mobile and tablet adaptations reduce type and spacing, stack profiles and contact details, and keep the booking button fixed in the bottom-right corner of the viewport while scrolling.

The call button opens https://calendly.com/kyle-materialfact/30min. Both profile and contact links use the supplied individual LinkedIn URLs. Email links open hello@materialfact.io.

## Verification

Production build and headless Chrome checks pass. Browser checks cover widths of 320, 390, 768, 1024, 1440, and 1920px: no horizontal overflow, all images and fonts load, asset dimensions match their layout rules, link destinations are correct, the keyboard skip link works, and no browser JavaScript errors occur. Desktop and mobile screenshots were inspected against the Figma reference.

The dev server is available locally; nothing has been deployed. Temporary browser checks and reference screenshots are kept in ignored `node_modules/.review-tools`.
