---
title: "Nativewind ClassName  error fixed  in VS Code"
datePublished: Fri Sep 29 2023 13:33:37 GMT+0000 (Coordinated Universal Time)
cuid: cln4nabpr000n09mkd6gs7ofl
slug: nativewind-classname-error-fixed-in-vs-code
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695994341220/c5282522-0c22-4427-a03e-d4a929624fab.jpeg
tags: react-native, typescript, expo, vscode-cjevho8kk00bo1ss2lmqqjr51, nativewind

---

Suddenly in the react native project ClassName gets an error in VS Code sonarlint.

After completing Nativewind guide for [typescript](https://www.nativewind.dev/getting-started/typescript), still ClassName error is still not rectified.

## Simple solution :

```bash
mv app.d.ts app.d.tsx
```

Rename app.d.ts -&gt; app.d.tsx

I posted this solution because this wasn't available online.

Happy Coding!