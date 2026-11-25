# How to edit your website (no coding experience needed)

Each section of your site is its own page, and each page is its own file. These hold the *words* and are the files you'll edit:

| File | Page | Notes |
|---|---|---|
| **index.html** | About | Your home page. Browsers automatically open the file called `index.html` when someone visits your address, which is why About is what visitors see first. |
| **contact.html** | Contact | |
| **photos.html** | Photos | Your photo grid. |
| **safetyisms.html** | Safetyisms | Your writing and work links. |

Then there are the supporting files:

- **style.css** controls how it *looks* (colours, font, spacing, photo grid). You can mostly ignore it.
- **posts/** holds any writing you publish on the site itself. TEMPLATE.html is a blank post to copy.
- **CNAME** holds just your domain name (joshpeng.com). GitHub uses it to know which address belongs to this site. Leave it alone.
- **photos/** is the folder your pictures go in. The ones there now are grey examples to delete once you add your own.

## 1. Seeing the site on your own computer

1. Keep all the files and folders together in one folder, exactly as they are.
2. Double-click **index.html**. It opens your home page in your web browser, and the menu links take you to the other pages.
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

**Replace placeholder text.** Anything grey and italic on the site starts with `[PLACEHOLDER]`. Find it in that page's file (see the table at the top), type your own words over it, and delete ` class="placeholder"` from that tag so it turns into normal black text. Before and after:

```html
<p class="placeholder">[PLACEHOLDER] Write a few sentences about who you are...</p>
<p>I'm a safety engineer based in Toronto.</p>
```

**Add a paragraph.** Copy a whole `<p>...</p>` line, paste it underneath, and change the words.

**Add an item to any list** (like Work links or Contact details). Copy a whole `<li>...</li>` line, paste it underneath, and change the words and link.

**Add a piece of writing to Safetyisms.** Open **safetyisms.html**. Each entry in the Writing list is a block that starts with `<article class="entry">` and ends with `</article>`. Copy the whole block, paste it at the top of the list so the newest is first, then change the title, date, summary and link.

- If the piece lives somewhere else (Substack, Medium, LessWrong, a paper), just put that web address in the link.
- If you want it to live on your own site: copy **posts/TEMPLATE.html**, rename the copy to something simple like `posts/my-first-post.html`, write your post in it, and point the link at `posts/my-first-post.html`. The template has notes showing where everything goes.

**Change your email.** In **contact.html**, change `you@example.com` in *both* spots on that line (one is the link, one is the visible text).

**Change your name or the menu.** The top of every page (your name and the menu) is copied into each of the four page files. That keeps each file simple and self-contained, but it means that if you change your name or rename a menu link, you need to make the same change in all four files.

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
2. Open **photos.html**. Copy one whole `<img ...>` line and paste it where you want the photo to appear. Order in the file is order on the page.
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

## 7. Connecting joshpeng.com with Cloudflare, step by step

### First, what's actually going on

When someone types **joshpeng.com** into a browser, their computer doesn't know where your site is. It needs a number, called an **IP address**, which is the internet's version of a street address for a specific computer. The **Domain Name System (DNS)** is the internet's phone book: it turns names like joshpeng.com into those numbers. DNS was designed in the 1980s so people wouldn't have to remember numbers (Mockapetris, *RFC 1034: Domain Names, Concepts and Facilities*, 1987).

Your site's files sit on GitHub's computers. So the whole job is:

1. **Own the name** (buy it from Cloudflare).
2. **Write phone-book entries** (DNS records at Cloudflare) saying "joshpeng.com lives at GitHub's address".
3. **Tell GitHub to expect visitors** for joshpeng.com, so it knows to serve your site when they arrive.

### Part A: Buy the domain on Cloudflare

1. Go to **dash.cloudflare.com** and log in (or click *Sign up* to make a free account).
2. In the menu on the left, click **Domain Registration**, then **Register Domains**. Cloudflare sometimes reshuffles its menus. If you don't see that, look for a section just called **Domains**, or type "register" into the search box at the top.
3. Type `joshpeng.com` into the search box and press Enter.
4. If it says it's available, click **Purchase** (or the price button next to it). Cloudflare sells domains at the price they pay for them, so a .com is roughly $10 to $11 a year, and renewals cost the same.
5. Fill in your contact details. **Why:** every domain owner has to register contact details with the body that runs domain names. Cloudflare hides them from the public list for free ("WHOIS privacy"), so strangers can't look up your home address.
6. Pay. Auto-renew is on by default, and it's worth leaving on. If a domain lapses, someone else can buy it.
7. When it finishes, joshpeng.com shows up in your Cloudflare account list. Because you bought it from Cloudflare, Cloudflare also runs its phone book (DNS) automatically, so there's nothing else to connect.

### Part B: Add the DNS records (the phone-book entries)

1. On the Cloudflare dashboard home page, click **joshpeng.com** in your list of domains.
2. In the left menu, click **DNS**, then **Records**.
3. If anything is already listed there, look at it. A brand-new domain is usually empty. If you see A or CNAME records you didn't create, delete them using *Edit → Delete*, because they'd clash with the ones below.
4. Click **Add record**. A small form appears with these boxes: *Type*, *Name*, *IPv4 address* (or *Target*), *Proxy status*, *TTL*.
5. Fill it in like this:
   - **Type:** `A`. An "A record" means "this name points to this IP address". The A stands for "address".
   - **Name:** `@`. The `@` symbol is shorthand for "the domain itself", i.e. plain joshpeng.com with nothing in front.
   - **IPv4 address:** `185.199.108.153`. This is one of GitHub Pages' public addresses. "IPv4" is the classic style of IP address, four numbers from 0 to 255 separated by dots.
   - **Proxy status:** click the orange cloud so it turns **grey** and says **DNS only**. This one matters, see the note below.
   - **TTL:** leave it on **Auto**. TTL ("time to live") is how long other computers may remember this answer before asking again.
6. Click **Save**.
7. Repeat steps 4 to 6 three more times, changing only the address:
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`

   **Why four?** They're four separate entry points into GitHub's network. If one is busy or down, browsers try another, so your site stays up. All four lead to the same place. GitHub publishes these exact numbers in its documentation, and they're the same for everyone who uses GitHub Pages. They aren't secret or specific to you.
8. Click **Add record** once more for the "www" version:
   - **Type:** `CNAME`. A CNAME ("canonical name") says "this name is just another name for that other name". Instead of pointing to a number, it points to another domain, which then gets looked up as normal.
   - **Name:** `www`. This covers www.joshpeng.com.
   - **Target:** `joshpeng703.github.io`. That's your GitHub Pages address, so www.joshpeng.com follows wherever GitHub says that lives.
   - **Proxy status:** grey cloud, **DNS only**.
   - **TTL:** Auto.
9. Click **Save**. You should now see five rows: four A rows and one CNAME row, all with grey clouds.

**Why the grey cloud matters:** with the orange cloud on, Cloudflare stands in the middle and answers visitors itself, hiding GitHub. GitHub then can't confirm you own the domain and can't issue the security certificate that gives you the padlock (https). Grey means Cloudflare just gives out the address, and visitors go straight to GitHub.

### Part C: Tell GitHub about the domain

1. Go to **github.com/joshpeng703/jeiga**.
2. Click **Settings** in the row of tabs near the top. It has a gear icon and is the last tab on the right.
3. In the left menu, click **Pages**.
4. Find the **Custom domain** box, type `joshpeng.com`, and click **Save**.
   **What happens:** GitHub adds a tiny file called `CNAME` to your site's files. It contains just your domain, and it tells GitHub "requests for joshpeng.com should get this site". You'll see it appear in your file list. Leave it there.
5. GitHub now runs a **DNS check**. It looks up joshpeng.com in the phone book to see whether it points at GitHub. Right after adding the records it may say the check is in progress or failed. That's normal, because the internet's copies of the phone book take time to update ("propagation"). With Cloudflare this is often a few minutes, but it can take up to 24 hours.
6. When it shows a green tick ("DNS check successful"), tick **Enforce HTTPS**. If the box is greyed out, GitHub is still getting your certificate. Wait a while and refresh.
   **What happens:** GitHub gets a free security certificate for joshpeng.com from Let's Encrypt, a non-profit that issues them. The certificate is what makes browsers show the padlock and encrypt the connection. "Enforce" means anyone who types the insecure `http://` gets moved to the secure version.
7. Visit **https://joshpeng.com**. Your site should appear. www.joshpeng.com and the old joshpeng703.github.io/jeiga address will both forward there.

### Part D (optional but recommended): Verify the domain with GitHub

This proves to GitHub, at the account level, that you own joshpeng.com. If the site is ever switched off, nobody else on GitHub can then attach your domain to their own site.

1. On GitHub, click your **profile picture** (top right), then **Settings**. This is your *account* settings, not the repository's.
2. In the left menu, click **Pages** (under "Code, planning, and automation").
3. Click **Add a domain**, type `joshpeng.com`, and click **Add domain**.
4. GitHub shows you a **TXT record**: a name that starts with `_github-pages-challenge-joshpeng703` and a long random value. A TXT record is a phone-book entry that just holds text. Here it works like a password GitHub asks you to post publicly to prove you control the domain.
5. In Cloudflare, go to **DNS → Records → Add record**. Choose **Type:** `TXT`, paste the **Name** and the **Content** exactly as GitHub shows them, and click **Save**.
6. Back on GitHub, click **Verify**. If it fails, wait a few minutes and try again.
