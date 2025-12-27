---
title: "Lập Trình Hướng Đối Tượng Trong Java: Nền Tảng Và Ứng Dụng Thực Tế"
date: 2025-12-23
tags: ["java", "oop", "lập trình hướng đối tượng", "encapsulation", "inheritance", "polymorphism", "abstraction", "interactive"]
description: "Hướng dẫn chi tiết lập trình hướng đối tượng (OOP) trong Java: 4 nguyên tắc cốt lõi, ví dụ thực tế, diagram minh họa và chạy code trực tiếp trên trình duyệt để thử nghiệm ngay."

keywords:
  - oop java
  - lập trình hướng đối tượng java
  - encapsulation inheritance polymorphism abstraction
  - học oop java
  - java oop tutorial tiếng việt
  - chạy java oop online
---

<style>
.post-content {
  max-width: 1500px !important;
}
</style>

<h1 style="text-align:center;">Lập Trình Hướng Đối Tượng Trong Java: Nền Tảng Và Ứng Dụng Thực Tế</h1>

<img src="https://upload.wikimedia.org/wikipedia/en/3/30/Java_programming_language_logo.svg"
     alt="Java Logo"
     style="width:180px; display:block; margin:30px auto;">

<p>
Lập trình hướng đối tượng (OOP) là <b>cốt lõi thiết kế của Java</b>. Mọi thứ trong Java đều là đối tượng (trừ một số kiểu nguyên thủy). OOP giúp code dễ bảo trì, tái sử dụng và mở rộng – đặc biệt quan trọng trong các dự án lớn như hệ thống ngân hàng, doanh nghiệp.
</p>

<p>
Java thực thi đầy đủ 4 nguyên tắc OOP: <b>Encapsulation</b>, <b>Inheritance</b>, <b>Polymorphism</b>, <b>Abstraction</b>. Bài viết này sẽ giải thích từng nguyên tắc kèm ví dụ thực tế và code chạy trực tiếp.
</p>

<hr>

<h2 id="bon-nguyen-tac">1. Bốn nguyên tắc OOP trong Java</h2>

<img src="https://www.wikitechy.com/wp-content/uploads/2024/09/what-is-oops-in-java.png"
     alt="Bốn nguyên tắc OOP trong Java"
     style="width:100%; max-width:800px; display:block; margin:30px auto; border-radius:8px;">

<hr>

<h2 id="encapsulation">2. Encapsulation (Đóng gói)</h2>

<p>Bảo vệ dữ liệu bằng cách đặt <code>private</code> cho thuộc tính và cung cấp <code>getter/setter</code>.</p>

<pre><code class="language-java">
class Person {
    private String name;
    private int age;

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public int getAge() { return age; }
    public void setAge(int age) {
        if (age > 0) this.age = age;
    }
}
</code></pre>

<hr>

<h2 id="inheritance">3. Inheritance (Kế thừa)</h2>

<p>Lớp con kế thừa thuộc tính và phương thức từ lớp cha bằng <code>extends</code>.</p>

<pre><code class="language-java">
class Animal {
    protected String name;

    public void eat() {
        System.out.println(name + " đang ăn...");
    }
}

class Dog extends Animal {
    public Dog(String name) {
        this.name = name;
    }

    public void bark() {
        System.out.println("Gâu gâu!");
    }
}
</code></pre>

<hr>

<h2 id="polymorphism">4. Polymorphism (Đa hình)</h2>

<p>Cùng một phương thức nhưng hành vi khác nhau tùy đối tượng.</p>

<pre><code class="language-java">
Animal myPet = new Dog("Buddy");
myPet.eat();  // Gọi phương thức của lớp cha
// myPet.bark(); // Không được vì kiểu tham chiếu là Animal
</code></pre>

<hr>

<h2 id="abstraction">5. Abstraction (Trừu tượng hóa)</h2>

<p>Ẩn chi tiết triển khai qua <code>abstract class</code> hoặc <code>interface</code>.</p>

<pre><code class="language-java">
interface Drawable {
    void draw();  // Phương thức trừu tượng
}

class Circle implements Drawable {
    public void draw() {
        System.out.println("Vẽ hình tròn");
    }
}
</code></pre>

<hr>

<h2 id="ung-dung">6. Ứng dụng thực tế</h2>

<ul>
  <li>Framework Spring: Dependency Injection dựa trên OOP</li>
  <li>Android: Activity, Fragment kế thừa từ lớp cơ sở</li>
  <li>Game: Nhân vật kế thừa từ class Character</li>
  <li>Hệ thống ngân hàng: Account → SavingAccount, CheckingAccount</li>
</ul>

<hr>

<h2 id="thuc-hanh">7. Thực hành chạy code trực tiếp</h2>

<p>
Bạn có thể <b>chỉnh sửa và chạy ví dụ OOP thực tế</b> ngay trên trình duyệt.
</p>

<p><strong>Hướng dẫn:</strong><br>
- Chỉnh sửa code (thêm lớp con mới, override phương thức...).<br>
- Nhấn <b>▶ Run Java</b> → chương trình chạy và hiện kết quả.<br>
- Nhập tên động vật khi được hỏi.<br>
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

<iframe id="output" style="width:100%; height:560px; border:1px solid #ccc; border-radius:8px;"></iframe>

<script src="https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.51.0/min/vs/loader.min.js"></script>

<script>
require.config({
  paths: { vs: "https://cdnjs.cloudflare.com/ajax/libs/monaco-editor/0.51.0/min/vs" }
});

let editor;

require(["vs/editor/editor.main"], function () {
  editor = monaco.editor.create(document.getElementById("editor"), {
    value: `import java.util.Scanner;

abstract class Animal {
    protected String name;

    public Animal(String name) {
        this.name = name;
    }

    abstract void makeSound();

    public void eat() {
        System.out.println(name + " đang ăn...");
    }

    public void sleep() {
        System.out.println(name + " đang ngủ Zzz...");
    }
}

class Dog extends Animal {
    public Dog(String name) {
        super(name);
    }

    @Override
    void makeSound() {
        System.out.println(name + ": Gâu gâu!");
    }
}

class Cat extends Animal {
    public Cat(String name) {
        super(name);
    }

    @Override
    void makeSound() {
        System.out.println(name + ": Meo meo!");
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("=== DEMO 4 NGUYÊN TẮC OOP TRONG JAVA ===\\n");

        System.out.print("Nhập tên chó: ");
        String dogName = sc.nextLine();
        Animal dog = new Dog(dogName);

        System.out.print("Nhập tên mèo: ");
        String catName = sc.nextLine();
        Animal cat = new Cat(catName);

        System.out.println("\\n--- Hành động của các động vật ---");
        dog.eat();
        dog.makeSound();
        dog.sleep();

        System.out.println();

        cat.eat();
        cat.makeSound();
        cat.sleep();

        System.out.println("\\n--- Polymorphism demo ---");
        Animal[] pets = {dog, cat};
        for (Animal pet : pets) {
            pet.makeSound();  // Hành vi khác nhau dù cùng kiểu Animal
        }

        System.out.println("\\nThử thêm lớp con mới (Bird, Fish...) và chạy lại nhé!");
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

<p>Hãy thử mở rộng ví dụ để củng cố OOP:</p>

<ul>
  <li>Thêm lớp <code>Bird</code> với <code>makeSound()</code> là "Chíp chíp!" và phương thức <code>fly()</code>.</li>
  <li>Tạo interface <code>Swimmable</code> và implement cho lớp <code>Fish</code>.</li>
  <li>Thêm encapsulation: private field + getter/setter cho <code>name</code>.</li>
  <li>Dùng <code>instanceof</code> để kiểm tra loại động vật và gọi phương thức riêng.</li>
  <li>Tạo mảng <code>Animal[] zoo</code> và cho tất cả động vật ăn + kêu.</li>
</ul>

<p>Bạn đã nắm vững nền tảng OOP – kỹ năng quan trọng nhất để viết code Java chuyên nghiệp! Tiếp theo có thể học Collection, Exception Handling hoặc Spring Framework. Chúc bạn code vui!</p>
