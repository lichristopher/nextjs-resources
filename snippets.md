# Next js code snippets

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

## programatically changing search parameters

```jsx
"use client"
import {useRouter, useSearchParams} from "next/navigation";

export function Form() {
  const searchPrams = useSearchParams();
  const router = useRouter();

  return (
    <form>
      <input value={searchParams.get("q") || ""} onChange={(e) => {
        const params = new URLSearchParams(searchParams);
        params.set("q", e.target.value);
        router.push(`?${params.toString()}`);
      }}>

    </form>
  )
}
```
