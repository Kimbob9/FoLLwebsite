# Friends of Longridge Library website

A simple, fast website made with plain HTML, CSS and JavaScript. It is built to be hosted free on **GitHub Pages**, and designed so that volunteers can update it without any coding knowledge.

## What is in the folder

| File or folder | What it is | Do volunteers edit it? |
|---|---|---|
| `js/content.js` | **News, events, gallery photos, email address, social links** | **Yes, this is the main one** |
| `about.html` | Text of the About us page | Occasionally |
| `index.html` | Home page welcome text | Occasionally |
| `images/gallery/` | Photos for the gallery | Yes (add pictures) |
| `images/logo.jpg` | The group logo | Rarely |
| `css/style.css` | Colours, fonts and layout | Rarely |
| `js/main.js` | Makes the menu, event cards and gallery work | No |
| `events.html`, `gallery.html`, `contact.html`, `404.html` | Page templates | Rarely |

---

## Part 1: Publishing the website for the first time

You only need to do this once. Ask whoever is setting up your GitHub account to follow these steps.

1. **Create a GitHub account** at <https://github.com> (free). Use a shared group email address if you can, so the account does not depend on one person.
2. Click the **+** in the top-right corner, then **New repository**.
3. Name it, for example, `longridge-library-friends`. Choose **Public**. Click **Create repository**.
4. On the new empty repository page, click **uploading an existing file**.
5. Open the website folder on your computer, select **everything inside it** (the `css`, `images` and `js` folders and all the `.html` files) and drag it into the browser window. Wait for the upload to finish.
   - Tip: the `.nojekyll` file is hidden on some computers. If it does not upload, don't worry, the site works without it.
6. Scroll down and click **Commit changes**.
7. Go to **Settings**, then **Pages** (in the left-hand menu).
8. Under **Build and deployment**, set **Source** to **Deploy from a branch**. Under **Branch**, choose **main** and **/ (root)**, then click **Save**.
9. Wait one or two minutes and refresh the page. A green box will appear with your website address, which looks like:
   `https://YOUR-USERNAME.github.io/longridge-library-friends/`

### Using your own web address (optional)

If the group owns a domain name (for example `friendsoflongridgelibrary.org.uk`), go to **Settings, Pages, Custom domain** and follow GitHub's instructions. Your domain provider's help pages explain how to point the domain at GitHub.

---

## Part 2: Updating events

Everything is done in one file: `js/content.js`.

1. On GitHub, open your repository and click the **js** folder, then **content.js**.
2. Click the **pencil icon** (Edit this file) at the top right of the file.
3. Scroll to the section headed **4. UPCOMING EVENTS**.
4. **To add an event**, copy a whole block like this one and paste it just below another event's closing `},`:

   ```js
   {
     date: "2026-11-14",
     time: "10:30am – 12:00pm",
     title: "Coffee and cake morning",
     location: "Longridge Library",
     description: "Pop in for a hot drink, a slice of cake and a natter."
   },
   ```

   Then change the words between the quote marks.
5. **To change an event**, just edit the words in that block.
6. **To remove an event**, delete its whole block from `{` to `},`.
7. Click **Commit changes** (green button, top right), then **Commit changes** again in the box that appears.
8. Wait one or two minutes, then refresh the website.

**Good to know**

- Dates are written **Year-Month-Day** (`"2026-11-14"`), always with two digits for the month and day.
- The day of the week ("Saturday") is added automatically.
- Events **hide themselves** the day after their date, so you never have to clean up. (The sample events will disappear on their own too.)
- Events are shown soonest first, wherever you place them in the file.
- Optional link: add a line `link: { text: "Book a place", url: "https://example.com" },` inside the event. Delete that line if you do not want it.

### Updating news the same way

News is section **3. LATEST NEWS** in the same file. Copy a block, change the `date`, `title` and `text`. The newest three stories appear on the Home page.

### Changing the email address, address or social links

These are in sections **1. SITE DETAILS** and **2. SOCIAL MEDIA LINKS** at the top of `js/content.js`. Replace the placeholder `friends@example.org` and the example Facebook and Instagram addresses with your real ones.

---

## Part 3: Adding photos to the gallery

### Step A: Get the photo ready

- Make sure you have permission to share the photo, and that anyone clearly pictured (especially children) has agreed to it being online.
- Photos straight from a phone are very large and slow the site down. Resize them to about **1600 pixels wide** first. Free tools: *Squoosh* (<https://squoosh.app>), or the Photos app on your computer.
- Give the file a simple name with no spaces, such as `book-sale-oct-2026.jpg`. Use lower case and dashes.
- Landscape (wide) photos look best. All photos are shown in a 4:3 frame.

### Step B: Upload it

1. On GitHub, open your repository, then the **images** folder, then **gallery**.
2. Click **Add file**, then **Upload files**.
3. Drag your photo in, wait for it to finish, then click **Commit changes**.

### Step C: List it

1. Open `js/content.js` and click the pencil icon, as in Part 2.
2. Scroll to **5. PHOTO GALLERY**.
3. Add a new line at the **top** of the list (so newest photos come first):

   ```js
   { src: "images/gallery/book-sale-oct-2026.jpg", alt: "Volunteers selling books from tables in the library", caption: "Autumn book sale, October 2026" },
   ```

   - `src` must match your file name **exactly**, including capital letters and `.jpg`.
   - `alt` describes the photo for people who use screen readers. Please always write something short and helpful.
   - `caption` is the text shown under the photo.
4. Click **Commit changes**.

To remove the grey placeholder pictures, delete their lines from the list (you can also delete the `placeholder-1.svg` to `placeholder-8.svg` files from `images/gallery`).

---

## Part 4: Publishing your changes

Whenever you click **Commit changes** on GitHub, the live website updates by itself after **one to two minutes**. If you do not see your change:

- Refresh the page with **Ctrl + F5** (Windows) or **Cmd + Shift + R** (Mac).
- On GitHub, click the **Actions** tab. A yellow dot means it is still publishing; a green tick means it is done; a red cross means something went wrong (see Troubleshooting below).

### Undoing a mistake

Every change is saved in history. Open the file on GitHub, click **History**, find the last good version and click the `<>` button to view it. You can copy that text back in, or ask a technically minded friend to revert it.

---

## Part 5: Setting up the contact form

GitHub Pages cannot send emails by itself, so the contact form has two modes.

**Out of the box (no setup):** when someone presses *Send message*, their own email app opens with the message ready to send to your group email address. This works but is a little clunky for visitors who do not use an email app.

**Better option: Formspree (free plan available)**

1. Create an account at <https://formspree.io> and click **New form**. Enter your group email address.
2. Formspree gives you a web address like `https://formspree.io/f/abcdwxyz`.
3. Open `js/content.js`, find `contactFormEndpoint: ""` and paste your address between the quotes:

   ```js
   contactFormEndpoint: "https://formspree.io/f/abcdwxyz",
   ```
4. Commit the change. Messages from the form will now arrive in your inbox. The first time, Formspree may ask you to confirm your email address.

---

## Part 6: Editing the page text

The Home and About pages are ordinary HTML. Look for the comments that say `EDIT:` (they appear between `<!--` and `-->`) and change only the words between tags like `<p>` and `</p>`. Leave the angle brackets as they are.

For example, in `about.html`:

```html
<p>The Friends of Longridge Library is a community group of volunteers...</p>
```

Change the sentence, keep the `<p>` and `</p>`.

---

## Trying the site on your own computer

You do not have to publish to see changes. Download the folder, then double-click `index.html` to open it in your browser. Edit `js/content.js` in any plain text editor (such as Notepad or TextEdit in plain-text mode), save, and refresh the browser.

---

## Troubleshooting

**The Events, News or Gallery sections are empty or the menu has vanished.**
There is almost certainly a small typing slip in `js/content.js`. The usual culprits:

- a missing comma at the end of a line or after a closing `}`,
- a missing or extra `"` quote mark,
- a plain double quote `"` used inside a piece of text (use an apostrophe `'` instead).

Compare your edit with the sample blocks, or use GitHub's history to go back to the last working version. Pressing **F12** in your browser and choosing **Console** will usually point to the line with the problem.

**My new photo does not show.**
Check the file name in `src` matches the uploaded file exactly (capital letters count) and that the file is inside `images/gallery`.

**An event is missing.**
Check the date is `Year-Month-Day` and is today or in the future.

**Changes not appearing after five minutes.**
Look at the **Actions** tab for a red cross, and try Ctrl + F5 to clear your browser's saved copy.

---

## Accessibility notes

The site includes a "skip to content" link, clear keyboard focus outlines, high-contrast colours, a readable font (Atkinson Hyperlegible, designed for low vision readers), labelled form fields and a keyboard-friendly photo viewer. To keep it that way:

- Always write a helpful `alt` description for each gallery photo.
- Use clear link text such as "Book a place", not "click here".
- Keep event descriptions short and in plain English.

## Changing colours and fonts

Open `css/style.css`. The colours are listed at the top inside `:root { ... }`, each with a note about what it is used for. Change the six-character codes (for example `#17605c`) to restyle the whole site. Choose dark colours for text and backgrounds with plenty of contrast.
