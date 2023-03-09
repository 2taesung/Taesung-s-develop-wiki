# Vite

vite는 vue를 타겟으로 vue 개발자가 만들었다가 다른 라이브러리들에서도 지원하게 됨.

```bash
yarn create vite <프로젝트명> --template react-ts
```



vite.config.ts

```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
})
```



