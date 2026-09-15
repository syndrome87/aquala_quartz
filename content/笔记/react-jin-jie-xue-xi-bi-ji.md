---
title: React进阶学习笔记
date: 2026-04-07T13:47:06
updated: 2026-04-07T18:47:10
tags:
  - 笔记
draft: true
---
# React 进阶学习笔记

本文参考[HDAlex_John](https://space.bilibili.com/337242418) React 进阶教程,学习并记录

## React route

简单路由对象的基础组成

```text
createBrowserRouter([
  {
    path: "/",
    Component: App,
  },
]);
```

### Nested Routes

嵌套路由,在路由对象内用 children 嵌套子对象

```text
createBrowserRouter([
  {
    path: "/dashboard",
    Component: Dashboard,
    children: [
      { index: true, Component: Home },
      { path: "settings", Component: Settings },
    ],
  },
]);
```

### NavLink

类似 a 标签,包装 `<Link>` 并添加用于样式化激活和待定状态的额外属性。

```text
<NavLink to="/message">Messages</NavLink>

// Using render props
<NavLink
  to="/messages"
  className={({ isActive, isPending }) =>
    isPending ? "pending" : isActive ? "active" : ""
  }
>
  Messages
</NavLink>
```

### useNavigate

声明 navigate 后以较为灵活的函数调用实现掉转

```text
import { useNavigate } from "react-router";

function SomeComponent() {
  let navigate = useNavigate();
  return (
    <button onClick={() => navigate(-1)}>
      Go Back
    </button>
  );
}
```

### useLocation 的返回值

```text
interface Location<State = any> {
    hash: string;
    key: string;
    pathname: string;
    search: string;
    state: State;
    unstable_mask: undefined | Path;
}
```
