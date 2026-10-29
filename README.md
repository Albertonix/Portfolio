# Tony Albert Portfolio

Portfolio website of **Tony Albert**, a motion designer and graphic designer in Hyderabad, India, with 7+ years of experience.
It holds 20 projects: product films, app explainers, brand reveals and social reels.

- Instagram: [@tonyalbertx](https://www.instagram.com/tonyalbertx/)
- Behance: [behance.net/tonyalbert3](https://www.behance.net/tonyalbert3)
- LinkedIn: [Tony Albert](https://www.linkedin.com/in/tony-albert-72405b190/)
- Email: tony31071998@gmail.com

## Put it online with GitHub Pages

1. Sign in to GitHub and create a new **public** repository, for example `portfolio`.
   If you name it `<your-username>.github.io`, the site lives at `https://<your-username>.github.io/` with no extra path.
2. Open the new repository and click **Add file → Upload files**.
3. Drag in **everything inside this folder**: `index.html`, `assets`, `Tony_Albert_Portfolio.pdf`, `README.md`, `.nojekyll` and `.gitignore`.
   Drag the files themselves, not the folder that holds them, so `index.html` sits at the top level of the repository.
   The `.nojekyll` and `.gitignore` files are hidden on Mac and Windows. Show hidden files to see them. The site still works if they're missing.
4. Click **Commit changes**. The upload is about 71 MB, so give it a minute.
5. Go to **Settings → Pages**. Under **Build and deployment**, set Source to **Deploy from a branch**, Branch to **main**, and folder to **/ (root)**. Click **Save**.
6. After a minute or two, the site is live at `https://<your-username>.github.io/<repository-name>/`.

**Limits:** GitHub's web uploader accepts files up to 25 MB and 100 files per upload. Every file here fits, and the largest video is about 13 MB.

### Link previews (optional)
Once the site is live, open `index.html` and change the `og:image` line to the full address, so WhatsApp, LinkedIn and others show a preview card:

```html
<meta property="og:image" content="https://<your-username>.github.io/<repository-name>/assets/images/og-cover.jpg">
```

### Custom domain (optional)
Buy a domain such as `tonyalbert.in`, then add it under **Settings → Pages → Custom domain** and follow GitHub's DNS instructions.

## Folder structure

```
index.html                  page structure and text
Tony_Albert_Portfolio.pdf   PDF version, linked from the site
assets/
  css/style.css             all styling, including light and dark themes
  js/main.js                project list, timeline, filters and video player
  videos/                   20 project videos (H.264, web-compressed)
  images/                   video thumbnails, favicon and social preview image
.nojekyll                   tells GitHub Pages to serve the files as they are
```

## Add a new project

1. Compress the video:
   ```
   ffmpeg -i input.mp4 -vf "scale='if(gt(iw,ih),min(1280,iw),-2)':'if(gt(iw,ih),-2,min(1280,ih))'" -c:v libx264 -preset veryfast -crf 26 -pix_fmt yuv420p -movflags +faststart -c:a aac -b:a 128k assets/videos/newproject.mp4
   ```
2. Save a still frame as the thumbnail:
   ```
   ffmpeg -ss 3 -i assets/videos/newproject.mp4 -frames:v 1 -q:v 4 assets/images/newproject.jpg
   ```
3. In `assets/js/main.js`, add an entry to the `var P=[` list:
   ```js
   {id:"newproject",cat:"motion",title:"Project Title",client:"Short label",w:1080,h:1920,dur:30,
    video:"assets/videos/newproject.mp4",poster:"assets/images/newproject.jpg",
    desc:"One or two sentences about the project.",tags:["Tag","Tag","9:16"]},
   ```
   - `cat` is `motion`, `edit` or `design`.
   - `w`, `h` and `dur` are the video's width, height and length in seconds.
   - Projects appear in the order they're listed.

   The timeline, filters, counts and stats update on their own.
4. Upload the changed files to GitHub. The live site updates within a minute or two.

## Built with
Plain HTML, CSS and JavaScript, with no build step or framework.
Fonts come from Google Fonts: Big Shoulders Display, Instrument Sans and JetBrains Mono.
