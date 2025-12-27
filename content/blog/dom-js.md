---
title: "Thao Tác Với DOM Trong JavaScript: Làm Chủ Giao Diện Web"
date: 2025-12-23
tags: ["javascript", "dom", "document object model", "frontend", "web development", "event listener", "interactive"]
description: "Hướng dẫn chi tiết thao tác DOM trong JavaScript: chọn phần tử, thay đổi nội dung, style, thêm sự kiện. Kèm ví dụ thực tế và chạy code trực tiếp trên trình duyệt để thử nghiệm ngay."

keywords:
  - thao tác dom javascript
  - dom javascript
  - học dom js
  - javascript dom tutorial tiếng việt
  - queryselector addeventlistener
  - chạy dom javascript online
  - javascript frontend cơ bản
---

<style>
.post-content {
  max-width: 1500px !important;
}
</style>

<h1 style="text-align:center;">Thao Tác Với DOM Trong JavaScript: Làm Chủ Giao Diện Web</h1>

<img src="https://upload.wikimedia.org/wikipedia/commons/6/6a/JavaScript-logo.png"
     alt="JavaScript Logo"
     style="width:160px; display:block; margin:30px auto;">

<p>
<b>DOM (Document Object Model)</b> là cây cấu trúc đại diện cho toàn bộ trang HTML. JavaScript có thể đọc, thay đổi, thêm/xóa phần tử trên DOM → biến trang web tĩnh thành <b>động và tương tác</b>.
</p>

<p>
DOM là nền tảng của mọi thao tác frontend: thay đổi nội dung, style, xử lý click, form validation… và cũng là cơ sở cho các framework hiện đại như React, Vue.
</p>

<hr>

<h2 id="dom-la-gi">1. DOM là gì?</h2>

<img src="https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction/dom-tree.png"
     alt="Cấu trúc cây DOM"
     style="width:100%; max-width:800px; display:block; margin:30px auto; border-radius:8px;">

<p>DOM là biểu diễn dạng cây của tài liệu HTML. Mỗi thẻ HTML là một node, JavaScript có thể truy cập và thay đổi bất kỳ node nào.</p>

<hr>

<h2 id="chon-phan-tu">2. Chọn phần tử DOM</h2>

<pre><code class="language-javascript">
// Các cách phổ biến
document.getElementById("id");
document.querySelector(".class");           // Lấy phần tử đầu tiên
document.querySelectorAll("p");             // Lấy tất cả (NodeList)
document.getElementsByClassName("class");   // HTMLCollection
document.getElementsByTagName("div");
</code></pre>

<hr>

<h2 id="thay-doi">3. Thay đổi nội dung và style</h2>

<pre><code class="language-javascript">
let element = document.querySelector("#demo");

// Thay đổi nội dung
element.innerHTML = "Nội dung mới từ JS!";
element.textContent = "Chỉ text, an toàn hơn";

// Thay đổi thuộc tính
element.setAttribute("title", "Tooltip mới");

// Thay đổi style
element.style.color = "red";
element.style.backgroundColor = "#f0f8ff";
element.classList.add("highlight");
</code></pre>

<hr>

<h2 id="su-kien">4. Xử lý sự kiện (Event Listener)</h2>

<pre><code class="language-javascript">
document.querySelector("button").addEventListener("click", () => {
    alert("Bạn vừa click nút!");
});

// Nhiều loại sự kiện
element.addEventListener("mouseover", () => { /* ... */ });
element.addEventListener("keydown", (e) => { console.log(e.key); });
</code></pre>

<hr>

<h2 id="tao-xoa">5. Tạo và xóa phần tử</h2>

<pre><code class="language-javascript">
// Tạo phần tử mới
let newDiv = document.createElement("div");
newDiv.innerHTML = "Phần tử mới được tạo bằng JS";
document.body.appendChild(newDiv);

// Xóa phần tử
element.remove();  // Hoặc parent.removeChild(element)
</code></pre>

<hr>

<h2 id="ung-dung">6. Ứng dụng thực tế</h2>

<ul>
  <li>Validate form trước submit</li>
  <li>Tạo modal, dropdown menu</li>
  <li>Slider ảnh, carousel</li>
  <li>Todo list tương tác</li>
  <li>Load dữ liệu động (AJAX/Fetch)</li>
</ul>

<hr>

<h2 id="thuc-hanh">7. Thực hành chạy code trực tiếp</h2>

<p>
Bạn có thể <b>chỉnh sửa và chạy ví dụ DOM thực tế</b> ngay trên trình duyệt. Code sẽ tạo giao diện mini và cho phép tương tác.
</p>

<p><strong>Hướng dẫn:</strong><br>
- Chỉnh sửa code trong editor.<br>
- Nhấn <b>▶ Run JavaScript</b> → kết quả hiển thị ngay bên dưới (giao diện + console).<br>
- Thử click các nút được tạo ra để thấy hiệu ứng.<br>
- Nhấn <b>📋 Copy Code</b> để sao chép.
</p>

<div id="editor" style="height:520px; border:1px solid #ccc; border-radius:8px;"></div>

<div style="margin-top:14px; text-align: left;">
  <button onclick="copyCode()" id="copyBtn" style="
    padding:12px 20px;
    background:#333;
    color:white;
    border:none;
    cursor:pointer;
    font-size:16px;
    font-weight:bold;
    border-radius:0 6px 6px 0;
    margin-left:0;">
    Copy Code
  </button>

  <button onclick="runCode()" style="
    padding:12px 26px;
    background:#f7df1e;
    color:#000;
    border:none;
    cursor:pointer;
    font-size:16px;
    font-weight:bold;
    border-radius:6px 0 0 6px;
    margin-right:0;">
    ▶ Run JavaScript
  </button>
</div>

<span id="copyFeedback" style="margin-left:12px; font-size:14px; color:#28a745; font-weight:bold; display:none;">Đã sao chép!</span>

<h3 id="ket-qua">Kết quả</h3>

<iframe id="output" style="width:100%; height:600px; border:1px solid #ccc; border-radius:8px;"></iframe>

<script src="https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.51.0/min/vs/loader.min.js"></script>

<script>
require.config({
  paths: { vs: "https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.51.0/min/vs" }
});

let editor;

require(["vs/editor/editor.main"], function () {
  editor = monaco.editor.create(document.getElementById("editor"), {
    value: `// MINI APP: Todo List đơn giản với DOM Manipulation

// Tạo giao diện cơ bản
document.body.innerHTML = \`
  <div style="max-width:600px; margin:40px auto; font-family:Arial, sans-serif;">
    <h2 style="text-align:center; color:#333;">My Todo List</h2>
    
    <div style="margin-bottom:20px;">
      <input type="text" id="todoInput" placeholder="Nhập việc cần làm..." 
             style="padding:10px; width:70%; font-size:16px;">
      <button id="addBtn" style="padding:10px 20px; font-size:16px; background:#f7df1e; border:none;">
        Thêm
      </button>
    </div>
    
    <ul id="todoList" style="list-style:none; padding:0;"></ul>
    
    <p id="status" style="text-align:center; color:#666; margin-top:30px;"></p>
  </div>
\`;

// DOM Elements
const input = document.getElementById("todoInput");
const addBtn = document.getElementById("addBtn");
const list = document.getElementById("todoList");
const status = document.getElementById("status");

let todos = [];

// Hàm cập nhật giao diện
function renderTodos() {
    list.innerHTML = "";
    todos.forEach((todo, index) => {
        const li = document.createElement("li");
        li.innerHTML = \`
          <span>\${todo}</span>
          <button style="float:right; background:red; color:white; border:none; padding:5px 10px;">
            Xóa
          </button>
        \`;
        li.style = "padding:10px; background:#f8f9fa; margin:5px 0; border-radius:5px;";
        
        // Xóa todo
        li.querySelector("button").addEventListener("click", () => {
            todos.splice(index, 1);
            renderTodos();
            updateStatus();
        });
        
        list.appendChild(li);
    });
    updateStatus();
}

function updateStatus() {
    status.textContent = todos.length === 0 
        ? "Chưa có việc nào! Hãy thêm todo"
        : \`Bạn có \${todos.length} việc cần làm!\`;
}

// Thêm todo
addBtn.addEventListener("click", () => {
    const text = input.value.trim();
    if (text) {
        todos.push(text);
        input.value = "";
        renderTodos();
    }
});

// Enter để thêm
input.addEventListener("keypress", (e) => {
    if (e.key === "Enter") addBtn.click();
});

// Khởi tạo
renderTodos();

console.log("Mini Todo App đã sẵn sàng! Thử thêm vài việc nhé 🚀");
`,
    language: "javascript",
    theme: "vs-dark",
    automaticLayout: true,
    fontSize: 15,
    minimap: { enabled: false },
    wordWrap: "on"
  });
});

function runCode() {
  const code = editor.getValue();
  const encoded = encodeURIComponent(code);
  document.getElementById("output").src = 
    "https://onecompiler.com/embed/javascript?code=" + encoded;
}

function copyCode() {
  const code = editor.getValue();
  navigator.clipboard.writeText(code).then(() => {
    const feedback = document.getElementById("copyFeedback");
    feedback.style.display = "inline";
    feedback.textContent = "Đã sao chép!";
    setTimeout(() => { feedback.style.display = "none"; }, 2000);
  }).catch(err => {
    alert("Không thể sao chép: " + err);
  });
}
</script>

<h3 id="goi-y-thu-suc">Gợi ý thử sức</h3>

<p>Hãy thử mở rộng mini app để luyện DOM:</p>

<ul>
  <li>Thêm nút "Xóa tất cả" và "Đánh dấu hoàn thành".</li>
  <li>Lưu todo vào localStorage để reload trang vẫn giữ.</li>
  <li>Thêm hiệu ứng hover cho item todo.</li>
  <li>Tạo counter đếm số việc hoàn thành.</li>
  <li>Thêm validate: không cho thêm todo rỗng.</li>
</ul>

<p>Bạn đã làm chủ DOM – kỹ năng cốt lõi của frontend developer! Từ đây, bạn có thể học Fetch API, ES6+ hoặc chuyển sang framework như React. Chúc code vui!</p>
