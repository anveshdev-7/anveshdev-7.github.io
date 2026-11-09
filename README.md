# Anvesh Dev: portfolio website

A single-page portfolio with an interactive 3D hero, animated background, smooth scrolling,
a custom cursor, light and dark themes, and a Gmail contact card. It is plain HTML, CSS and
JavaScript, so there is no build step.

## Put it online
Upload `index.html` **and the `assets` folder together**, side by side, to your hosting
(File Manager, FTP, or a free host). If the `assets` folder is missing, the logo and the
project images will not show.

Free options: **Netlify Drop** (app.netlify.com/drop, drag this whole folder onto the page),
GitHub Pages, or Vercel.

## What is in the folder
- `index.html`: the whole site. The styles and scripts are inside it.
- `assets/logo/`: your logo. `*-for-dark.webp` is the light version shown in dark mode and
  `*-for-light.webp` is the dark version shown in light mode. `mark-*` is the small AD symbol in
  the header. `logo-*` is the full logo used in the footer and the mobile menu.
- `favicon.ico` and `assets/icons/`: your logo as the browser-tab icon (`favicon.ico`, `icon-32.png`,
  `icon-192.png`) and the home-screen icon for iPhones (`apple-touch-icon.png`).
- `assets/og-image.jpg`: the picture shown when someone shares your link on WhatsApp, LinkedIn, X,
  Facebook, Telegram and similar apps (1200 x 630 pixels, your logo on a dark background).
- `assets/projects/`: the three sample project previews, each in two sizes (`-640` for phones,
  `-1280` for larger screens).

## Your web address (link preview picture)
The link-preview lines near the top of `index.html` (`og:url`, `og:image`, `twitter:image`) already
point to `https://anveshdev-7.github.io/`. Upload the whole folder to the **root** of your
GitHub Pages repository (`index.html`, `favicon.ico` and `assets` side by side) so that
`https://anveshdev-7.github.io/assets/og-image.jpg` opens in the browser. If you later move to a
custom domain, replace `anveshdev-7.github.io` in those three lines.

After you upload, test the preview with the Facebook Sharing Debugger or LinkedIn Post Inspector.
Apps keep an old preview for days, and those two tools make them fetch the new one. Browsers also
cache tab icons, so you may need a hard refresh (Ctrl+Shift+R) or a new tab to see the new one.

## Edit it
- **Real projects:** replace the images in `assets/projects/` with screenshots of your own work,
  keeping the same file names. Make both sizes (640 and 1280 pixels wide, 16:10 shape works best).
  Then edit the text in the "Selected work" section of `index.html`: title, description, tech tags
  and the "Live site" line. The cards say "Placeholder" until you change them.
- **Clients:** in the "Who I build for" section, the rounded labels describe the kinds of clients
  you want. The three dashed cards are open slots. When you have a real client who agreed to be
  listed, replace "Your business could be here" with their name and "Open client slot 1" with what
  you built for them. Delete the small note below the cards once your slots are filled.
- **Social links:** near the bottom of `index.html`, find `var SOCIALS = [];` and add entries like
  `{ label: "GitHub", url: "https://github.com/your-name" }`.
- **Email:** the address appears in the Contact section (search for `anveshnikam95@gmail.com`; it is
  also inside the Gmail button's link). Change both if the address ever changes.
- **Skills:** edit the "How I work" section and add the specific tools you can confirm.
- **Colours:** the design tokens are at the top of the `<style>` block (`--bg`, `--fg`, `--accent`).
  Dark is the default. The light theme follows the visitor's system setting and the header toggle.

## Speed notes
Already done in the code: images are lazy-loaded with fixed sizes (no layout shift), fonts load
without blocking the first paint, the smooth-scroll library loads after the page and only on
desktop, the animations use only `transform` and `opacity`, and the heavy canvas effects run in a
lighter mode on phones and pause when off screen. The 3D hero shape is not shown or loaded at all
on phones (screens under 768 pixels wide), so phones get a clean headline and less work to do.

Optional, on Apache or LiteSpeed hosting: add these lines to your `.htaccess` file (add them to the
existing file; do not replace it). They turn on compression and caching, which PageSpeed rewards.

    <IfModule mod_deflate.c>
      AddOutputFilterByType DEFLATE text/html text/css application/javascript image/svg+xml
    </IfModule>
    <IfModule mod_expires.c>
      ExpiresActive On
      ExpiresByType image/webp "access plus 1 month"
    </IfModule>

If you replace an image and keep its name, visitors may see the old one for a while because of
caching. Giving the new file a new name (for example `landing-page-v2-1280.webp`) avoids that.

## Notes
- The Contact section opens a Gmail draft addressed to you. There is no form and no third-party service.
- Animations respect the visitor's "reduce motion" setting.
