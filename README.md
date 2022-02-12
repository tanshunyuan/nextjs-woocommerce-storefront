# Next.js WooCommerce Storefront Theme 
Using Next.js, TypeScript and Styled-components.



[![Quality gate](https://sonarcloud.io/api/project_badges/quality_gate?project=Onixaz_nextjs-woocommerce-storefront)](https://sonarcloud.io/dashboard?id=Onixaz_nextjs-woocommerce-storefront)

#### *WIP*

![demo](https://github.com/Onixaz/nextjs-woocommerce-storefront/blob/main/public/demo.gif)




## The Goal

The idea behind this repo was to showcase the power of [Next.js](https://nextjs.org/) by building a frontend for [WooCommerce](https://woocommerce.com/) using nothing but [Woo's REST API](https://woocommerce.github.io/woocommerce-rest-api-docs/) only. This means truly headless and secure WooCommerce without any redirects to checkouts etc. In a true [Jamstack](https://jamstack.org/) fashion.



## Features
* WooCommerce Storefront theme inspired responsive design.
* Static page generation using getStaticProps and getStaticPaths for SEO and performance.
* Client side fetching of dynamic data like prices / account details using [SWR](https://swr.vercel.app/).
* WooCommerce REST API abstraction using [Next's API routes](https://nextjs.org/docs/api-routes/introduction).
* JWT based authentication for data fetching / endpoint protection.
* Cart system using [CoCart](https://wordpress.org/plugins/cart-rest-api-for-woocommerce) plugin.
* Customer registration and authentication using [NextAuth.js](https://next-auth.js.org/). 
* Checkout system using [Stripe](https://stripe.com/) as a payment method example.


## How to use

Install required plugins on your Wordpress:
* [WooCommerce](https://wordpress.org/plugins/woocommerce/) (obviously)
* [JWT Authentication for WP REST API](https://wordpress.org/plugins/jwt-authentication-for-wp-rest-api/)
* [Cocart Lite](https://wordpress.org/plugins/cart-rest-api-for-woocommerce)
* [Password Reset with Code for WordPress REST API](https://wordpress.org/plugins/bdvs-password-reset/) (to be implemented)

Change Permalinks to **Post Name (Settings -> Permalinks).** Also make sure your **JWT Authentication for WP REST API** plugin is configured correctly. 


You'll need to import some products. For testing you can use sample data from Woo https://docs.woocommerce.com/document/importing-woocommerce-sample-data/ just like I did.

To test in-app payments you'll need to register a Stripe account for the publishable key and secret. (https://stripe.com/docs/keys) 

**Next clone this repo, cd into it and npm install.**

Create **.env.local** file in the root of the project. 

It should consist of 


``` 
NEXT_PUBLIC_WP_API_URL=https://example.com
NEXTAUTH_URL=http://localhost:3000 // change to actual production url
WP_JWT_AUTH_SECRET_KEY=your-random-secret
NEXTAUTH_SECRET_KEY=your-another-random-secret
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=your-stripe-publishable-key
STRIPE_SECRET_KEY=your-stripe-secret-key

```

Notice that **NEXT_PUBLIC_WP_API_URL** and **NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY** should have **NEXT_PUBLIC** prefix, since these variables need to be exposed to the browser. 

**WP_JWT_AUTH_SECRET_KEY** which will be used to sign jwt should match the one you define in **wp-config.php** when configuring "JWT Authentication for WP REST API" plugin.

Finally **npm run dev.**

Note: In case you're not getting the **x-cocart-api key** when calling CoCart endpoint from a response header, allow cross origin headers using [https://github.com/co-cart/co-cart-tweaks](https://github.com/co-cart/co-cart-tweaks)




## Deployment

You can easily deploy on [Netlify](https://www.netlify.com) using [Next.js Build Plugin](https://github.com/netlify/netlify-plugin-nextjs). 

Just make sure you set your env variables. For more details refer to [https://www.netlify.com/blog/2020/12/10/environment-variables-in-next.js-and-netlify/](https://www.netlify.com/blog/2020/12/10/environment-variables-in-next.js-and-netlify/).

##  Todo

* ~~User registration and login functionality.~~
* ~~Dynamic prices using SWR (client side data fetching).~~
* ~~Shipping options.~~
* ~~Products pagination.~~
* ~~User specific cart.~~
* User dashboard (orders, addresses, password reset).
* Pages for categories.
* Blog page.
* Image optimization.
* Filters.
* Coupons system.
* Product reviews.
* Wishlist.
* Search.
* More payment methods.
* Tests


#### Contributions are welcome

MIT License
