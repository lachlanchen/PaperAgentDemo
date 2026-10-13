[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


[![LazyingArt banner](https://github.com/lachlanchen/lachlanchen/raw/main/figs/banner.png)](https://lazying.art)

# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

Một bộ khung bài báo LaTeX gọn nhẹ, phản ánh đúng kho mã và tập trung vào `latex/main.tex`, được thiết kế để kiểm chứng và mở rộng quy trình soạn thảo bản thảo bằng phương trình, thuật toán, bảng biểu, glossary/thuật ngữ viết tắt, tài liệu tham khảo và công cụ biên dịch PDF.

## 🧩 Tóm tắt nhanh

| Mục | Giá trị |
| --- | --- |
| Tệp bản thảo chính | `latex/main.tex` |
| Kiểu build hiện tại | LaTeX cục bộ (`latexmk` / `pdflatex`) |
| Tình trạng thư mục i18n | `i18n/` đã tồn tại (tệp ngôn ngữ có thể được bổ sung theo thời gian) |
| Tình trạng tệp giấy phép | Hiện chưa có |

## 📌 Tổng quan

Kho lưu trữ này hiện cung cấp:

- Một tệp nguồn bản thảo chính duy nhất: `latex/main.tex`.
- Cấu trúc bài báo mẫu với abstract, methods, algorithm, results, discussion và conclusion.
- Bộ gói LaTeX cho các tác vụ viết bài nghiên cứu thông dụng (toán học, trích dẫn, glossary, cross-references).
- Siêu dữ liệu pipeline trong `.auto-readme-work/` cho việc sinh README đa ngôn ngữ.

Lưu ý quan trọng của kho:

- `AGENTS.md` mô tả các thư mục dự kiến (`figures/`, `data/`, `artifacts/`, `code/`), nhưng một số trong số đó chưa tồn tại trong cây hiện tại. README này giữ nguyên mục tiêu đó và ghi rõ các phần còn thiếu.

## ✨ Tính năng

- Soạn thảo toán bằng `amsmath`, `amssymb`, `bm`, `mathtools`, và `siunitx`.
- Hỗ trợ hình ảnh và bảng qua `graphicx`, `subcaption`, `booktabs`, và `multirow`.
- Môi trường thuật toán qua `algorithm` và `algpseudocode`.
- Hỗ trợ trích dẫn qua `natbib`.
- Hỗ trợ glossary và thuật ngữ viết tắt qua `glossaries` (`\makeglossaries` đã được bật).
- Cross-referencing qua `hyperref` và `cleveref`.
- Nội dung ví dụ đã có sẵn: phương trình hàm mục tiêu với quy chuẩn hóa `\ell_1`, phương trình SNR theo dB, giả mã gradient descent, bảng so sánh định lượng, và mục tài liệu tham khảo nội tuyến.

## 🧭 Cấu trúc dự án

```text
PaperAgentDemo/
├── .auto-readme-work/
│   └── 20260228_200112/
│       ├── pipeline-context.md
│       ├── language-nav-root.md
│       ├── language-nav-i18n.md
│       └── translation-plan.txt
├── .gitignore
├── AGENTS.md
├── README.md
├── i18n/                         # currently present; language README files may be added over time
└── latex/
    ├── main.tex                  # primary manuscript source
    ├── main.acn                  # generated glossary/acronym artifact
    ├── main.glo                  # generated glossary artifact
    └── main.ist                  # glossary style artifact
```

## ✅ Điều kiện tiên quyết

Cài đặt một môi trường TeX bao gồm các gói được sử dụng trong `latex/main.tex`.

Yêu cầu thực tế tối thiểu:

- `latexmk`
- `pdflatex`
- `bibtex` (cho xử lý thư mục tham khảo trong luồng chuẩn)
- Công cụ glossary cần thiết cho quy trình `glossaries` (thường là `makeglossaries` từ bản phân phối TeX)

Giả định:

- Tên gói và phiên bản không được khóa cứng trong kho; nên dùng bản phân phối TeX Live hoặc MiKTeX tương đối mới.

## 📥 Cài đặt

Clone và vào thư mục dự án:

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

Hiện chưa có bước cài đặt bổ sung qua package manager nào được định nghĩa trong repo.

## 🚀 Cách sử dụng

| Nhiệm vụ | Lệnh |
| --- | --- |
| Build đề xuất | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| Biên dịch nhanh một lượt | `pdflatex latex/main.tex` |
| Dọn file phụ | `latexmk -c latex/main.tex` |

Lệnh build chính (khuyến nghị, theo `AGENTS.md`):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Biên dịch một lượt (lặp nhanh):

```bash
pdflatex latex/main.tex
```

Dọn file phụ LaTeX nhưng giữ lại PDF:

```bash
latexmk -c latex/main.tex
```

Quy trình mong đợi:

1. Chỉnh sửa nội dung trong `latex/main.tex`.
2. Build PDF.
3. Kiểm tra trực quan bố cục và tài liệu tham khảo trong PDF đầu ra.

## ⚙️ Cấu hình

Cấu hình cấp tài liệu hiện tại nằm trong `latex/main.tex`:

- Document class: `article` với `11pt,a4paper`.
- Bố cục trang: `geometry` với `margin=1in`.
- Khoảng cách dòng: `\onehalfspacing`.
- Thiết lập màu liên kết qua `linkblue` tùy chỉnh và các tùy chọn `hyperref`.
- Các mục glossary và acronym được định nghĩa trước cho `CNN`, `SNR`, `HSI`, và `event camera`.

Hành vi bỏ qua ở cấp repository (`.gitignore`):

- Bỏ qua hầu hết artifact build của LaTeX (`*.aux`, `*.log`, `*.pdf`, v.v.).
- Bỏ qua mặc định các thư mục `artifacts/` và `data/`.

## 🧪 Ví dụ

Build bản thảo từ đầu đến cuối:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Dọn rồi build lại:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Biên dịch nhanh khi đang chỉnh sửa một phần:

```bash
pdflatex latex/main.tex
```

## 🛠 Ghi chú phát triển

Hướng dẫn từ `AGENTS.md`:

- Giữ mã nguồn LaTeX theo các mục `\section{}` rõ ràng.
- Dùng tiền tố nhãn nhất quán: `eq:` cho phương trình, `fig:` cho hình, `tab:` cho bảng, và `alg:` cho thuật toán.
- Ưu tiên trỏ tham chiếu bằng `\cref{}`.
- Dùng tên tài nguyên viết thường, nối bởi dấu gạch ngang (ví dụ: `figures/snr-comparison.pdf`).
- Thụt đầu dòng các khối LaTeX lồng nhau bằng hai khoảng trắng khi cần thiết.

Cách xác thực:

- Không có test tự động.
- Xác thực chính là build LaTeX thành công rồi kiểm tra trực quan PDF đã tạo.

## 🧰 Xử lý sự cố

Một số lỗi phổ biến và kiểm tra:

- Build thất bại do thiếu gói: cài thêm các gói LaTeX còn thiếu từ bản phân phối TeX của bạn.
- Mục glossary không xuất hiện: kiểm tra đã cài đủ công cụ glossary và chạy lại `latexmk` để các bước glossary chạy.
- Cảnh báo trích dẫn hoặc tham chiếu vẫn còn: build lại bằng `latexmk` (các lượt chạy lặp lại sẽ được xử lý tự động).
- PDF đầu ra không được git theo dõi: đây là hành vi mong đợi vì `*.pdf` hiện đang bị ignore trong `.gitignore`.

## 🗺 Lộ trình

Các bước kế tiếp dự kiến hoặc rất có thể (suy diễn từ tệp repository và hướng dẫn):

1. Thêm `figures/`, `data/`, `artifacts/`, và `code/` khi phạm vi công việc mở rộng.
2. Thêm tệp README theo ngôn ngữ trong `i18n/` theo đúng liên kết chuyển ngôn ngữ.
3. Thêm script hỗ trợ tùy chọn để tạo hình/bảng tái lập trong `code/`.
4. Triển khai CI để xác minh build nếu dự án mở rộng vượt khỏi khuôn mẫu local.

## 🤝 Đóng góp

Hiện chưa có quy trình đóng góp chính thức, vì vậy dùng baseline sau:

1. Tạo một nhánh mới.
2. Thực hiện thay đổi tập trung.
3. Chạy một lần build LaTeX sạch:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. Kèm theo phần tóm tắt rõ ràng về thay đổi bản thảo hoặc tooling trong PR.

Phong cách commit gợi ý theo hướng dẫn repository:

- Dùng tiêu đề commit rõ ràng theo mệnh lệnh.
- Ví dụ: `Add glossary entries for sensor terms`

## 📄 Giấy phép

Không có tệp license trong thư mục gốc của repository.

Giả định:

- Tất cả quyền và điều khoản tái sử dụng hiện chưa được xác định cho đến khi có tệp `LICENSE`.

## 📚 Tài liệu tham khảo và lời cảm ơn

Bản thảo mẫu trong `latex/main.tex` hiện đang bao gồm các mục tài liệu tham khảo nội tuyến cho:

- Goodfellow, Bengio, và Courville, *Deep Learning* (MIT Press, 2016).
- Gallego et al., *Event-based vision: A survey* (IEEE TPAMI, 2022).

Tình trạng ghi nhận:

- Hiện chưa có mục acknowledgements riêng trong bản thảo.
- Các liên kết tài trợ/hỗ trợ được tập trung trong mục **❤️ Support** ở trên.


## ❤️ Support

| Donate | PayPal | Stripe |
| --- | --- | --- |
| [![Donate](https://camo.githubusercontent.com/24a4914f0b42c6f435f9e101621f1e52535b02c225764b2f6cc99416926004b7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f6e6174652d4c617a79696e674172742d3045413545393f7374796c653d666f722d7468652d6261646765266c6f676f3d6b6f2d6669266c6f676f436f6c6f723d7768697465)](https://chat.lazying.art/donate) | [![PayPal](https://camo.githubusercontent.com/d0f57e8b016517a4b06961b24d0ca87d62fdba16e18bbdb6aba28e978dc0ea21/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f50617950616c2d526f6e677a686f754368656e2d3030343537433f7374796c653d666f722d7468652d6261646765266c6f676f3d70617970616c266c6f676f436f6c6f723d7768697465)](https://paypal.me/RongzhouChen) | [![Stripe](https://camo.githubusercontent.com/1152dfe04b6943afe3a8d2953676749603fb9f95e24088c92c97a01a897b4942/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5374726970652d446f6e6174652d3633354246463f7374796c653d666f722d7468652d6261646765266c6f676f3d737472697065266c6f676f436f6c6f723d7768697465)](https://buy.stripe.com/aFadR8gIaflgfQV6T4fw400) |
