## Javascript - React.js useCallback hook

1. useState
- The count state tracks the current count and updates when the increment, decrement, or reset buttons are clicked.
- State is managed in the Parent component and displayed dynamically in the UI.

2. useCallback
- The increment, decrement, and reset functions are wrapped with useCallback.
- This ensures these functions are only recreated when their dependencies change.
- Since these functions are passed as props to the Child component, wrapping them in useCallback ensures their reference remains stable, preventing unnecessary re-renders of the Child.

3. React.memo
- The Child component is wrapped with React.memo, memoizing the component and preventing re-renders unless props change.
- For example, if the increment function's reference doesn't change (due to useCallback), the Child rendering the "Increment" button won't re-render.

How It Works
1. The Parent component initializes the count state and defines the increment, decrement, and reset functions.
2. These functions are passed to their respective Child components as props.
3. Each Child component displays a button with a specific label (e.g., "Increment") and executes the corresponding function when clicked.
4. Thanks to React.memo and useCallback, the Child components only re-render when their respective function references change.
5. When interacting with the buttons, the count is updated via the corresponding function (increment, decrement, or reset), and only the required components re-render.

Benefits
- Performance Optimization: Combining React.memo and useCallback avoids unnecessary re-renders of the Child components, useful in larger applications or complex components.
- Reusable Components: The Child component is generalized and can handle any action provided through props.
- Cleaner State Management: All state updates (count) are centralized in the Parent, keeping app logic clear and maintainable.
