## Why I Chose This Framework

I was stuck between React and Vue, but ultimately chose **Vue** because of its simplicity and ease of use. Its syntax is more similar to standard HTML, CSS, and JavaScript. While React is often preferred for large-scale products, Vue is a perfect fit for a smaller project, like this to-do app.

## Difficulties & Solutions

- I had an issue getting the project to run after initialization (`npm run dev`). I kept seeing the error **"vite: command not found"**. After re-reading the tutorial, I realized I had made a simple mistake — I forgot to run `npm install` first.

- I was having a hard time understanding the concept of passing data through props, so I visited the [documentation about props](https://vuejs.org/guide/components/props.html). After reading, I learned that props are a way for components to communicate. In this case, the parent component (**App.vue**) passes data down to the child component (**ToDoItem.vue**). The `ToDoItem` component receives the `label` and `done` information and displays it in its template. It’s sort of similar to passing arguments into a function.





