# Adding yourself to the Associates page

The [Associates page](https://www.farfetched.ltd/associates/) lists the people and businesses that work with Far Fetched. Each one has a photo or logo and a short blurb. You add your own entry through a pull request, and Jesse reviews it before it goes live.

The repository is public, so anything you commit is visible straight away, even before it reaches the live site.

## Before you start

1. **Get access.** Send Jesse your GitHub username. He adds you to this repository with write access. You can't push a branch until he does.
2. **Have these ready:**
   - **A headshot:** a portrait at least 600px wide, ideally head and shoulders. If you're adding a business, a logo instead (SVG or transparent PNG).
   - **A blurb:** two or three sentences, about 60 words at most.
   - **Optional:** your title and company, a one-line description of how you work with Far Fetched, the sectors you work in, and your LinkedIn and website links.

Photos are cropped to portrait shape and given a blue tint to match the site, and they return to full colour on hover. You don't need to edit your photo first.

## Option A: use a coding agent

Paste the prompt below into Claude Code, Cursor, Copilot or a similar agent. It asks you for everything it needs.

````markdown
Add me to the Associates page of the Far Fetched website, then open a pull request.

## Repository
- Repo: https://github.com/far-fetched-labs/farfetched-website
- Base branch: `feature/associates-page` (the default branch). Clone it, then create a branch called `associate/<my-name-slug>`.
- It's a Jekyll site. The source is in `docs/`.
- Roster data: `docs/_data/associates.yml`. Read the comment block at the top of this file first. It defines every field.
- Images go in `docs/assets/associates/`. Create the folder if it doesn't exist.

## Ask me for these before you edit anything
1. Is this entry for a **person** or a **business**?
2. The image file: a headshot for a person, or a logo for a business.
3. Name, as it should appear on the page.
4. Role. For a person, a title (e.g. "Fractional CFO"). For a business, what it does.
5. Company (people only, optional).
6. How I work with Far Fetched (optional), e.g. "Delivery partner".
7. Sectors (optional), e.g. iGaming, Fintech.
8. Blurb: two or three sentences, about 60 words at most. Offer to tighten my draft, but show me the final text before you commit it.
9. LinkedIn URL and website URL (optional).

## Rules
- Add **one** new entry at the end of the `people` or `businesses` list. Don't edit, reorder or remove any other entry, including entries marked `sample: true`.
- Leave out any field I don't give you. Never invent details, claims or links.
- Headshots:
  - Save as `docs/assets/associates/<name-slug>.jpg` (or `.webp`): at least 600px wide, under about 400 KB. Resize or compress if needed and tell me what you changed.
  - Remove EXIF and GPS metadata.
  - Don't crop or recolour the image yourself; the page does that. If my face isn't roughly centred, set `image_position` (e.g. `"60% 20%"`).
- Logos:
  - Save as `docs/assets/associates/<name-slug>.svg` or `.png`, with a transparent background.
  - If the logo is dark, set `logo_background: light`.
- Set `image:` to the site path, e.g. `/assets/associates/jane-doe.jpg`.
- Change no files except the YAML entry and the one image.

## Check before opening the PR
- Make sure the YAML is valid, e.g. `ruby -ryaml -e 'YAML.load_file("docs/_data/associates.yml")'`.
- If Ruby and Bundler are installed, run `bundle install`, then `bundle exec jekyll serve --source docs` from the repo root. Open http://127.0.0.1:4000/associates/ and check my entry on a desktop-width window and a phone-width window. If you can't run it, say so in the PR.

## Pull request
- Target `feature/associates-page` in `far-fetched-labs/farfetched-website`. Don't target `main`, and don't target any other repository.
- Title: `Add <Name> to associates`
- Body: the entry exactly as it will appear, plus any image changes you made.
- Tell me the PR link when it's open.
````

## Option B: do it by hand

1. Create a branch from `feature/associates-page` called `associate/<your-name>`, e.g. `associate/jane-doe`.
2. Add your image to `docs/assets/associates/`, named after you:
   - **Headshot:** `jane-doe.jpg`, at least 600px wide and under about 400 KB, with location metadata removed.
   - **Logo:** `acme.svg`, or a `.png` with a transparent background.
3. Add your entry to the end of the `people` or `businesses` list in `docs/_data/associates.yml`. The comments at the top of that file explain every field. Leave out any field you don't need. Don't change anyone else's entry. A person entry looks like this:

   ```yaml
     - name: Jane Doe
       image: /assets/associates/jane-doe.jpg
       role: Fractional CFO
       company: Example Ltd
       relationship: Delivery partner
       sectors: [iGaming, Fintech]
       blurb: >-
         Two or three sentences on what you do and how you work with
         Far Fetched, in about 60 words at most.
       linkedin: https://www.linkedin.com/in/janedoe
       website: https://example.com
   ```

4. Optional: preview the site by running `bundle install` and then `bundle exec jekyll serve --source docs`, and open http://127.0.0.1:4000/associates/.
5. Open a pull request into `feature/associates-page`, titled `Add <Your Name> to associates`.

## What happens next

Jesse reviews your pull request and may suggest changes to the wording. Once he approves it, it merges here. Jesse then copies the approved entries into the main site repository and publishes them to www.farfetched.ltd.

Questions: [info@farfetched.ltd](mailto:info@farfetched.ltd)
