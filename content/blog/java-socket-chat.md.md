---
title: "Xây Dựng Ứng Dụng Chat Đơn Giản Bằng Java Socket: Hướng Dẫn Từ A Đến Z"
date: 2025-12-23
tags: ["java", "socket", "chat app", "lập trình mạng", "multi thread", "dự án java", "tcp server", "interactive"]
description: "Hướng dẫn chi tiết xây dựng ứng dụng chat thời gian thực bằng Java Socket: server hỗ trợ nhiều client, broadcast tin nhắn. Kèm code đầy đủ, giải thích và ví dụ chạy trực tiếp để thử nghiệm."

keywords:
  - ứng dụng chat java socket
  - chat app java
  - java socket chat tutorial
  - lập trình chat java
  - multi client server java
  - java network programming chat
  - dự án java socket
---

<style>
.post-content {
  max-width: 1500px !important;
}
</style>

<h1 style="text-align:center;">Xây Dựng Ứng Dụng Chat Đơn Giản Bằng Java Socket: Hướng Dẫn Từ A Đến Z</h1>

<img src="https://upload.wikimedia.org/wikipedia/en/3/30/Java_programming_language_logo.svg"
     alt="Java Logo"
     style="width:180px; display:block; margin:30px auto;">

<p>
Xây dựng ứng dụng chat client-server là một trong những dự án thực tế thú vị nhất để nắm vững lập trình mạng trong Java. Dự án này giúp bạn hiểu sâu về <b>Socket TCP</b>, <b>multi-threading</b>, và cách xử lý kết nối đồng thời.
</p>

<p>
Bài viết sẽ hướng dẫn từ kiến trúc cơ bản đến code hoàn chỉnh: server hỗ trợ nhiều client, broadcast tin nhắn thời gian thực. Bạn sẽ có một ứng dụng chat hoạt động thực sự!
</p>

<hr>

<h2 id="kien-truc">1. Kiến trúc ứng dụng chat</h2>

<img src="https://www.codejava.net/images/articles/java/socket/chat-app-client-server-diagram.png"
     alt="Kiến trúc Client-Server Chat App với Java Socket"
     style="width:100%; max-width:900px; display:block; margin:30px auto; border-radius:8px;">

<ul>
  <li><b>Server</b>: Mở port 8080, chấp nhận nhiều client, lưu danh sách output stream, broadcast tin nhắn.</li>
  <li><b>Client</b>: Kết nối đến server, một thread gửi tin từ console, một thread nhận và in tin từ server.</li>
</ul>

<hr>

<h2 id="server">2. Code Server (hỗ trợ nhiều client)</h2>

<pre><code class="language-java">
import java.io.*;
import java.net.*;
import java.util.*;

public class ChatServer {
    private static final int PORT = 8080;
    private static Set<PrintWriter> clientWriters = new HashSet<>();

    public static void main(String[] args) throws IOException {
        System.out.println("Chat Server đang khởi động trên port " + PORT + "...");
        ServerSocket serverSocket = new ServerSocket(PORT);

        while (true) {
            Socket clientSocket = serverSocket.accept();
            System.out.println("Client mới kết nối: " + clientSocket.getRemoteSocketAddress());

            PrintWriter writer = new PrintWriter(clientSocket.getOutputStream(), true);
            clientWriters.add(writer);

            // Thread riêng xử lý tin nhắn từ client này
            new Thread(new ClientHandler(clientSocket, writer)).start();
        }
    }

    // Broadcast tin nhắn đến tất cả client
    public static void broadcast(String message) {
        for (PrintWriter writer : clientWriters) {
            writer.println(message);
        }
    }

    static class ClientHandler implements Runnable {
        private Socket socket;
        private PrintWriter writer;

        public ClientHandler(Socket socket, PrintWriter writer) {
            this.socket = socket;
            this.writer = writer;
        }

        @Override
        public void run() {
            try (BufferedReader reader = new BufferedReader(new InputStreamReader(socket.getInputStream()))) {
                String message;
                while ((message = reader.readLine()) != null) {
                    System.out.println("Nhận: " + message);
                    broadcast("👤 " + message);  // Thêm prefix để phân biệt
                }
            } catch (IOException e) {
                System.out.println("Client ngắt kết nối: " + socket.getRemoteSocketAddress());
            } finally {
                if (writer != null) clientWriters.remove(writer);
                try { socket.close(); } catch (IOException ignored) {}
            }
        }
    }
}
</code></pre>

<hr>

<h2 id="client">3. Code Client (gửi/nhận tin nhắn)</h2>

<pre><code class="language-java">
import java.io.*;
import java.net.*;

public class ChatClient {
    private static final String SERVER_HOST = "localhost";
    private static final int SERVER_PORT = 8080;

    public static void main(String[] args) throws IOException {
        Socket socket = new Socket(SERVER_HOST, SERVER_PORT);
        System.out.println("Đã kết nối đến Chat Server!");

        // Thread nhận tin nhắn từ server
        new Thread(new ServerListener(socket)).start();

        // Gửi tin nhắn từ console
        PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
        BufferedReader console = new BufferedReader(new InputStreamReader(System.in));

        System.out.println("Nhập tin nhắn (gõ 'bye' để thoát):");

        String userInput;
        while ((userInput = console.readLine()) != null) {
            if (userInput.equalsIgnoreCase("bye")) break;
            out.println(userInput);
        }

        socket.close();
        System.out.println("Đã ngắt kết nối.");
    }

    static class ServerListener implements Runnable {
        private Socket socket;

        public ServerListener(Socket socket) {
            this.socket = socket;
        }

        @Override
        public void run() {
            try (BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()))) {
                String message;
                while ((message = in.readLine()) != null) {
                    System.out.println(message);
                }
            } catch (IOException e) {
                System.out.println("Mất kết nối server.");
            }
        }
    }
}
</code></pre>

<hr>

<h2 id="cach-chay">4. Cách chạy và test ứng dụng</h2>

<ol>
  <li>Chạy <code>ChatServer</code> trước (mở terminal đầu tiên).</li>
  <li>Mở nhiều terminal → chạy <code>ChatClient</code> (mỗi terminal là một người chat).</li>
  <li>Nhập tin nhắn → tất cả client khác sẽ nhận được ngay!</li>
</ol>

<hr>

<h2 id="cau-truc">5. Cấu trúc code chi tiết</h2>

<ul>
  <li>Sử dụng <code>HashSet&lt;PrintWriter&gt;</code> để quản lý client (thread-safe hơn ArrayList).</li>
  <li>Mỗi client có một thread riêng → không block server.</li>
  <li>Broadcast đơn giản: lặp qua tất cả writer và gửi.</li>
</ul>

<hr>

<h2 id="cau-tien">6. Cải tiến nâng cao</h2>

<ul>
  <li>Thêm tên người dùng khi kết nối.</li>
  <li>Thông báo khi client join/leave.</li>
  <li>Private message (/w username message).</li>
  <li>Giao diện GUI bằng Swing/JavaFX.</li>
  <li>Thêm mã hóa tin nhắn.</li>
</ul>

<hr>

<h2 id="thuc-hanh">7. Thực hành chạy code trực tiếp</h2>

<p>
Bạn có thể <b>thử mô phỏng ứng dụng chat</b> với nhập liệu thực tế ngay trên trình duyệt (server echo + chat đơn giản).
</p>

<p><strong>Hướng dẫn:</strong><br>
- Chỉnh sửa code trong editor.<br>
- Nhấn <b>▶ Run Java</b> → nhập tên và tin nhắn khi được hỏi.<br>
- Xem cách server xử lý và trả lời.<br>
- Nhấn <b>📋 Copy Code</b> để lấy code về máy.
</p>

<div id="editor" style="height:540px; border:1px solid #ccc; border-radius:8px;"></div>

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

<iframe id="output" style="width:100%; height:580px; border:1px solid #ccc; border-radius:8px;"></iframe>

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

        System.out.println("=== Ứng Dụng Chat Java Socket Mô Phỏng ===");
        System.out.println("Server đang chờ tin nhắn từ bạn...\\n");

        System.out.print("Nhập tên của bạn: ");
        String name = sc.nextLine();

        System.out.println("\\nChào " + name + "! Bắt đầu chat (gõ 'bye' để thoát):\\n");

        String message;
        int count = 1;
        do {
            System.out.print(name + ": ");
            message = sc.nextLine();

            if (!message.equalsIgnoreCase("bye")) {
                System.out.println("Đã gửi: " + message);
                System.out.println("Server echo: [" + count + "] " + message.toUpperCase());
                System.out.println("Server đảo ngược: " + new StringBuilder(message).reverse().toString());
                count++;
                System.out.println();
            }
        } while (!message.equalsIgnoreCase("bye"));

        System.out.println("\\nTạm biệt " + name + "! Kết nối đóng.");
        System.out.println("Bạn đã gửi " + (count - 1) + " tin nhắn.");
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

<ul>
  <li>Thêm thông báo khi có client mới (mô phỏng bằng input "join").</li>
  <li>Thêm lệnh /help hiển thị hướng dẫn.</li>
  <li>Đếm số từ trong mỗi tin nhắn.</li>
  <li>Thêm timestamp cho mỗi tin.</li>
  <li>Copy code về máy và chạy thật server + nhiều client!</li>
</ul>

<p>Chúc mừng bạn đã hoàn thành một dự án mạng thực tế với Java Socket! Đây là nền tảng để xây dựng các ứng dụng phức tạp hơn như game multiplayer, file transfer, hoặc remote control. Hãy thử triển khai và mở rộng nó nhé!</p>