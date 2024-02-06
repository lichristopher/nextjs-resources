# Set-up prisma with nextjs

```bash
DATABASE_URL="file:./db.sqlite"
DATABASE_URL="file:./dev.db"
npm install prisma --save-dev
npm install @prisma/client@latest
npx prisma init
npx prisma init --datasource-provider sqlite
npx prisma migrate dev --name init
```

```text
import { PrismaClient } from '@prisma/client'

let prisma: PrismaClient

if (process.env.NODE_ENV === 'production') {
  prisma = new PrismaClient()
} else {
  if (!global.prisma) {
    global.prisma = new PrismaClient()
  }
  prisma = global.prisma
}

export default prisma
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
