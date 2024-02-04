# Set-up prisma with nextjs

```bash
npm install prisma --save-dev
npm install @prisma/client@latest
npx prisma init
npx prisma init --datasource-provider sqlite
```

```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "sqlite"
  url      = "file:./db.sqlite"
}

model Todo {
  id String @id @default(uuid())
  content String
  createdAt DateTime @default(now())
  completed Boolean @default(false)
}
model User {
  id   Int    @id
  name String
}

```
