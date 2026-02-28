[English](../README.md) · [العربية](README.ar.md) · [Español](README.es.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [Tiếng Việt](README.vi.md) · [中文 (简体)](README.zh-Hans.md) · [中文（繁體）](README.zh-Hant.md) · [Deutsch](README.de.md) · [Русский](README.ru.md)


# PaperAgentDemo

![Status](https://img.shields.io/badge/status-active-1f6feb)
![LaTeX Workflow](https://img.shields.io/badge/LaTeX-workflow-008080)
![Manuscript](https://img.shields.io/badge/manuscript-latex%2Fmain.tex-0a7ea4)
![Glossary](https://img.shields.io/badge/glossaries-enabled-6f42c1)
![License](https://img.shields.io/badge/license-Not%20Specified-lightgrey)

Một bộ khung bài báo LaTeX gọn nhẹ, bám sát trạng thái thực tế của kho mã, tập trung vào `latex/main.tex`, được thiết kế để kiểm chứng và mở rộng quy trình viết bản thảo với phương trình, thuật toán, bảng biểu, thuật ngữ/từ viết tắt, tài liệu tham khảo và công cụ build PDF.

| Mục | Giá trị |
| --- | --- |
| Tệp bản thảo chính | `latex/main.tex` |
| Kiểu build hiện tại | LaTeX cục bộ (`latexmk` / `pdflatex`) |
| Trạng thái thư mục i18n | `i18n/` đã tồn tại (các tệp ngôn ngữ có thể được bổ sung theo thời gian) |
| Trạng thái tệp giấy phép | Hiện chưa có |

## 📌 Tổng quan

Kho mã này hiện cung cấp:

- Một tệp nguồn bản thảo chính duy nhất: `latex/main.tex`.
- Cấu trúc bài báo mẫu gồm abstract, methods, algorithm, results, discussion và conclusion.
- Bộ gói LaTeX bao phủ các nhu cầu viết nghiên cứu phổ biến (toán học, trích dẫn, glossary, cross-reference).
- Siêu dữ liệu pipeline trong `.auto-readme-work/` để tạo README đa ngôn ngữ.

Lưu ý quan trọng về kho mã:

- `AGENTS.md` mô tả các thư mục dự kiến (`figures/`, `data/`, `artifacts/`, `code/`), nhưng một số thư mục trong đó hiện chưa có trong cây thư mục hiện tại. README này giữ nguyên định hướng đó và ghi rõ các phần còn thiếu.

## ✨ Tính năng

- Soạn thảo công thức toán qua `amsmath`, `amssymb`, `bm`, `mathtools` và `siunitx`.
- Hỗ trợ hình và bảng qua `graphicx`, `subcaption`, `booktabs` và `multirow`.
- Môi trường thuật toán qua `algorithm` và `algpseudocode`.
- Hỗ trợ trích dẫn qua `natbib`.
- Hỗ trợ glossary và acronym qua `glossaries` (`\makeglossaries` đã bật).
- Cross-reference qua `hyperref` và `cleveref`.
- Nội dung ví dụ đã có sẵn: phương trình hàm mục tiêu với regularization `\ell_1`, phương trình SNR theo dB, giả mã gradient descent, bảng so sánh định lượng và các mục tài liệu tham khảo nội tuyến.

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

Cài đặt một môi trường TeX bao gồm các gói được dùng bởi `latex/main.tex`.

Yêu cầu tối thiểu thực tế:

- `latexmk`
- `pdflatex`
- `bibtex` (cho xử lý tài liệu tham khảo trong luồng chuẩn)
- Công cụ glossary cần cho luồng `glossaries` (thường là `makeglossaries` từ bộ TeX)

Giả định:

- Tên gói và phiên bản không được ghim trong kho mã này; hãy dùng bản phân phối TeX Live hoặc MiKTeX tương đối mới.

## 📥 Cài đặt

Clone kho mã và đi vào thư mục:

```bash
git clone <your-fork-or-repo-url>
cd PaperAgentDemo
```

Hiện chưa có bước cài đặt qua package manager nào được định nghĩa trong kho mã.

## 🚀 Cách dùng

| Tác vụ | Lệnh |
| --- | --- |
| Build khuyến nghị | `latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex` |
| Biên dịch nhanh một lượt | `pdflatex latex/main.tex` |
| Dọn tệp phụ trợ | `latexmk -c latex/main.tex` |

Lệnh build chính (khuyến nghị, theo `AGENTS.md`):

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Biên dịch một lượt (lặp nhanh):

```bash
pdflatex latex/main.tex
```

Dọn các tệp phụ trợ LaTeX nhưng giữ PDF:

```bash
latexmk -c latex/main.tex
```

Quy trình dự kiến:

1. Chỉnh sửa nội dung bản thảo trong `latex/main.tex`.
2. Build PDF.
3. Kiểm tra trực quan bố cục và tham chiếu trong PDF đầu ra.

## ⚙️ Cấu hình

Cấu hình hiện tại ở cấp tài liệu nằm trong `latex/main.tex`:

- Lớp tài liệu: `article` với `11pt,a4paper`.
- Bố cục trang: `geometry` với `margin=1in`.
- Giãn dòng: `\onehalfspacing`.
- Thiết lập màu liên kết qua `linkblue` tùy chỉnh và các tùy chọn `hyperref`.
- Acronym và glossary entry được khai báo sẵn cho `CNN`, `SNR`, `HSI` và `event camera`.

Hành vi ignore ở cấp kho mã (`.gitignore`):

- Bỏ qua phần lớn artifact build LaTeX (`*.aux`, `*.log`, `*.pdf`, v.v.).
- Bỏ qua mặc định các thư mục `artifacts/` và `data/`.

## 🧪 Ví dụ

Build bản thảo end-to-end:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Dọn rồi build lại:

```bash
latexmk -c latex/main.tex
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

Biên dịch nhanh khi đang chỉnh một phần:

```bash
pdflatex latex/main.tex
```

## 🛠 Ghi chú phát triển

Hướng dẫn từ `AGENTS.md`:

- Giữ mã nguồn LaTeX dưới các tiêu đề `\section{}` rõ ràng.
- Dùng tiền tố nhãn nhất quán: `eq:` cho phương trình, `fig:` cho hình, `tab:` cho bảng và `alg:` cho thuật toán.
- Ưu tiên tham chiếu qua `\cref{}`.
- Dùng tên tài nguyên viết thường, nối bằng dấu gạch ngang (ví dụ: `figures/snr-comparison.pdf`).
- Thụt lề các khối LaTeX lồng nhau bằng hai dấu cách khi hữu ích.

Cách tiếp cận xác thực:

- Không có bộ kiểm thử tự động.
- Xác thực chính là build LaTeX thành công cộng với kiểm tra trực quan PDF được tạo.

## 🧰 Khắc phục sự cố

Các lỗi thường gặp và cách kiểm tra:

- Build lỗi thiếu package: cài các gói LaTeX còn thiếu từ bản phân phối TeX của bạn.
- Mục glossary không xuất hiện: đảm bảo công cụ glossary đã được cài và chạy lại `latexmk` để các bước glossary được thực thi.
- Cảnh báo citation hoặc reference vẫn còn: build lại bằng `latexmk` (nhiều lượt chạy sẽ được xử lý tự động).
- PDF đầu ra không được git theo dõi: đây là hành vi dự kiến vì `*.pdf` hiện bị ignore trong `.gitignore`.

## 🗺 Lộ trình

Các bước kế tiếp đã lên kế hoạch hoặc nhiều khả năng sẽ làm (suy ra từ tệp kho mã và hướng dẫn):

1. Thêm các thư mục `figures/`, `data/`, `artifacts/` và `code/` khi phạm vi công việc mở rộng.
2. Thêm các tệp README theo từng ngôn ngữ trong `i18n/` khớp với các liên kết điều hướng ngôn ngữ.
3. Thêm script hỗ trợ tùy chọn để tái lập việc tạo hình/bảng trong `code/`.
4. Thiết lập CI để xác minh build nếu dự án phát triển vượt khỏi mức template cục bộ.

## 🤝 Đóng góp

Hiện chưa có quy trình đóng góp chính thức, nên dùng baseline sau:

1. Tạo một nhánh.
2. Thực hiện thay đổi tập trung.
3. Chạy build LaTeX sạch:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error latex/main.tex
```

4. Đính kèm phần tóm tắt rõ ràng về thay đổi bản thảo hoặc công cụ trong PR.

Kiểu commit gợi ý theo hướng dẫn kho mã:

- Dùng tiêu đề commit rõ ràng, ở thể mệnh lệnh.
- Ví dụ: `Add glossary entries for sensor terms`

## 📄 Giấy phép

Hiện chưa có tệp giấy phép trong thư mục gốc của kho mã.

Giả định:

- Mọi quyền và điều khoản tái sử dụng hiện chưa được chỉ định cho đến khi thêm tệp `LICENSE`.

## 📚 Tài liệu tham khảo và Ghi nhận

Bản thảo mẫu trong `latex/main.tex` hiện bao gồm các mục tài liệu tham khảo nội tuyến cho:

- Goodfellow, Bengio, và Courville, *Deep Learning* (MIT Press, 2016).
- Gallego và cộng sự, *Event-based vision: A survey* (IEEE TPAMI, 2022).

Trạng thái ghi nhận:

- Hiện không có phần acknowledgements, sponsor, hoặc donation/support riêng trong các tệp của kho mã.
- Nếu thông tin sponsor/support tồn tại ở nguồn bên ngoài, hãy bổ sung tại đây mà không xóa nội dung kỹ thuật.
