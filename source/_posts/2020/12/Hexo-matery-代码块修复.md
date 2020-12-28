---
title: Hexo matery 代码块修复
date: 2020-12-28 11:29:23
tags:

---



###  代码块在 matery 主题下的基本展示:

```python
# python
a = 10;
```

```html
<!-- HTML -->
<div calss="wrap">
    我是 wrap 内容
</div>
```

```javascript
/* js */
const timer = null
```

```css
/* css */
.wrap{
    width: 10px;
    height: 10px;
}
```

```java
// java
class People{
    int age = 18;
}
```

```sql
-- mysql 无法高亮
-- 推荐: sql
select * from dept;
```

```bash
# bash
npm install 
```

###  配置步骤详解