---
title: JavaScript实战练习分析
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
tags: javascript
categories: javascript
abbrlink: 63989
date: 2020-11-26 21:56:24
top_img:
cover:轮播图:
---

###  全屏轮播图

###  轮播图:

```scss
@charset "utf-8";

#Slider {
  background-color: #333;
  color: #fff;
  line-height: 27px;
  position: relative;
  overflow: hidden;
  height: 80vh;
  width: 100vw;
  box-sizing: border-box;
}

h1 {
  font-weight: 700;
  font-size: 16px;
}

.sContent p {
  text-indent: 2rem;
}

.buttons {
  width: 100%;
}

.slider {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: opacity .4s ease-in-out;
}

.current {
  opacity: 1;
}



/* 左右按钮*/
#prev,
#next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 50px;
  height: 50px;
  background-color: rgb(221, 101, 101);
  border: 2px solid rgb(255, 255, 255);
  border-radius: 50%;
  padding: 2px;
  color: #fff;
  cursor: pointer;
}

#prev {
  left: 50px;
  top: 40vh;
}

#next {
  position: absolute;
  right: 50px;
  top: 40vh;
  transform: rotate(-180deg);
}

#next:hover,
#prev:hover {
  background-color: #ccc;
  color: #333;
}

#prev img,
#next img {
  position: absolute;
  left: 50%;
  top: 20px;
  transform: translate(-50%, 0);
  width: 16px;
}

/* background-image */

.slider:nth-child(1) {
  background: url('../access/img/Slider/01.jpg') no-repeat center center/cover;
}

.slider:nth-child(2) {
  background: url('../access/img/Slider/02.jpg') no-repeat center center/cover;
}

.slider:nth-child(3) {
  background: url('../access/img/Slider/03.jpg') no-repeat center center/cover;
}

.slider:nth-child(4) {
  background: url('../access/img/Slider/04.jpg') no-repeat center center/cover;
}

.slider:nth-child(5) {
  background: url('../access/img/Slider/01.jpg') no-repeat center center/cover;
}

/* centont*/
.slider .sContent {
  position: absolute;
  bottom: 50px;
  right: 600px;
  width: 600px;
  color: #333;
  background-color: rgba(255, 255, 255, .8);
  padding: 35px;
  height: 120px;
  opacity: 0;
  border-radius: 6px;
  overflow: hidden;
}

.slider.current .sContent {
  opacity: 1;
  transform: translateX(600px);
  transition: all 0.7s ease-in-out 0.3s;
}
```

```html
  <div id="Slider">
    <div class="slider current">
      <div class="sContent">
        <h1>第一页</h1>
        <p>
          1924年，安特生(瑞典地质学家兼考古学家)在甘肃临洮马家窑村发现一处远古文化遗址，
          定名为仰韶文化马家窑期，在当地收集了大量的代表华夏文化的彩陶器皿。个沉寂几千年的远古文化，
          第一次以马家窑期之名出现在世人面前！
        </p>
      </div>
    </div>
      
      <div class="slider">
      <div class="sContent">
        <h1>第二页</h1>
        <p>
          1924年，安特生(瑞典地质学家兼考古学家)在甘肃临洮马家窑村发现一处远古文化遗址，
          定名为仰韶文化马家窑期，在当地收集了大量的代表华夏文化的彩陶器皿。个沉寂几千年的远古文化，
          第一次以马家窑期之名出现在世人面前！
        </p>
      </div>
    </div>
      
      ···
      
      
  </div>
        
```



```javascript
console.log("正在加载 Slider.js·········");

const sliders = document.querySelectorAll(".slider");
const prev = document.querySelector("#prev");
const next = document.querySelector("#next");

const nextSlider = function () {
  // get current class
  const current = document.querySelector(".current");
  if (current.nextElementSibling) {
    // add current to next sibling
    current.nextElementSibling.classList.add("current");
  } else {
    // add current to start
    sliders[0].classList.add("current");
  }
  // clear current
  setTimeout(() => current.classList.remove("current"));
};

const prevSlider = function () {
  // get current class
  const current = document.querySelector(".current");
  if (current.previousElementSibling) {
    // add current to next sibling
    current.previousElementSibling.classList.add("current");
  } else {
    // add current to start
    sliders[sliders.length - 1].classList.add("current");
  }
  // clear current
  setTimeout(() => current.classList.remove("current"));
};

// click Event
next.addEventListener("click", function () {
  nextSlider();
});
prev.addEventListener("click", function () {
  prevSlider();
});

// 定时器
var timer = setInterval(function () {
  nextSlider();
}, 2000);

// 鼠标移入移除
var rmTimer = document.querySelector("#Slider ");
rmTimer.addEventListener("mouseenter", function () {
  // 鼠标移入清除 定时器
  clearInterval(timer);
  // 清除定时器变量
  timer = null;
  console.log("鼠标移入,清除定时器···");
});
rmTimer.addEventListener("mouseleave", function () {
  // 鼠标移出开启定时器
  timer = setInterval(function () {
    nextSlider();
  }, 2000);
  console.log("鼠标移入,开启定时器···");
});

```

> 轮播图总结:
>
> + 主要通过 css 中`background:url()` 存放图片路径
> + 添加鼠标移入移出事件
> + 添加`定时器应用`
>
> + 掌握 `position,transition`使用

> 内容来源依据: https://www.bilibili.com/video/BV1LV411z72g?p=22