# Read 32 : Intro to Next.js & Tailwind CSS


## What is Next Js:[source](https://www.youtube.com/watch?v=__mSgDEOyv8)
**Created by Vercel, Next.js is an open-source and JavaScript framework, allowing you to develop fast and user-friendly web applications and static websites using React. Actually, it is based on Node.js and Babel, and it integrates with React to develop Single Page Applications. This makes server-side convenient and easier.**

**Next JS is a JavaScript framework that allows developers to create user-friendly and blazing fast static websites and static web applications with React. Next JS is an open-source, lightweight web development framework for React applications. It allows developers to build server-side rendering.**

**Next.js is based on React babel and webpack, which provides an out-of-the-box solution for server-side rendering (SSR) of React components.** **Next.js is an open-source JavaScript framework that allows developers to create dynamic and static web applications and websites.**


**Furthermore, Next.js provides many features, such as static export, preview mode, pre-rendering, faster compilation, and automatic building size optimization. As per my view, the existing Next.js version is something React has been missing for quite a long time.**

**Next JS includes all the features you will need to create an application. Furthermore, the documentation is excellent, and it is becoming increasingly popular among developers for front-end development.**

**Next.js is a popular framework, but that doesn’t mean you should use it all of the time.**

### What is Next.js Used For?
Next.js is used to develop:

* ECommerce Websites
* Marketing Websites
* Landing Pages

<br>
<br>

## Next.js 13 :[source](https://nextjs.org/blog/next-13)

 `npm i next@latest react@latest react-dom@latest eslint-config-next@latest`
   
## New app Directory (Beta)

**The app directory is currently in beta and we do not recommend using it in production yet. You can use Next.js 13 with the pages directory with stable features like the improved next/image and next/link components, and opt into the app directory at your own pace. The pages directory will continue to be supported for the foreseeable future.**


### The app directory includes support for:

1. **Layouts**: Easily share UI between routes while preserving state and avoiding expensive re-renders.
2. **Server Components**: Making server-first the default for the most dynamic applications.
3. **Streaming**: Display instant loading states and stream in units of UI as they are rendered.
Support for Data Fetching: async Server Components and extended fetch API enables component-level fetching.

  ![app](https://nextjs.org/_next/image?url=%2Fstatic%2Fblog%2Flayouts-rfc%2Fapp-folder.png&w=3840&q=75)



<br>


## What is tailwindcss :[source](https://tailwindcss.com/docs/utility-first)

### Why use tailwindcss

Traditionally, whenever you need to style something on the web, you write CSS. With Tailwind, you style elements by applying pre-existing classes directly in your HTML.

Example:

- Tailwind’s flexbox and padding utilities (flex, shrink-0, and p-6) to control the overall card layout
- The max-width and margin utilities (max-w-sm and mx-auto) to constrain the card width and center it horizontally
- The background color, border radius, and box-shadow utilities (bg-white, rounded-xl, and shadow-lg) to style the card’s appearance
- The width and height utilities (w-12 and h-12) to size the logo image
- The space-between utilities (space-x-4) to handle the spacing between the logo and the text
- The font size, text color, and font-weight utilities (text-xl, text-black, font-medium, etc.) to style the card text
- This approach allows us to implement a completely custom component design without writing a single line of custom CSS.

Why not just use inline styles?
A common reaction to this approach is wondering, “isn’t this just inline styles?” and in some ways it is — you’re applying styles directly to elements instead of assigning them a class name and then styling that class.

But using utility classes has a few important advantages over inline styles:

- Designing with constraints. Using inline styles, every value is a magic number. With utilities, you’re choosing styles from a predefined design system, which makes it much easier to build visually consistent UIs.
- Responsive design. You can’t use media queries in inline styles, but you can use Tailwind’s responsive utilities to build fully responsive interfaces easily.
- Hover, focus, and other states. Inline styles can’t target states like hover or focus, but Tailwind’s state variants make it easy to style those states with utility classes.