---
title: "Async/Await Trong JavaScript: Hướng Dẫn Chi Tiết Cho Người Mới"
date: 2025-12-23
tags: ["javascript", "async await", "bất đồng bộ", "promise", "fetch api", "lập trình javascript", "frontend", "interactive"]
thumbnail: "https://res.cloudinary.com/anonystick/image/upload/v1618031138/javascript/async-await-trong-javascript.jpg"
description: "Học async/await trong JavaScript từ cơ bản đến nâng cao với ví dụ thực tế. Hiểu rõ cách xử lý bất đồng bộ mà không bị callback hell. Chạy code trực tiếp ngay trên trình duyệt mà không cần cài đặt."

keywords:
  - async await javascript
  - học async await
  - xử lý bất đồng bộ javascript
  - promise javascript
  - fetch api async await
  - javascript tutorial tiếng việt
  - chạy javascript online
---

<style>
.post-content {
  max-width: 1500px !important;
}
</style>

<h1 style="text-align:center;">Async/Await Trong JavaScript: Hướng Dẫn Chi Tiết</h1>

<img src="https://upload.wikimedia.org/wikipedia/commons/6/6a/JavaScript-logo.png"
     alt="JavaScript Logo"
     style="width:160px; display:block; margin:30px auto;">

<p>
Trong lập trình web hiện đại, hầu hết các tác vụ như gọi API, đọc file, hoặc chờ phản hồi từ server đều là <b>bất đồng bộ</b>. 
Nếu không xử lý đúng cách, code sẽ rối rắm (callback hell) hoặc ứng dụng bị treo.
</p>

<p>
<b>Async/await</b> là cú pháp hiện đại nhất của JavaScript (từ ES2017) giúp viết code bất đồng bộ <b>gần giống đồng bộ</b>, dễ đọc và dễ bảo trì hơn rất nhiều so với callback hay Promise thuần.
</p>

<hr>

<h2 id="event-loop">1. JavaScript và Event Loop</h2>

<img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/0*vVsia7i4DvG_uGik.png"
     alt="JavaScript Event Loop"
     style="width:100%; margin:30px 0; border-radius:8px;">

<p>
JavaScript là ngôn ngữ <b>single-threaded</b> với cơ chế <b>Event Loop</b> giúp xử lý bất đồng bộ mà không block main thread.
</p>

<hr>

<h2 id="promise-co-ban">2. Promise cơ bản</h2>

<pre><code class="language-javascript">
const myPromise = new Promise((resolve) => {
    setTimeout(() => {
        resolve("Hoàn thành sau 2 giây!");
    }, 2000);
});

myPromise.then(result => {
    console.log(result);
});
</code></pre>

<hr>

<h2 id="async-await">3. Async/Await là gì?</h2>

<pre><code class="language-javascript">
async function helloAsync() {
    return "Hello từ Async/Await!";
}

helloAsync().then(msg => console.log(msg));

// Sử dụng await
async function demo() {
    const result = await Promise.resolve("Dễ hiểu hơn rồi!");
    console.log(result);
}
demo();
</code></pre>

<hr>

<h2 id="xu-ly-loi">4. Xử lý lỗi với try/catch</h2>

<pre><code class="language-javascript">
async function fetchPost() {
    try {
        const response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
        if (!response.ok) throw new Error("Lỗi mạng");
        const data = await response.json();
        console.log("Tiêu đề bài viết:", data.title);
    } catch (error) {
        console.error("Lỗi:", error.message);
    }
}
fetchPost();
</code></pre>

<hr>

<h2 id="chay-song-song">5. Chạy nhiều Promise song song</h2>

<pre><code class="language-javascript">
async function loadDataParallel() {
    try {
        const [post, user] = await Promise.all([
            fetch("https://jsonplaceholder.typicode.com/posts/1").then(r => r.json()),
            fetch("https://jsonplaceholder.typicode.com/users/1").then(r => r.json())
        ]);
        console.log("Bài viết:", post.title);
        console.log("Tác giả:", user.name);
    } catch (error) {
        console.error("Lỗi khi tải song song:", error);
    }
}
loadDataParallel();
</code></pre>

<hr>

<h2 id="thuc-hanh">6. Thực hành chạy code trực tiếp</h2>

<p>
Bạn có thể <b>chỉnh sửa code và chạy JavaScript với nhập liệu thực tế</b> ngay trên trình duyệt.
</p>

<p><strong>Hướng dẫn:</strong><br>
- Chỉnh sửa code trong editor bên dưới (thử thay đổi thông báo, thêm logic...).<br>
- Nhấn <b>▶ Run JavaScript</b> → chương trình sẽ chạy.<br>
- Khi chạy, sẽ có <b>hộp thoại nhập liệu hiện lên</b> để bạn nhập ID todo.<br>
- Nhấn <b>📋 Copy Code</b> để sao chép code hiện tại.
</p>

<div id="editor" style="height:480px; border:1px solid #ccc; border-radius:8px;"></div>

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

<iframe
  id="output"
  style="width:100%; height:520px; border:1px solid #ccc; border-radius:8px;">
</iframe>

<script src="https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.51.0/min/vs/loader.min.js"></script>

<script>
require.config({
  paths: { vs: "https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.51.0/min/vs" }
});

let editor;

require(["vs/editor/editor.main"], function () {
  editor = monaco.editor.create(document.getElementById("editor"), {
    value: `// Ví dụ async/await với nhập liệu thực tế từ người dùng
// Khi chạy, sẽ hiện hộp thoại để bạn nhập ID!

async function fetchTodoByUserInput() {
    // Hỏi người dùng nhập ID
    let input = prompt(" Nhập ID todo bạn muốn xem (1-200, mặc định 1):", "1");
    
    // Nếu người dùng bấm Cancel hoặc để trống
    if (input === null || input.trim() === "") {
        console.log(" Đã hủy nhập liệu. Dừng chương trình.");
        return;
    }
    
    const todoId = parseInt(input.trim());
    
    // Kiểm tra hợp lệ
    if (isNaN(todoId) || todoId < 1 || todoId > 200) {
        console.error(" ID không hợp lệ! Vui lòng nhập số từ 1 đến 200.");
        return;
    }

    console.log(\` Đang lấy todo số \${todoId} từ API...\`);

    try {
        const response = await fetch(\`https://jsonplaceholder.typicode.com/todos/\${todoId}\`);
        
        if (!response.ok) {
            throw new Error(\`Lỗi HTTP: \${response.status}\`);
        }

        const todo = await response.json();
        
        console.log(" Thành công! Thông tin todo:");
        console.log(\`   ID: \${todo.id}\`);
        console.log(\`   Tiêu đề: \${todo.title}\`);
        console.log(\`   Trạng thái: \${todo.completed ? "Đã hoàn thành " : "Chưa hoàn thành "}\`);
        console.log(\`   User ID: \${todo.userId}\`);

    } catch (error) {
        console.error(" Có lỗi xảy ra khi gọi API:");
        console.error("   " + error.message);
    }
}

// Chạy chương trình
fetchTodoByUserInput();

// Bạn có thể thêm nhiều hàm khác ở dưới đây!
// Ví dụ: hỏi thêm có muốn xem todo khác không?
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
    "https://onecompiler.com/embed/javascript/3.12.0?code=" + encoded;
}

function copyCode() {
  const code = editor.getValue();
  navigator.clipboard.writeText(code).then(() => {
    const feedback = document.getElementById("copyFeedback");
    feedback.style.display = "inline";
    feedback.textContent = "Đã sao chép!";
    
    setTimeout(() => {
      feedback.style.display = "none";
    }, 2000);
  }).catch(err => {
    alert("Không thể sao chép: " + err);
  });
}
</script>

<h3 id="goi-y-thu-suc">Gợi ý thử sức</h3>

<p>Hãy thử chỉnh sửa và chạy code để luyện tập async/await với nhập liệu thực tế!</p>

<ul>
  <li>Thay <code>prompt</code> hỏi thêm tên người dùng và chào theo tên.</li>
  <li>Lặp lại: hỏi có muốn xem todo khác không (dùng vòng lặp + prompt).</li>
  <li>Lấy nhiều ID cùng lúc (nhập dạng "1,5,10" rồi split và dùng Promise.all).</li>
  <li>Thêm xử lý lỗi khi người dùng nhập sai nhiều lần.</li>
  <li>Thay fetch todos bằng posts hoặc users từ API.</li>
</ul>

<p>Bây giờ bạn đã có một playground JavaScript tương tác thực sự – người đọc sẽ cảm thấy như đang code thật! </p>