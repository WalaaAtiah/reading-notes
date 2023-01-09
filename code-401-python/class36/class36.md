# Read 36 : Data Fetching

## What is SWR :[source](https://blog.openreplay.com/beginner-s-guide-to-swr-data-fetching-in-react)

**SWR stands for `stale-while-revalidate`, a HTTP cache invalidation strategy popularized by HTTP RFC 5861. It basically means that it performs data fetching in 3 steps:**

1. Returns cached data first (stale)
2. Sends the fetch request (revalidate)
3. Returns the up-to-date data

**SWR is created by Vercel and one of its advantages is that it is a fast and lightweight package.**

### **Why use SWR?**
1. **Built-in Cache + Real-Time Experience**
2. **Auto Revalidation**
3. **Pagination**
4. **Local mutation**
5. **Dependent fetching**
6. **Smart error retry**
7. **Supports fetching from both REST and GraphQL APIs**
8. **Typescript and React Native ready**


## Example Usage of SWR in React
1. Install package `npm install swr`
2. Import useSWR `import useSWR from 'swr'`
3. Write a fetcher function

```
import axios from 'axios'

const fetcher = url => axios.get(url).then(res => res.data)
```
4.  Fetch Data

```
import useSWR from 'swr'

function App () {
  const fetcher = (...args) => fetch(...args).then(res => res.json())

   // Add these lines
  const { data, error } = useSWR('https://jsonplaceholder.typicode.com/todos/1', fetcher)

  if (error) return <div>Failed to load</div>
  if (!data) return <div>Loading...</div>

  // render data below
}
```

5. Display Data

```
{
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": false
}
```

## SWR :[source](https://swr.vercel.app/)

### **Features**

* Fast, lightweight and reusable data fetching
* Built-in cache and request deduplication
* Real-time experience
* Transport and protocol agnostic
* SSR / ISR / SSG support
* TypeScript ready
* React Native


* Fast page navigation
* Polling on interval
* Data dependency
* Revalidation on focus
* Revalidation on network recovery
* Local mutation (Optimistic UI)
* Smart error retry
* Pagination and scroll position recovery
* React Suspense