# Reading 33: Next.js 

> WHAT IS NEXT.JS?
- Next.js is a JavaScript framework that enables you to build superfast and extremely user-friendly static websites, as well as web applications using React.
- advantages like:
  - Rich User Experience (easier and faster)
  - Great performance (also easier and faster)
  - Rapid feature development

    

> Take into consideration: 
- Code has to be bundled using a bundler like webpack and transformed using a compiler like Babel.
- You need to do production optimizations such as code splitting.
- You might want to statically pre-render some pages for performance and SEO. You might also want to use server-side rendering or client-side rendering.
- You might have to write some server-side code to connect your React app to your data store.



> built-in features in next.js 
- An intuitive page-based routing system (with support for dynamic routes)
- Pre-rendering, both static generation (SSG) and server-side rendering (SSR) are supported on a per-page basis
- Automatic code splitting for faster page loads
- Client-side routing with optimized prefetching
- Built-in CSS and Sass support, and support for any CSS-in-JS library
- Development environment with Fast Refresh support
- API routes to build API endpoints with Serverless Functions
- Fully extendable
 


> Assets & Metadata & CSS styling 
- Next.js can serve static assets, like images, under the top-level public directory. Files inside public can be referenced from the root of the application similar to pages.
- `title` is part of the `head` HTML tag, so let's dive into how we can modify the `head` tag in a Next.js page 
  - this will help you in the CEO for search engine performance
- CSS modules allow you to locally scope CSS at the component-level by automatically creating unique class names.



> React Context 
- What is React context? 
  - React context allows us to pass down and use (consume) data in whatever component we need in our React app without using props.
- When should you use React context? 
  - when you are passing data that can be used in any component in your application.
  - types of data included 
    - Theme data (like dark or light mode)
    - User data (the currently authenticated user)
    - Location-specific data (like user language or locale)



> Props drilling
- is a term to describe when you pass props down multiple levels to a nested component, through components that don't need it.



> How do I use React context? 
- steps to using React context: 
  - Create context using the createContext method.
  - Take your created context and wrap the context provider around your component tree.
  - Put any value you like on your context provider using the value prop.
  - Read that value within any component by using the context consumer.



> What is the useContext hook ? 
- we can pass the entire context object to React.useContext() to consume context at the top of our component.



> React Context VS Redux 
- Redux is a way of more easily passing around data. This is because Redux comes with React context itself. 
- Instead of using render props we can use `React.useContext()`


> WHAT CAN YOU BUILD WITH NEXT.JS?
- With Next.js you can build a number of digital products and interfaces such as:
  - MVP (Minimum Viable Product)
  - Jamstack websites
  - Web Portals
  - Single web pages
  - Static websites
  - SaaS products
  - eCommerce and retail websites
  - Dashboards
  - Complex and demanding web applications
  - Interactive user interfaces


> Resources 
- https://pagepro.co/blog/what-is-nextjs/
- https://nextjs.org/learn/basics/create-nextjs-app
- https://www.freecodecamp.org/news/react-context-for-beginners/

