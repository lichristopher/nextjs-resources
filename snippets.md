# Next js code snippers

```jsx
export function function AddPostForm() {
  const addPost = async (formData: FormData) => {
    "use server"
    await prisma.post.create({
      data: {
        title: formData.get("title") as string,
        body: formData.get("body") as string
      }
    });
  };
}
```
