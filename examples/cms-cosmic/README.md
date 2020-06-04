# A statically generated blog example using Next.js and Cosmic

This example showcases Next.js's [Static Generation](https://nextjs.org/docs/basic-features/pages) feature using [Cosmic](https://cosmicjs.com/) as the data source.

## Demo

[https://cosmic-nextjs-blog.now.sh/](https://cosmic-nextjs-blog.now.sh/)

### Related examples

- [Blog Starter](/examples/blog-starter)
- [Sanity](/examples/cms-sanity)
- [TakeShape](/examples/cms-takeshape)
- [Prismic](/examples/cms-prismic)

## How to use

### Using `create-next-app`

Execute [`create-next-app`](https://github.com/zeit/next.js/tree/canary/packages/create-next-app) with [npm](https://docs.npmjs.com/cli/init) or [Yarn](https://yarnpkg.com/lang/en/docs/cli/create/) to bootstrap the example:

```bash
npm init next-app --example cms-cosmic cms-cosmic-app
# or
yarn create next-app --example cms-cosmic cms-cosmic-app
```

### Download manually

Download the example:

```bash
curl https://codeload.github.com/zeit/next.js/tar.gz/canary | tar -xz --strip=2 next.js-canary/examples/cms-cosmic
cd cms-cosmic
```

## Configuration

### Step 1. Create an account and a project on Cosmic

First, [create an account on Cosmic](https://cosmicjs.com).

### Step 2. Install the Next.js Static Blog

After creating an account, install the [Next.js Static Blog](https://www.cosmicjs.com/apps/nextjs-static-blog) from the Cosmic App Marketplace.

### Step 3. Set up environment variables

Go to the **Settings** menu at the sidebar and click **Basic Settings**.

Then copy the **Bucket slug** and **Read Key**.

Next, copy the `.env.example` file in this directory to `.env` (which will be ignored by Git):

```bash
cp .env.example .env
```

Then set each variable on `.env`:

- `NEXT_EXAMPLE_CMS_COSMIC_BUCKET_SLUG` should be the Bucket slug you just copied.
- `NEXT_EXAMPLE_CMS_COSMIC_READ_KEY` should be the Read Key you just copied.
- `NEXT_EXAMPLE_CMS_COSMIC_PREVIEW_SECRET` can be any random string (but avoid spaces), like `Read Key` - this is used for [the Preview Mode](https://nextjs.org/docs/advanced-features/preview-mode).

Your `.env` file should look like this:

```bash
NEXT_EXAMPLE_CMS_COSMIC_BUCKET_SLUG=...
NEXT_EXAMPLE_CMS_COSMIC_READ_KEY=...
NEXT_EXAMPLE_CMS_COSMIC_PREVIEW_SECRET=...
```

### Step 4. Run Next.js in development mode

```bash
npm install
npm run dev

# or

yarn install
yarn dev
```

Your blog should be up and running on [http://localhost:3000](http://localhost:3000)! If it doesn't work, post on [GitHub discussions](https://github.com/zeit/next.js/discussions).

### Step 5. Add preview link

To add the ability to preview content from your Cosmic dashboard go to <i>Posts > Edit Settings</i> and scroll down to the "Preview Link" section. (Screenshot below)
![Image](https://cdn.cosmicjs.com/14e6c0f0-a07b-11ea-829b-5b458b05d525-preview-link.png)

Add your live URL or localhost development URL which includes your chosen preview secret and `[object_slug]` shortcode. It should look like the following:

```
http://localhost:3000/api/preview?secret=<secret>&slug=[object_slug]
```

- `<secret>` is the string you entered for `NEXT_EXAMPLE_CMS_COSMIC_PREVIEW_SECRET`.
- `[object_slug]` shortcode will automatically be converted to the post's `slug` attribute.

On Cosmic, go to one of the posts you've created and:

- **Update the title**. For example, you can add `[Draft]` in front of the title.
- Click **Save Draft**, but **DO NOT** click **Publish**. By doing this, the post will be in the draft state.

Now, if you go to the post page directly on localhost, you won't see the updated title. However, if you use the **Preview Mode**, you'll be able to see the change ([Documentation](https://nextjs.org/docs/advanced-features/preview-mode)).

Next, click the Preview Link button on the Post to see the updated title. To exit the preview mode, you can click **Click here to exit preview mode** at the top. (Screenshot below)

<img src="https://cdn.cosmicjs.com/80f42680-a07a-11ea-829b-5b458b05d525-preview-button.png" width="300" />

### Step 6. Deploy on Vercel

You can deploy this app to the cloud with [Vercel](https://vercel.com/import?filter=next.js&utm_source=github&utm_medium=readme&utm_campaign=next-example) ([Documentation](https://nextjs.org/docs/deployment)).

To deploy on Vercel, you need to set the environment variables with **Now Secrets** using [Vercel CLI](https://vercel.com/download) ([Documentation](https://vercel.com/docs/now-cli#commands/secrets)).

Install [Vercel CLI](https://vercel.com/download), log in to your account from the CLI, and run the following commands to add the environment variables. Replace `<NEXT_EXAMPLE_CMS_COSMIC_BUCKET_SLUG>`, `<NEXT_EXAMPLE_CMS_COSMIC_READ_KEY>` and `<NEXT_EXAMPLE_CMS_COSMIC_PREVIEW_SECRET>` with the corresponding strings in `.env`.

```
vercel secrets add next_example_cms_cosmic_bucket_slug <NEXT_EXAMPLE_CMS_COSMIC_BUCKET_SLUG>
vercel secrets add next_example_cms_cosmic_read_key <NEXT_EXAMPLE_CMS_COSMIC_READ_KEY>
vercel secrets add next_example_cms_cosmic_preview_secret <NEXT_EXAMPLE_CMS_COSMIC_PREVIEW_SECRET>
```

Then push the project to GitHub/GitLab/Bitbucket and [import to Vercel](https://vercel.com/import?filter=next.js&utm_source=github&utm_medium=readme&utm_campaign=next-example) to deploy.