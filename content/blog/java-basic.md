---
title: "Java Cơ Bản – Học Lý Thuyết & Chạy Code Trực Tiếp"
date: 2025-12-23
tags: ["java", "cơ bản", "lập trình", "interactive"]
description: "Học Java cơ bản từ con số 0 với lý thuyết dễ hiểu, ví dụ minh họa và chạy code trực tiếp ngay trên trình duyệt mà không cần cài đặt. Bao gồm biến, điều kiện, vòng lặp, nhập liệu và bài tập thực hành."

keywords: 
  - java cơ bản
  - học java
  - lập trình java cho beginner
  - java tutorial tiếng việt
  - chạy java online
  - java interactive
  - hướng dẫn java từ đầu
---

<style>
.post-content {
  max-width: 1500px !important;
}
</style>

<h1 style="text-align:center;">Java Cơ Bản Cho Người Mới Bắt Đầu</h1>

<img src="https://upload.wikimedia.org/wikipedia/en/3/30/Java_programming_language_logo.svg"
     alt="Java Logo"
     style="width:180px; display:block; margin:30px auto;">

<p>
Java là ngôn ngữ lập trình <b>biên dịch</b>, <b>hướng đối tượng</b>, được phát triển bởi Sun Microsystems và hiện nay thuộc Oracle. Java được sử dụng rộng rãi trong phát triển ứng dụng doanh nghiệp, web backend, Android và các hệ thống lớn.
</p>

<p>
Ưu điểm lớn nhất của Java là khả năng chạy đa nền tảng nhờ <b>Java Virtual Machine (JVM)</b>
với triết lý nổi tiếng: <b>Write Once, Run Anywhere</b>.
</p>

<hr>

<h2 id="java-hoat-dong-nhu-the-nao">1. Java hoạt động như thế nào?</h2>

<img
  src="https://softwareperformancenotes.github.io/img/jvmarch.jpg"
  alt="JVM Architecture Diagram"
  style="width:100%; margin:25px 0;">


<p>
Khi bạn viết chương trình Java (<code>.java</code>), quá trình thực thi sẽ diễn ra như sau:
</p>

<ul>
  <li>Mã nguồn được <b>javac</b> biên dịch thành <b>bytecode (.class)</b></li>
  <li>Bytecode chạy trên <b>JVM</b>, không phụ thuộc hệ điều hành</li>
  <li>JVM chịu trách nhiệm quản lý bộ nhớ, bảo mật và tối ưu hiệu năng</li>
</ul>

<p>
Nhờ JVM, cùng một chương trình Java có thể chạy trên Windows, Linux, macOS
mà không cần chỉnh sửa mã nguồn.
</p>

<hr>

<h2 id="cau-truc-chuong-trinh-java">2. Cấu trúc chương trình Java</h2>

<p>
Mọi chương trình Java đều phải nằm trong một <b>class</b>.
Hàm <code>main</code> là điểm bắt đầu khi chương trình được chạy.
</p>

<pre><code class="language-java">
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Xin chào Java");
    }
}
</code></pre>

<ul>
  <li><code>public</code>: phạm vi truy cập</li>
  <li><code>class</code>: khai báo lớp</li>
  <li><code>main</code>: hàm chính</li>
  <li><code>System.out.println</code>: in dữ liệu ra màn hình</li>
</ul>

<hr>

<h2 id="bien-va-kieu-du-lieu-trong-java">3. Biến và kiểu dữ liệu trong Java</h2>

<img
  src="https://media.geeksforgeeks.org/wp-content/uploads/20250619155321977504/data_types_in_java.webp"
  alt="Java Data Types Diagram"
  style="width:100%; margin:25px 0;">


<p>
Java là ngôn ngữ <b>kiểu tĩnh</b>, nghĩa là bạn phải xác định kiểu dữ liệu cho biến
ngay khi khai báo.
</p>

<ul>
  <li><b>int</b> – số nguyên</li>
  <li><b>double</b> – số thực</li>
  <li><b>char</b> – ký tự</li>
  <li><b>boolean</b> – true / false</li>
  <li><b>String</b> – chuỗi ký tự</li>
</ul>

<pre><code class="language-java">
int age = 20;
double score = 8.5;
String name = "Java Learner";
</code></pre>

<hr>

<h2 id="cau-lenh-dieu-kien">4. Câu lệnh điều kiện</h2>

<p>
Câu lệnh điều kiện giúp chương trình đưa ra quyết định dựa trên dữ liệu đầu vào.
</p>

<pre><code class="language-java">
int age = 18;

if (age >= 18) {
    System.out.println("Bạn đủ tuổi");
} else {
    System.out.println("Bạn chưa đủ tuổi");
}
</code></pre>

<hr>

<h2 id="vong-lap-trong-java">5. Vòng lặp trong Java</h2>

<p>
Vòng lặp cho phép thực thi một khối lệnh nhiều lần.
</p>

<ul>
  <li><b>for</b>: biết trước số lần lặp</li>
  <li><b>while</b>: lặp theo điều kiện</li>
  <li><b>do-while</b>: chạy ít nhất một lần</li>
</ul>

<pre><code class="language-java">
for (int i = 1; i <= 5; i++) {
    System.out.println("Lần chạy: " + i);
}
</code></pre>

<hr>

<h2 id="nhap-du-lieu-tu-ban-phim">6. Nhập dữ liệu từ bàn phím</h2>

<p>
Java sử dụng lớp <code>Scanner</code> để nhập dữ liệu từ người dùng.
</p>

<pre><code class="language-java">
import java.util.Scanner;

Scanner sc = new Scanner(System.in);
System.out.print("Nhập tên: ");
String name = sc.nextLine();
</code></pre>

<hr>

<h2 id="thuc-hanh-java-truc-tiep">7. Thực hành Java trực tiếp</h2>

<p>
Bạn có thể <b>chỉnh sửa code và chạy chương trình Java với nhập liệu thực tế</b> ngay trên trình duyệt.
</p>

<p><strong>Hướng dẫn:</strong><br>
- Chỉnh sửa code trong editor nếu muốn.<br>
- Nhấn <b>▶ Run Java</b> → chương trình sẽ chạy.<br>
- <b>Khi chạy, sẽ hiện ô nhập liệu ngay trong khung kết quả</b> để bạn nhập tên và tuổi.<br>
- Nhấn <b>📋 Copy Code</b> để sao chép toàn bộ code hiện tại.
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
    background:#007acc;
    color:white;
    border:none;
    cursor:pointer;
    font-size:16px;
    font-weight:bold;
    border-radius:6px 0 0 6px;
    margin-right:0;">
    ▶ Run Java
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
    value: `import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Nhập tên của bạn: ");
        String name = sc.nextLine();

        System.out.print("Nhập tuổi của bạn: ");
        int age = sc.nextInt();

        System.out.println("\\n--- Kết quả ---");
        System.out.println("Xin chào " + name + "!");

        if (age >= 18) {
            System.out.println("Bạn đã đủ tuổi trưởng thành ");
        } else {
            System.out.println("Bạn chưa đủ tuổi trưởng thành ");
        }

        // Tính tổng các số từ 1 đến tuổi
        int sum = 0;
        for (int i = 1; i <= age; i++) {
            sum += i;
        }

        System.out.println("Tổng các số từ 1 đến " + age + " = " + sum);

        System.out.println("\\nCảm ơn bạn đã thử chương trình!");
    }
}`,
    language: "java",
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
    "https://onecompiler.com/embed/java?code=" + encoded;
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

<p>Hãy thử chỉnh sửa code và chạy lại để luyện tập nhé!</p>

<ul>
  <li>Tính tổng chỉ các số <b>chẵn</b> từ 1 đến tuổi.</li>
  <li>Thêm nhập giới tính (nam/nữ) và in lời chào: "Chào anh [tên]" hoặc "Chào chị [tên]".</li>
  <li>Thay vì tính tổng, in <b>bảng cửu chương</b> của một số người dùng nhập.</li>
  <li>Thêm kiểm tra tuổi hợp lệ (0 ≤ tuổi ≤ 150), nếu không thì báo lỗi.</li>
  <li>Thêm vòng lặp hỏi người dùng có muốn chạy lại chương trình không.</li>
</ul>

<p>Hoàn thành các thử thách này là bạn đã nắm chắc các khái niệm cơ bản nhất của Java rồi đấy!</p>
