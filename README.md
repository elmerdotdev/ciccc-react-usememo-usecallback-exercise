# React JS - memo and useCallback Exercise

**Goal:** To understand how memo and callback hooks can help optimize your React application by reducing re-renders.

## Instructions

1. Create a new React project by running `npm create vite@latest memo-callback`
2. Create a `count` state in your `App.tsx` component and a incrementing button that just increases the value by one.

### memo

3. Create a component called `Profile` and pass a `firstname` prop and a `lastname` prop to the component. You can use whatever values. Display the props inside your `Profile` component.
4. Add a `console.log("Rendered Profile Component")` inside your `Profile` component.
5. Now, try clicking on the increment button. You will see on your Dev Tools it will keep logging *"Rendered Profile Component"*. This is because in React, when a state changes in a parent component, all child components that receive a prop/s from the parent will re-render.
6. Go back to your `Profile` component and wrap the component with a `memo`. After that, refresh the page and click on the increment button again. You will notice that the *"Rendered Profile Component"* message will no longer log multiple times. This is because you memoized the component and unless the prop values change, React will not re-render the component.

### useCallback

7. Create a `ProductList.tsx` component. Add a `products` state and create an async function called `fetchProducts()` that fetches data from `https://dummyjson.com/products` and updates the state with the results.
8. Create a component called `GetProductsButton.tsx` and inside it, create a button with the label "Fetch Products". Still inside the button component, add a `console.log("Rendered Button Component")`.
9. Pass the `fetchProducts` function as a prop to the button component. On the button component, attach the function prop to the `onClick` attribute.
10. Click on the **Fetch Products** button and notice how every time you click, it lgs *"Rendered Button Component"* to the Dev Tools. This is because after you fetch the data, you are updating the products state, which in turn re-renders the button since it is receiving a function prop from the parent component.
11. To avoid re-rendering the button component, wrap your function in a `useCallback` with no dependencies and wrap your button component in a `memo`. The `useCallback` will memoize the `fetchProducts()` function so that it doesn't get recreated when the state is updated. Also, because of the `memo` on the button component, the button component will not re-render because the function prop is basically still the same as the function's identity is maintained and not re-created.
12. Commit and push your changes.
