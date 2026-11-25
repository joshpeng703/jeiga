# How to edit your website (no coding experience needed)

Your website is two text files plus a folder of photos:

- **index.html** holds all the *words* on your site. This is the file you'll edit.
- **style.css** controls how it *looks* (colours, font, spacing, photo grid). You can mostly ignore it.
- **posts/** holds any writing you publish on the site itself. TEMPLATE.html is a blank post to copy.
- **photos/** is the folder your pictures go in. The ones there now are grey examples to delete once you add your own.

## 1. Seeing the site on your own computer

1. Keep index.html, style.css and the photos folder together in one folder.
2. Double-click **index.html**. It opens in your web browser. That's your site.
3. After you edit and save a file, refresh the browser tab to see the change.

To edit, open the file in any plain text editor. On a Mac, TextEdit works if you first choose *Format → Make Plain Text*. On Windows, Notepad works. A free editor like **VS Code** colours the code so it's easier to read, but it's optional.

## 2. The only rule you need: tags come in pairs

HTML wraps text in **tags**, which are words in angle brackets. Most come in an opening and closing pair:

```html
<p>This is a paragraph.</p>
```

`<p>` opens, `</p>` (with a slash) closes. **Change the words between the tags, and leave the tags alone.** That's 90% of editing.

The tags you'll see:

| Tag | Means |
|---|---|
| `<h1>` | Your name at the top |
| `<h2>` | A section heading |
| `<p>` | A paragraph |
| `<li>` | One item in a list |
| `<a href="...">` | A link. The address goes inside the quotes, the clickable words go between the tags |
| `<!-- ... -->` | A note to you. It never shows on the site |

## 3. Common edits

**Replace placeholder text.** Anything grey and italic on the site starts with `[PLACEHOLDER]`. Find it in index.html, type your own words over it, and delete ` class="placeholder"` from that tag so it turns into normal black text. Before and after:

```html
<p class="placeholder">[PLACEHOLDER] Write a few sentences about who you are...</p>
<p>I'm a safety engineer based in Toronto.</p>
```

**Add a paragraph.** Copy a whole `<p>...</p>` line, paste it underneath, and change the words.

**Add an item to any list** (like Work links or Contact details). Copy a whole `<li>...</li>` line, paste it underneath, and change the words and link.

**Add a piece of writing to Safetyisms.** Each entry in the Writing list is a block that starts with `<article class="entry">` and ends with `</article>`. Copy the whole block, paste it at the top of the list so the newest is first, then change the title, date, summary and link.

- If the piece lives somewhere else (Substack, Medium, LessWrong, a paper), just put that web address in the link.
- If you want it to live on your own site: copy **posts/TEMPLATE.html**, rename the copy to something simple like `posts/my-first-post.html`, write your post in it, and point the link at `posts/my-first-post.html`. The template has notes showing where everything goes.

**Change your email.** In the Contact section, change `you@example.com` in *both* spots on that line (one is the link, one is the visible text).

**Change a colour or font.** Open style.css and look for lines marked `EDIT`. Colours are written as codes like `#2f5d50`. Search "colour picker" online to find codes you like.

## 4. Photos

### Step 1: Shrink the photo first

Photos straight off a phone or camera are often 3 to 10 MB each, which makes the site slow. Shrink each one to about **1600 pixels on its longest side** before adding it. It still looks sharp on a big screen, but it's roughly 10 times smaller. Any of these work:

- **Any computer, free:** go to **squoosh.app** in your browser, drag the photo in, tick *Resize* and set width to 1600, pick *MozJPEG* with quality around 75, then click the download button.
- **Mac:** open the photo in Preview, choose *Tools → Adjust Size*, set the width to 1600, then *File → Export* as JPEG.
- **Windows:** open the photo in the Photos app, click the *…* menu, choose *Resize image*, and pick a smaller size.

Aim for each file to end up under about 500 KB.

Also give the file a simple name with no spaces, like `harbour-sunset.jpg`. Spaces and capital letters in file names are a common cause of "my photo doesn't show up".

### Step 2: Add it to the grid

1. Put the file in the **photos** folder.
2. In index.html, find the Photos section. Copy one whole `<img ...>` line and paste it where you want the photo to appear. Order in the file is order on the page.
3. Change the file name and the description:

```html
<img src="photos/harbour-sunset.jpg" alt="Sunset over the harbour">
```

The `alt` description is read aloud to visitors who use screen readers, so write a few words about what's in the photo.

To **remove** a photo, delete its `<img ...>` line. To **reorder**, cut and paste lines.

### Step 3 (optional): Customise the grid

Every photo is shown as a neat square tile, cropped to fit, so mixed shapes still line up. You can change the layout in two safe ways:

- **Make one photo bigger:** add a size to its line. `class="wide"` makes it 2 tiles wide, `class="tall"` makes it 2 tiles tall, and `class="big"` makes it both. The grid fills in any gaps around it automatically.

```html
<img src="photos/harbour-sunset.jpg" alt="Sunset over the harbour" class="big">
```

- **Change how many photos sit side by side:** in style.css, find `--photo-columns: 3;` and change the 3 to 2 or 4. You can also change `--photo-gap` for more or less space between photos. On phones it always switches to 2 per row so photos stay a decent size.

Because these are the only knobs, you can't really break the layout by playing with them. If something looks odd, change the number back.

## 5. If something breaks

Usually it's a missing `<`, `>`, `/` or quote mark. Undo (Ctrl+Z / Cmd+Z) until it looks right again. Keeping a copy of the folder before big changes is a good habit.

## 6. Putting it online (GitHub Pages)

Your site lives in the GitHub repository **joshpeng703/jeiga** and is published at **https://joshpeng703.github.io/jeiga/**.

You don't need your computer at all to edit. Go to your files on github.com, click a file, click the **pencil icon**, make your change, then click **Commit changes**. To add a photo, open the photos folder on github.com and click **Add file → Upload files**. The live site updates about a minute later.

## 7. Using your own domain name (like yourname.com)

GitHub Pages supports your own domain for free, including the padlock (HTTPS). You buy the domain from a domain seller (a "registrar") and point it at GitHub. Claude won't buy anything for you.

1. **Buy the domain** from a registrar such as Cloudflare, Porkbun or Namecheap. Expect roughly $10 to $20 a year for a .com. Watch for cheap first-year prices that jump at renewal.
2. **Tell GitHub the domain.** On github.com, open your site's repository, go to *Settings → Pages*, type your domain under *Custom domain* (for example `www.yourname.com`) and click Save.
3. **Point the domain at GitHub.** In your registrar's DNS settings, add these records:

| Type | Name / Host | Value |
|---|---|---|
| CNAME | `www` | `YOUR-GITHUB-USERNAME.github.io` |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |

   The CNAME line makes `www.yourname.com` work. The four A lines make plain `yourname.com` work too.
4. **Wait, then turn on the padlock.** DNS changes can take anywhere from minutes to a day. Once GitHub shows a green tick, tick *Enforce HTTPS* on the same Settings page.
5. **Recommended: verify the domain** under your GitHub account's *Settings → Pages*. This stops anyone else from ever attaching your domain to their own site.
