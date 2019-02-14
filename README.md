# 使用 CSS3 属性做 fullpage

参考：

[HTML slides without frameworks, just CSS](https://www.chenhuijing.com/blog/html-slides-without-frameworks/)

[:target MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:target)

## 了解 :target 属性

`:target` CSS 伪类 代表一个唯一的页面元素(目标元素)，其id 与当前URL片段匹配；只有当前URL片段与页面元素的id匹配时，该元素的 `:target` 属性才会生效。

举例：

当页面上有这样一个元素时：

```html
<style>
    #show{
        display:none
    }
    #show:targer{
        display:block
    }
</style>
<div id="show">...</div>
```

只有当 URL 片段为 `/#show` 的时候，这个元素才是可见的。

---

## 设置页面元素属性

给需要轮播的元素设置 `:target`；当当前页面 URL 片段与元素的 id 匹配，该元素显示（`z-index:1`），其他元素隐藏（`z-index:0`）。

---

## 设置过渡动画

```css
main{
    position: relative;
}
section {
    color: #fff;
    height: 100vh;
    width: 100%;
    position: absolute;
    z-index: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transform: rotate(90deg);
    transform-origin: 0 0;
    transition: transform 1s, opacity 0.8s;
}
section:target {
    transform: rotate(0deg);
    z-index: 1;
}
section:target ~ section {
    opacity: 0;
    transform: rotate(-90deg);
}
```