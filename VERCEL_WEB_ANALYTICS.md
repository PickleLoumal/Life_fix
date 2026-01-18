# Vercel Web Analytics Implementation

This project has integrated **Vercel Web Analytics** to track visitor behavior and page views. This guide explains the setup, how it's implemented, and how to manage it.

## Overview

Vercel Web Analytics provides real-time insights into your website's performance and user behavior. This project uses the HTML implementation for plain HTML/static sites.

## Prerequisites

- A Vercel account ([sign up for free](https://vercel.com/signup))
- A Vercel project ([create a new project](https://vercel.com/new))
- The Vercel CLI (install with: `npm i -g vercel`, `pnpm i -g vercel`, `yarn global add vercel`, or `bun i -g vercel`)

## Setup Instructions

### Step 1: Enable Web Analytics in Vercel Dashboard

1. Go to your [Vercel dashboard](/dashboard)
2. Select your project
3. Click the **Analytics** tab
4. Click **Enable** in the dialog

> **Note:** Enabling Web Analytics will add new routes (scoped at `/_vercel/insights/*`) after your next deployment.

### Step 2: Current Implementation

This project uses the **HTML/static site implementation** of Vercel Web Analytics. The following code has been added to `index.html`:

```html
<!-- Vercel Web Analytics -->
<script>
    window.va = window.va || function () { (window.vaq = window.vaq || []).push(arguments); };
</script>
<script defer src="/_vercel/insights/script.js"></script>
```

This is placed in the `<head>` section of the HTML file and is minimal and non-intrusive.

### Step 3: Deploy Your Application

Deploy your app to Vercel using:

```bash
vercel deploy
```

Or, if you've connected your Git repository, simply push to your main branch. Vercel will automatically deploy your latest commits.

Once deployed, the analytics script will start tracking visitors and page views.

## Monitoring Your Analytics

### Real-time Monitoring

1. After deployment, you can verify the analytics script is working by:
   - Opening your deployed site in a browser
   - Opening the **Network** tab in Developer Tools
   - Looking for a `Fetch/XHR` request to `/_vercel/insights/view`

### Dashboard

To view your analytics data:

1. Go to your [Vercel dashboard](/dashboard)
2. Select your project
3. Click the **Analytics** tab
4. Explore your data by viewing and [filtering](/docs/analytics/filtering) the panels

## Advanced Features

### Custom Events (Pro/Enterprise Plans)

If you have a Pro or Enterprise plan, you can track custom events like button clicks, form submissions, or purchases:

```javascript
window.va('event', {
  name: 'event_name',
  data: { /* custom data */ }
});
```

Learn more about [custom events](/docs/analytics/custom-events).

### Filtering Data

You can filter your analytics data by various dimensions. Learn more about [filtering](/docs/analytics/filtering).

## Framework-Specific Implementations

While this project uses the plain HTML implementation, Vercel Analytics supports many frameworks with more seamless integration:

- **Next.js**: Use `@vercel/analytics/next` with the `Analytics` component
- **React (CRA)**: Use `@vercel/analytics/react` with the `Analytics` component
- **Vue**: Use `@vercel/analytics/vue` with the `Analytics` component
- **Nuxt**: Use `@vercel/analytics/nuxt` with the `Analytics` component
- **SvelteKit**: Use `@vercel/analytics/sveltekit` with the `injectAnalytics` function
- **Remix**: Use `@vercel/analytics/remix` with the `Analytics` component
- **Astro**: Use `@vercel/analytics/astro` with the `Analytics` component

For more information, see the [@vercel/analytics package documentation](/docs/analytics/package).

## Notes

- **HTML Implementation**: This project uses the HTML implementation, so there is no need to install the `@vercel/analytics` package.
- **Route Support**: There is no automatic route support with the HTML implementation. Custom events must be tracked manually if needed.
- **Privacy**: All data collected by Vercel Web Analytics complies with privacy and data compliance standards. Learn more about [privacy and compliance](/docs/analytics/privacy-policy).

## Troubleshooting

### Script Not Loading

If you don't see requests to `/_vercel/insights/view` in your Network tab:

1. Verify the project is deployed to Vercel
2. Check that Web Analytics is enabled in the Vercel dashboard
3. Clear your browser cache and refresh
4. Check browser console for any errors

### No Data Showing

After deployment, it may take a few minutes for data to appear in the dashboard. Make sure:

1. Your site has actual visitors
2. At least a few days have passed for sufficient data collection
3. Web Analytics is enabled in your project settings

## Next Steps

Now that you have Vercel Web Analytics set up, you can:

- [Learn how to use the `@vercel/analytics` package](/docs/analytics/package)
- [Learn how to set custom events](/docs/analytics/custom-events)
- [Learn about filtering data](/docs/analytics/filtering)
- [Read about privacy and compliance](/docs/analytics/privacy-policy)
- [Explore pricing and limits](/docs/analytics/limits-and-pricing)
- [Visit troubleshooting guide](/docs/analytics/troubleshooting)

## Additional Resources

- [Vercel Web Analytics Documentation](https://vercel.com/docs/analytics)
- [Vercel Dashboard](https://vercel.com/dashboard)
- [@vercel/analytics npm package](https://www.npmjs.com/package/@vercel/analytics)
