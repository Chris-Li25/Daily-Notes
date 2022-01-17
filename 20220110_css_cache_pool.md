# CSS 动画

### **DOM_POOL** 

#### 思路：缓存池

如果出现大量生成dom的场景，很多情况我们想要复用它，而不是每次都创建，这种场景情况下就有必要用到缓存池，[canvas](https://so.csdn.net/so/search?q=canvas)绘制也同样，这只是复用的一种思路，不局限于dom



#### 字体隧道效果

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Title</title>
    <style>
      html,
      body {
        margin: 0;
        padding: 0;
      }

      .container {
        background: #222;
        width: 100vw;
        height: 100vh;
        overflow: hidden;
      }

      #animateBox {
        width: 100%;
        height: 100%;
        perspective: 100px;
        transform-style: preserve-3d;
      }

      .text-item {
        position: absolute;
        font-size: 20px;
        transform-style: preserve-3d;
        color: #fff;
        text-shadow: 0px 0px 10px #00ffff;
        top: 50%;
        left: 50%;
        transition: transform 1s ease-out, opacity 500ms;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <input type="range" name="" id="" />
      <!-- <div id='animateBox'>

  </div> -->
    </div>
    <script>
      const $animateBox = document.getElementById("animateBox");
      const DOM_POOL = []; // dom 池
      const TEXT_ADD_NUM = 5;

      init();

      function init() {
        const $frag = document.createDocumentFragment();
        for (let i = 0; i < 200; i++) {
          const $item = document.createElement("div");
          $item.style.display = "none";
          $frag.appendChild($item);
          DOM_POOL.push($item);
        }
        $animateBox.appendChild($frag);
      }

      function handleTextEnd(textObj) {
        const $dom = textObj.dom;
        if ($dom) {
          $dom.style.display = "none";
          $dom.classList.remove("text-item");
          $dom.style.opacity = 0;
          $dom.style.transform = "";
          $dom.innerText = "";
          DOM_POOL.push($dom);
        }
      }

      function handleTextStart(textObj) {
        const $dom = textObj.dom;
        if ($dom) {
          const { x, y, z } = textObj.transformStart;
          const transformEnd = `translateX(${x}px) translateY(${y}px) translateZ(120px)`;
          $dom.style.opacity = 1;
          $dom.style.transform = transformEnd;
        }
      }

      function genTextArr() {
        const textArr = [];
        for (let i = 0; i < TEXT_ADD_NUM; i++) {
          if (!DOM_POOL.length) {
            console.log("dom pool empty!");
            break;
          }
          const $textItem = DOM_POOL.shift();
          const text = "123";

          const x = Math.floor(Math.random() * 501 - 250);
          const y = Math.floor(Math.random() * 501 - 250);
          const z = Math.floor(Math.random() * 301 - 290);

          const transformStart = `translateX(${x}px) translateY(${y}px) translateZ(${z}px)`;

          $textItem.classList.add("text-item");
          $textItem.style.display = "block";
          $textItem.style.transform = transformStart;
          $textItem.style.opacity = 0;
          $textItem.innerText = text;

          const textObj = {
            text,
            transformStart: { x, y, z },
            dom: $textItem,
          };

          textArr.push(textObj);
        }

        // dom已加载时开始动画
        setTimeout(() => {
          textArr.forEach((textObj) => {
            handleTextStart(textObj);
          });
        }, 100);

        // 动画结束时移除
        setTimeout(() => {
          textArr.forEach((textObj) => {
            handleTextEnd(textObj);
          });
        }, 1100);
      }

      setInterval(() => {
        genTextArr();
      }, 100);
    </script>
  </body>
</html>
```

