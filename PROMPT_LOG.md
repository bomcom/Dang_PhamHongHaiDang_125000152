# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

- **Họ và tên:** Phạm Hồng Hải Đăng
- **MSSV:** 125000152
- **Tên đề tài Website:** Landing Page Giới thiệu Tài liệu Cốt lõi Lộ trình Full-Stack AI Engineer
- **Công cụ AI đã sử dụng:** Antigravity (Google DeepMind AI Engine)

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)

> **Prompt khởi tạo thực tế của sinh viên:**
> 
> *"trước tiên là tạo thư mục riêng cho đề bài riêng này Dang_PhamHongHai_125000152*  
> *để tuân thủ tính kiểm soát , trước tiên là chúng ta cứ tạo indel.html rồi dừng lại để tôi đọc review code*  
> *làm chủ đề landing Page giới thiệu tài liệu 'Machine-Learning-Systems-Vol1.pdf' và 'mml-book.pdf'*  
> *cấu trúc html sau đây theo khung trực quan:*  
> *<DOCTYPE html>*  
> *<html lang="vi">*  
> *<head> giới thiệu một số tài liệu dành cho việc tự học cho mục tiêu thành full-stack AI </head>*  
> *<img> logo sách </img>*  
> *<nav class="menu">*  
> *<ul> chứa gồm 3 nút button dẫn tới thông tin liên hệ ở chân trang , số điện thoại liên hệ ( cũng ở chân trang) , email ( cũng ở chân trang)</ul>*  
> *<article>mml-book.pdf <div>giới thiệu nói về tài liệu và giải thích </div></article>*  
> *<article>maching-lreaning-System <div> giới thiệu và giải thích </div></article>*  
> *(bạn sẽ hiểu tại sao tôi dùng <article> thay vì <section>)*  
> *còn <section> thì có lẽ chỉ là trích dẫn lời bình luận thôi như chú bổ sung giải thích*  
> *<footer> thông tin liên hệ </footer>"*

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML5 & Kiểm soát Kiến trúc Thẻ Ngữ Nghĩa

- **Prompt đã dùng:** Prompt khởi tạo cấu trúc xương ở Mục 1, nhấn mạnh yêu cầu AI dừng lại ngay sau khi viết xong `index.html` để sinh viên kiểm tra (Code Review).
- **Kết quả AI tạo ra:**
  - AI khởi tạo tệp `index.html` với đầy đủ 5 thành phần Semantic HTML5 bắt buộc: `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<footer>`.
  - Phân chia 2 cuốn sách vào 2 thẻ `<article>` riêng biệt và phần trích dẫn bình luận chuyên gia vào thẻ `<section>`.
  - Sử dụng thẻ `<address>` bên trong `<footer>` để chứa 3 thông tin liên hệ (người phụ trách, hotline, email) tương ứng với 3 liên kết anchor trên menu.
- **Nhận xét & Tinh chỉnh của SV:**
  - **Lý do chọn `<article>` thay vì `<section>` cho 2 cuốn sách:** Qua việc nghiên cứu tài liệu W3C và MDN, sinh viên nắm rõ quy tắc *Syndication Test (Tính tự thân trọn vẹn)*. Mỗi cuốn sách (`mml-book.pdf` và `Machine-Learning-Systems-Vol1.pdf`) là một thực thể độc lập có tiêu đề, tác giả, giá trị nội dung riêng biệt; dù cắt ra khỏi trang web thì người đọc vẫn hiểu trọn vẹn. Do đó, dùng `<article>` là chuẩn xác nhất. Thẻ `<section>` chỉ dùng cho phần bình luận, chú giải bổ sung vì nó phụ thuộc vào ngữ cảnh chung.
  - **Áp dụng chuẩn thẻ `<address>`:** Vận dụng kiến thức W3C đã ôn tập, thẻ `<address>` được đặt trong `<footer>`, chứa các đường link liên lạc `<a href="tel:...">` và `<a href="mailto:...">`, tuyệt đối không lồng các thẻ phân đoạn tiêu đề lớn `<h1>`-`<h6>` vào bên trong `<address>`.

---

### Lần 2: Thiết kế Hệ thống CSS Variables, Bố cục CSS Grid & Kỹ nghệ Component Button

- **Prompt đã dùng:**
  > *"bạn làm lập trình kỹ nghệ CSS*  
  > *phần root gồm:*  
  > *khung màu chủ đạo sẽ làm màu đen và màu chủ đạo sẽ là màu xanh dương (do Các gam màu lạnh (Xanh dương, Xanh lá, Tím): Tạo cảm giác sang trọng, bí ẩn hoặc hài hòa giữa tự nhiên và hiện đại - vì thế tôi chọn màu xanh dương)*  
  > *và chuẩn CSS grid*  
  > *còn về component của nút button thì màu trắng (nền và đường viền trong suốt)"*

- **Kết quả AI tạo ra:**
  - Thiết lập `:root` với bảng màu chuẩn công nghệ: Nền Deep Space đen xanh thẳm (`#060b14`), màu chủ đạo xanh dương (`#1d4ed8`), điểm nhấn Cyan (`#38bdf8`), chữ trắng (`#ffffff`).
  - Dựng bố cục `.books-showcase` bằng **CSS Grid** (`display: grid; grid-template-columns: repeat(2, 1fr);`) chia đều 2 cột cân đối cho 2 thẻ bài viết `<article>`, tự động thích ứng 1 cột trên Mobile.
  - Component nút `.nav-link` có chữ màu trắng, nền và đường viền hoàn toàn trong suốt (`background: transparent; border: 1px solid transparent;`), khi rê chuột (`:hover`) sẽ phát sáng viền nhẹ màu Cyan và nâng độ cao tương tác.

- **Thách thức gặp phải:**
  - Khi đặt nút có nền và viền trong suốt trên nền tối, người dùng dùng bàn phím để điều hướng (Tab key) có thể khó nhận diện vị trí con trỏ chuột/focus.
- **Cách sửa prompt & Tinh chỉnh (Debug):**
  - Bổ sung hiệu ứng `:focus-visible` với đường viền sáng nổi bật `outline: 2px solid var(--accent-cyan); outline-offset: 3px;` để đảm bảo tiêu chuẩn trợ năng tiếp cận (Accessibility / a11y) theo W3C mà vẫn giữ nguyên thiết kế nền trong suốt khi hiển thị bình thường.

---

### Lần 3: Tích hợp Thư viện Hiệu ứng Chuyển động (Animate.css & AOS)

- **Prompt đã dùng:**
  - Nhúng CDN thư viện `animate.min.css` và `aos.css` vào thẻ `<head>` của `index.html`.
  - Tích hợp script khởi tạo `AOS.init()` trước khi đóng thẻ `</body>`.
- **Kết quả AI tạo ra:**
  - Tiêu đề Hero section áp dụng hiệu ứng `animate__animated animate__fadeInUp` và `animate__fadeInDown` mượt mà khi vừa tải trang.
  - Hai thẻ bài viết `<article>` áp dụng hiệu ứng cuộn trang `data-aos="fade-up"` (cuốn thứ hai có thêm `data-aos-delay="200"` để xuất hiện so le nhịp nhàng).
- **Thách thức gặp phải:**
  - Nếu cuộn trang nhanh, hiệu ứng AOS có thể bị giật hoặc kích hoạt lặp lại không cần thiết gây rối mắt người đọc.
- **Cách tinh chỉnh (Fix):**
  - Cấu hình tham số thư viện trong mã JavaScript: `AOS.init({ duration: 800, once: true, offset: 100 });`.
  - Thuộc tính `once: true` đảm bảo hiệu ứng chỉ diễn ra 1 lần khi cuộn tới, giúp trang web đạt chuẩn 60fps mượt mà, không lạm dụng animation gây mỏi mắt người dùng.

### Lần 4: Phản biện Học thuật & Mở rộng Bản đồ 4 Trụ Cột Tri Thức (Full-Stack AI Layers)

- **Prompt đã dùng:**
  > *"mà tôi thấy chỉ với 2 tài liệu đó là có thật sự là đủ và cần cho lộ trình full-stack AI không?"*  
  > *"vậy thì bổ sung thêm <article> cho mảnh ghép tầng 2 và mảnh ghép tầng 4 để cho có thôi , lấy tài liệu kinh điển làm đại diện như mml-book"*

- **Kết quả AI tạo ra:**
  - AI phân tích cấu trúc 4 tầng của một kỹ sư Full-Stack AI: Tầng 1 (Toán học), Tầng 2 (Kiến trúc Học sâu & LLMs), Tầng 3 (Hạ tầng ML Systems & MLOps), Tầng 4 (Kỹ nghệ Phần mềm Sản phẩm Đầu-Cuối).
  - Bổ sung thêm 2 thẻ `<article>` đại diện cho 2 tài liệu kinh điển thế giới:
    1. **Trụ cột 02 (Tầng 2):** *"Deep Learning"* (Ian Goodfellow, Yoshua Bengio - MIT Press) - bao quát Transformers, Attention, Generative AI.
    2. **Trụ cột 04 (Tầng 4):** *"Designing Data-Intensive Applications - DDIA"* (Martin Kleppmann - O'Reilly) - bao quát Vector Database, Streaming SSE/WebSockets, hệ thống phân tán chịu tải cao.
  - Cập nhật tiêu đề lưới thành *"Bốn Trụ Cột Tri Thức Toàn Diện (Full-Stack 4 Layers)"* và căn chỉnh CSS Grid tự động tạo thành mạng lưới 2x2 cards tuyệt đẹp, cân xứng hoàn hảo trên Desktop.

- **Nhận xét & Tinh chỉnh của SV:**
  - Đây là bước thể hiện rõ năng lực **phản biện và tư duy hệ thống** của sinh viên: Không chấp nhận một sản phẩm chỉ có 2 tài liệu khi đề tài là "Full-Stack AI", mà chủ động nhận diện khoảng trống kiến thức (thiếu tầng Deep Learning và tầng Kỹ nghệ Sản phẩm) để ra lệnh cho AI hoàn thiện bản đồ tri thức toàn diện.
  - Về mặt CSS, sinh viên yêu cầu kiểm tra thuộc tính `grid-column: 1 / -1;` cho tiêu đề `.section-title` để đảm bảo tiêu đề luôn nằm chính giữa toàn bộ hệ thống lưới 2x2.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding

### AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?
1. **Viết boilerplate CSS & Hệ thống biến `:root`:** AI giúp sinh nhanh các mã màu hex, tính toán độ mờ rgba, các hàm chuyển động `cubic-bezier`, bóng đổ `box-shadow` và cấu trúc truy vấn Media Queries responsive mà không cần phải gõ thủ công từng dòng.
2. **Tìm nạp thư viện CDN & Biểu tượng SVG:** Tự động lấy đúng link CDN phiên bản mới nhất của Animate.css và AOS.js, kèm các thuộc tính chuẩn SEO và Accessibility (`aria-label`, `aria-labelledby`).
3. **Soạn thảo nội dung học thuật có chiều sâu:** AI nhanh chóng trích xuất các ý chính của 2 cuốn giáo trình chuyên sâu (`mml-book` về Đại số tuyến tính, Giải tích đa biến; `Machine Learning Systems` về Pipeline, Distributed Training, Model Serving) giúp trang web có nội dung thực tế và chuyên nghiệp.

### Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?
1. **Người lập trình phải là "Kiến trúc sư trưởng", không giao phó toàn bộ cho AI:** Nếu chỉ nói *"làm cho tôi một website giới thiệu sách"*, AI sẽ sinh ra một mớ thẻ `<div>` lộn xộn (div-soup) và giao diện đại trà. Chỉ khi người học có kiến thức vững chắc (hiểu rõ khi nào dùng `<article>`, khi nào dùng `<section>`, `<address>` cấm lồng thẻ gì) và ra lệnh cụ thể, AI mới tạo ra sản phẩm chuẩn W3C đạt điểm tối đa.
2. **Nguyên tắc "Prompt từng bước có kiểm soát" (Iterative Prompting):** Không nên yêu cầu AI làm hết từ HTML, CSS đến JavaScript trong một lần duy nhất. Thay vào đó, hãy chia nhỏ: *Khởi tạo khung HTML -> Yêu cầu dừng lại để Review -> Ra chỉ lệnh Kỹ nghệ CSS -> Tích hợp hiệu ứng và gỡ lỗi*. Cách tiếp cận này giúp kiểm soát 100% mã nguồn và phát hiện lỗi sai kiến trúc ngay từ đầu.
3. **Chỉ đạo rõ ràng về mặt thẩm mỹ và ngữ nghĩa:** Việc định hướng rõ gam màu (màu xanh dương lạnh tạo cảm giác sang trọng, bí ẩn, công nghệ cao), bố cục CSS Grid, và đặc tính component (button nền và viền trong suốt, chữ trắng) giúp AI đưa ra kết quả chính xác ngay từ lần đầu tiên mà không phải sửa lại nhiều lần.
