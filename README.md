# Digital Storefront

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A modern SaaS template for building digital marketplaces. It offers tenant specific storefronts, flexible checkout, and an admin experience powered by Payload CMS and Next.js.

## Table of Contents

- [Features](#features)
- [Demo](#demo)
- [Setup](#setup)
  - [Simple Mode Setup](#simple-mode-setup)
  - [Advanced Mode Setup](#advanced-mode-setup)
- [Usage](#usage)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [FAQ](#faq)
- [License](#license)
- [Acknowledgements](#acknowledgements)
- [Contact](#contact)

## Features

- Serve many merchants from a single installation using tenant aware routing
- Issue vendor subdomains with wildcard DNS support
- Collect payments through Stripe Connect and apply automatic platform fees
- Let customers leave ratings and reviews on purchased products
- Manage inventory, categories, and tags from a Payload CMS dashboard
- Provide each buyer with a personal download library
- Offer search and advanced filtering across categories
- Upload images using Vercel Blob storage

## Demo

_No live demo is available._

## Setup

Below are two setup flows depending on how much customization you need. Both require Node.js 18+ or Bun 1+.

### Simple Mode Setup

1. **Clone the Repository**
   ```bash
   git clone <repo-url>
   cd digital-storefronts
   ```
2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Configure Environment**

   ```bash
   cp .env.example .env.local
   ```

   Required variables:
   * `APP_MODE=simple`
   * `DATABASE_URI=`
   * `PAYLOAD_SECRET=`
   * `STRIPE_SECRET_KEY=`
   * `STRIPE_WEBHOOK_SECRET=`
  * `BLOB_READ_WRITE_TOKEN=` - must follow the format `vercel_blob_rw_<store_id>_<random_string>`
   * `NEXT_PUBLIC_APP_URL=http://localhost:3000`
   * `NEXT_PUBLIC_ROOT_DOMAIN=localhost:3000`
   * `NEXT_PUBLIC_ENABLE_SUBDOMAIN_ROUTING=false`

4. **Run the App**

   ```bash
   npm run dev
   ```

### Advanced Mode Setup

For production you can enable wildcard subdomain routing and customize the platform fee percentage. Ensure your DNS provider supports `*.yourdomain.com` records.

Set the following variables in `.env.local`:

```env
NEXT_PUBLIC_ROOT_DOMAIN=yourdomain.com
NEXT_PUBLIC_ENABLE_SUBDOMAIN_ROUTING=true
PLATFORM_FEE_PERCENTAGE=10
```

Run database migrations and seeds:

```bash
npm run db:fresh
npm run db:seed
```

Then start the app with:

```bash
npm run build
npm start
```

## Usage

1. Register as a new merchant to create your own tenant.
2. Upload products and images from the admin dashboard.
3. Share your store via `https://yourtenant.yourdomain.com` once subdomains are enabled.
4. Customers browse products, add them to the cart and purchase through Stripe.
5. Purchased items appear in the customer's library for future downloads and reviews.

## Deployment

Deploy easily to Vercel. After connecting the repository, set the environment variables from `.env.local` in the Vercel dashboard.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/import/project)

## Contributing

Contributions are welcome! Please open an issue or submit a pull request. See `CONTRIBUTING.md` if available.

## FAQ

**How do platform fees work?** The variable `PLATFORM_FEE_PERCENTAGE` sets the percentage taken from each transaction and is applied automatically by Stripe.

**Can I disable subdomains?** Yes. Keep `NEXT_PUBLIC_ENABLE_SUBDOMAIN_ROUTING=false` and access stores via `/tenants/[slug]` routes.

**Which database does this project use?** MongoDB via Payload CMS. Provide the connection string in `DATABASE_URI`.

## License

This project is licensed under the MIT license.

## Acknowledgements

Built with [Next.js](https://nextjs.org/), [Payload CMS](https://payloadcms.com/), [Stripe](https://stripe.com/), and [shadcn/ui](https://ui.shadcn.com/).

## Contact

For support or questions, please open an issue in this repository.

