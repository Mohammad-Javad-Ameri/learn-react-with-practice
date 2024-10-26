### React Query Teaching Document

---

#### 1. **What is React Query?**

React Query is a data-fetching and state management library designed to simplify data management in React applications, particularly when dealing with server state. It helps you handle caching, synchronization, background updates, and error handling with minimal effort.

- **Server State** refers to data that is external to your application and needs to be fetched from a server, like an API.
- It automates much of the complexity involved in making HTTP requests, managing cache, and updating components based on API responses.

---

#### 2. **Why Use React Query?**

- **Automated Caching:** React Query caches your data, reducing unnecessary network requests.
- **Synchronized State:** It keeps your server and client states in sync with minimal configuration.
- **Automatic Refetching:** It automatically refetches data in the background if it becomes stale.
- **Error Handling:** Simplifies error states by catching errors during fetching.
- **Focus on the UI:** With React Query, you can focus on the UI rather than state management boilerplate.

---

#### 3. **Difference Between Redux, Context API, and React Query**

- **Redux:** Redux is a state management tool for managing client-side state in a predictable way using actions and reducers. It's ideal for managing global, client-specific state.

- **Context API:** Similar to Redux but simpler, Context API is built into React. It's great for sharing state globally without props drilling. However, it doesn’t handle server-side state or side effects (e.g., API calls) well.

- **React Query:**
  - React Query excels at managing server-side state and caching responses from APIs.
  - It abstracts away many complexities of data fetching and reduces the need for manual error handling and retry logic.

---

#### 4. **How to Install React Query**

To install React Query, use npm or yarn:

```bash
npm install @tanstack/react-query
# or
yarn add @tanstack/react-query
```

You also need to install **React Query Devtools** (optional but helpful during development):

```bash
npm install @tanstack/react-query-devtools
# or
yarn add @tanstack/react-query-devtools
```

---

#### 5. **Features of React Query**

- **Queries:** Queries are used to fetch data from the server. With a unique query key, React Query caches the results.

  ```js
  import { useQuery } from "@tanstack/react-query";

  const { data, error, isLoading } = useQuery("uniqueKey", fetchDataFunction);
  ```

- **Mutations:** Mutations handle updating or deleting data on the server.

  ```js
  import { useMutation } from "@tanstack/react-query";

  const mutation = useMutation(newDataFunction);
  ```

- **Automatic Caching and Refetching:**
  React Query automatically caches your data and determines when it needs to be refetched based on the "staleTime" configuration.

  ```js
  const { data, error } = useQuery("posts", fetchPosts, {
    staleTime: 60000, // 1 minute
  });
  ```

- **Background Refetching:** React Query refetches data in the background when you re-focus the app or regain network connection.

- **Pagination and Infinite Scroll:** Handling paginated queries or infinite scroll becomes easy with the built-in features.
- **Devtools Integration:** Debugging is easier with the React Query Devtools, which provides a visual interface to inspect queries, mutations, and cache.
- **Optimistic Updates:** Before receiving the server's response, you can "optimistically" update the UI, offering a smoother UX.

- **Suspense Mode (Optional):** React Query works with React’s `Suspense` to manage loading states.

  ```js
  const { data } = useQuery(["user", userId], fetchUserData, {
    suspense: true,
  });
  ```

- **React Query Hydration (SSR):** React Query supports Server-Side Rendering (SSR) by allowing you to fetch and cache data on the server.

- **Retries:** Automatically retry failed queries with exponential backoff.

  ```js
  const { data, error } = useQuery("todos", fetchTodos, {
    retry: 3, // Retries 3 times before throwing an error
  });
  ```

- **Prefetching:** Prefetch data before it is required by the user to reduce perceived latency.

  ```js
  queryClient.prefetchQuery("key", fetchFunction);
  ```

---

#### 6. **Conclusion**

React Query is a robust and flexible tool for handling server-side data and managing the complexities of fetching, caching, and synchronizing your application’s state. It reduces the boilerplate code involved in managing asynchronous tasks and offers a more declarative and powerful approach compared to Redux or Context API for handling server data.
