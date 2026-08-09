## 1. Head elements


```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Học HTML từ cơ bản đến nâng cao">
    <title>My First Web Page</title>
    <link rel="icon" href="favicon.ico" type="image/x-icon">
    <link rel="stylesheet" href="style.css">
</head>
```

### 1.1. `<meta>`

Thẻ `<meta>` dùng để khai báo metadata (siêu dữ liệu) cho trang HTML — **thông tin mô tả** về trang **nhưng không hiển thị trực tiếp cho người dùng**. Đây cũng là thẻ tự đóng (self-closing), đặt trong `<head>`.

```html
<!-- Cơ bản -->
<meta charset="UTF-8">

<!-- Đầy đủ -->
<meta name="description" content="Trang học HTML cơ bản" lang="vi">
```

Các thuộc tính chính:

- **charset**: khai báo bảng mã ký tự cho trang, nên đặt là thẻ `<meta>` đầu tiên trong `<head>` (trước cả `<title>`) để trình duyệt đọc đúng encoding ngay từ đầu. Giá trị gần như duy nhất được dùng hiện nay là `UTF-8`.

    ```html
    <meta charset="UTF-8">
    ```

- **name** + **content**: hai thuộc tính luôn đi cùng nhau — `name` khai báo loại metadata, `content` là giá trị tương ứng. Gồm các loại phổ biến:

    | `name` | Tác dụng | Ví dụ |
    |---|---|---|
    | `viewport` | Cấu hình hiển thị trên di động | `<meta name="viewport" content="width=device-width, initial-scale=1.0">` |
    | `description` | Mô tả trang, hiển thị trong kết quả tìm kiếm (SEO) | `<meta name="description" content="Học HTML từ cơ bản đến nâng cao">` |

    <details>
    <summary>Xem thêm các loại <code>name</code> khác</summary>

    | `name` | Tác dụng | Ví dụ |
    |---|---|---|
    | `keywords` | Từ khóa liên quan tới trang — SEO, nhưng hiện gần như không còn tác dụng với Google | `<meta name="keywords" content="html, css, javascript">` |
    | `author` | Tác giả của trang | `<meta name="author" content="Nguyen Van A">` |
    | `robots` | Điều khiển crawler có index trang / theo link trong trang hay không | `<meta name="robots" content="noindex, nofollow">` |
    | `theme-color` | Màu thanh địa chỉ trình duyệt trên di động | `<meta name="theme-color" content="#317EFB">` |
    | `generator` | Công cụ/nền tảng tạo ra trang (VD: CMS) | `<meta name="generator" content="WordPress 6.4">` |

    </details>

- **http-equiv** + **content**: mô phỏng hành vi của một HTTP response header ngay trong HTML, dùng khi không thể (hoặc không tiện) cấu hình header phía server.

    | `http-equiv` | Tác dụng | Ví dụ |
    |---|---|---|
    | `refresh` | Tự động tải lại hoặc chuyển hướng trang sau X giây | `<meta http-equiv="refresh" content="5; url=https://example.com">` |
    | `X-UA-Compatible` | Ép IE cũ dùng chế độ render mới nhất | `<meta http-equiv="X-UA-Compatible" content="IE=edge">` |

    <details>
    <summary>Xem thêm các loại <code>http-equiv</code> khác</summary>

    | `http-equiv` | Tác dụng | Ví dụ |
    |---|---|---|
    | `content-security-policy` | Khai báo chính sách bảo mật nội dung (CSP), hạn chế nguồn script/style được phép chạy | `<meta http-equiv="Content-Security-Policy" content="default-src 'self'">` |
    | `content-type` | Khai báo kiểu nội dung + charset — cách khai báo cũ trước khi có thuộc tính `charset` riêng | `<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">` |

    </details>

- **property** (không thuộc chuẩn HTML, nhưng rất phổ biến — dùng cho Open Graph để kiểm soát nội dung hiển thị khi chia sẻ link lên mạng xã hội):

    ```html
    <meta property="og:title" content="Tiêu đề khi chia sẻ Facebook">
    <meta property="og:description" content="Mô tả ngắn gọn khi chia sẻ">
    <meta property="og:image" content="https://example.com/thumbnail.jpg">
    ```

### 1.2. `<link>`

Thẻ `<link>` dùng để liên kết trang HTML hiện tại với một tài nguyên bên ngoài (file CSS, favicon, font...). Đây là thẻ tự đóng (self-closing), đặt trong `<head>`, không có nội dung bên trong.

```html
<!-- Cơ bản -->
<link rel="stylesheet" href="style.css" type="text/css">

<!-- Đầy đủ -->
<link rel="stylesheet" href="style.css" type="text/css" media="screen" crossorigin="anonymous">
```

Các thuộc tính chính:

- **rel** (bắt buộc): khai báo mối quan hệ giữa trang hiện tại và tài nguyên được liên kết. Gồm các loại sau:

    | `rel` | Tác dụng | Ví dụ |
    |---|---|---|
    | `stylesheet` | Liên kết file CSS ngoài — phổ biến nhất | `<link rel="stylesheet" href="style.css">` |
    | `icon` | Favicon hiển thị trên tab trình duyệt | `<link rel="icon" href="favicon.ico" type="image/x-icon">` |

    <details>
    <summary>Xem thêm các loại <code>rel</code> khác</summary>

    | `rel` | Tác dụng | Ví dụ |
    |---|---|---|
    | `apple-touch-icon` | Icon khi thêm trang vào màn hình chính trên iOS | `<link rel="apple-touch-icon" href="icon-180.png">` |
    | `preload` | Tải trước một tài nguyên (font, ảnh, script...) để dùng sớm, tăng performance | `<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>` |
    | `preconnect` | Mở kết nối sớm tới domain khác (DNS, TLS) trước khi cần tải tài nguyên từ đó | `<link rel="preconnect" href="https://fonts.googleapis.com">` |
    | `dns-prefetch` | Phân giải DNS trước cho domain ngoài, tối ưu tốc độ | `<link rel="dns-prefetch" href="https://example.com">` |
    | `manifest` | Liên kết file manifest cho Progressive Web App (PWA) | `<link rel="manifest" href="manifest.json">` |
    | `canonical` | Khai báo URL "chính thức" của trang, tránh trùng lặp nội dung (SEO) | `<link rel="canonical" href="https://example.com/page">` |
    | `alternate` | Liên kết phiên bản khác của trang (ngôn ngữ khác, RSS feed...) | `<link rel="alternate" hreflang="vi" href="https://example.com/vi">` |
    | `author` | Liên kết tới trang/thông tin tác giả | `<link rel="author" href="humans.txt">` |

    </details>

- **href**: đường dẫn tới tài nguyên được liên kết — có thể là đường dẫn tương đối (`style.css`, `./assets/favicon.ico`) hoặc tuyệt đối (`https://fonts.googleapis.com/...`).

- **type**: khai báo kiểu MIME của tài nguyên, giúp trình duyệt biết cách xử lý trước khi tải về. Ví dụ:
    - `text/css` — cho stylesheet
    - `image/x-icon` hoặc `image/png` — cho favicon

    <details>
    <summary>Xem thêm các loại <code>type</code> khác</summary>

    - `image/svg+xml` — favicon/icon định dạng `.svg`
    - `font/woff2` — cho file font (thường đi kèm `preload`)
    - `font/woff` — font web, định dạng cũ hơn `woff2`
    - `application/manifest+json` — file manifest cho PWA (`rel="manifest"`)
    - `application/rss+xml` — RSS feed (`rel="alternate"`)

    </details>

    Trên trình duyệt hiện đại, `type` thường **không bắt buộc** — trình duyệt tự nhận diện qua đuôi file hoặc header response, nên nhiều dự án bỏ qua thuộc tính này (VD chỉ viết `<link rel="stylesheet" href="style.css">` mà không cần `type="text/css"`).

- **crossorigin**: cần khai báo khi tải tài nguyên từ domain khác (VD: font từ Google Fonts) để trình duyệt xử lý đúng CORS, đặc biệt quan trọng khi dùng với `rel="preload"`. Gồm các giá trị sau:

    | Giá trị | Ý nghĩa | Ví dụ |
    |---|---|---|
    | `anonymous` | Gửi request CORS **không kèm** thông tin xác thực (cookie, client cert...). Đây cũng là giá trị mặc định nếu chỉ viết `crossorigin` mà không kèm giá trị | `<link rel="preload" href="font.woff2" as="font" crossorigin>` |
    | `use-credentials` | Gửi request CORS **có kèm** thông tin xác thực — dùng khi server yêu cầu credentials mới trả về đúng tài nguyên | `<link rel="stylesheet" href="https://cdn.example.com/style.css" crossorigin="use-credentials">` |

    > Nếu bỏ hẳn thuộc tính `crossorigin`, trình duyệt tải tài nguyên như bình thường (không qua cơ chế CORS) — nhưng với font, trình duyệt **luôn** áp dụng CORS ẩn dù bạn không khai báo, nên nếu thiếu `crossorigin` mà server không cho phép, font sẽ tải thất bại âm thầm.

- **media**: chỉ định điều kiện (media query) để quyết định khi nào stylesheet được áp dụng. Một số giá trị phổ biến:

    | Giá trị | Ý nghĩa | Ví dụ |
    |---|---|---|
    | `all` | Áp dụng cho mọi thiết bị — **mặc định nếu không khai báo `media`** | `<link rel="stylesheet" href="style.css" media="all">` |
    | `screen` | Chỉ áp dụng khi xem trên màn hình (máy tính, điện thoại...) | `<link rel="stylesheet" href="style.css" media="screen">` |
    | `print` | Chỉ áp dụng khi in trang | `<link rel="stylesheet" href="print.css" media="print">` |
    | `speech` | Chỉ áp dụng cho trình đọc màn hình (screen reader) | `<link rel="stylesheet" href="speech.css" media="speech">` |

    <details>
    <summary>Xem thêm — kết hợp với media feature</summary>

    Có thể kết hợp `media` với các điều kiện chi tiết hơn (giống media query trong CSS):

    ```html
    <!-- Chỉ áp dụng khi màn hình rộng tối đa 600px -->
    <link rel="stylesheet" href="mobile.css" media="(max-width: 600px)">

    <!-- Chỉ áp dụng khi màn hình ở chế độ ngang -->
    <link rel="stylesheet" href="landscape.css" media="(orientation: landscape)">
    ```

    </details>

- **sizes**: khai báo kích thước icon, không tự resize ảnh mà chỉ khai báo cho trình duyệt biết kích thước thật của file; thường dùng với `rel="icon"` hoặc `apple-touch-icon` khi có nhiều kích thước khác nhau:
    ```html
    <link rel="icon" href="icon-32.png" sizes="32x32">
    ```

## 2. Body elements
### 2.1. Text

```html
<!-- Cơ bản -->
<h1>Hello World!</h1>
<p>This is my first web page.</p>

<!-- Đầy đủ -->
<h1 style="font-size: 3.2rem; color: #333;">Hello World!</h1>
<p style="font-size: 1.6rem; font-weight: 400; line-height: 1.5; color: #555; text-align: left;">
    This is <strong>my</strong> first <em>web page</em>, và tôi rất <mark>thích</mark> nó.
</p>
```

- Các loại thẻ text:

    | Thẻ | Ý nghĩa | Ví dụ |
    |---|---|---|
    | `h1`, `h2`, `h3`, `h4`, `h5`, `h6` | Tiêu đề (heading) — mức độ quan trọng/kích thước giảm dần từ `h1` đến `h6` | `<h1>Tiêu đề chính</h1>` |
    | `p` | Đoạn văn bản | `<p>Nội dung đoạn văn.</p>` |
    | `span` | Khối inline không mang ý nghĩa ngữ nghĩa riêng, dùng để bọc và style một phần nhỏ của text | `<span style="color: red;">chữ đỏ</span>` |
    | `b` | In đậm thuần hiển thị, không mang ý nghĩa ngữ nghĩa - Tương đương `<span style="font-weight: bold;">` | `<b>đậm</b>` |
    | `strong` | Nhấn mạnh nội dung **quan trọng** (in đậm, có ý nghĩa ngữ nghĩa) - Trình đọc sẽ nhấn mạnh khi gặp thẻ này | `<strong>quan trọng</strong>` |
    | `i` | In nghiêng thuần hiển thị, không mang ý nghĩa ngữ nghĩa | `<i>nghiêng</i>` |
    | `em` | Nhấn mạnh nội dung (in nghiêng, có ý nghĩa ngữ nghĩa) - Trình đọc sẽ nhấn mạnh khi gặp thẻ này | `<em>nhấn mạnh</em>` |
    | `small` | Chữ nhỏ hơn — thường dùng cho ghi chú, disclaimer - Tương đương `<span style="font-size: smaller;">` | `<small>ghi chú nhỏ</small>` |
    | `mark` | Đánh dấu highlight nội dung | `<mark>từ khóa</mark>` |
    | `del` / `ins` | `del` gạch ngang (nội dung đã xóa), `ins` gạch chân (nội dung mới thêm) | `<del>giá cũ</del> <ins>giá mới</ins>` |
    | `sub` / `sup` | Chỉ số dưới / chỉ số trên | `H<sub>2</sub>O`, `x<sup>2</sup>` |
    | `br` | Xuống dòng, không tạo đoạn mới như thẻ `<p>` | `Dòng 1<br>Dòng 2` |
    | `hr` | Đường kẻ ngang, phân cách nội dung theo chủ đề | `<hr>` |

- Các thuộc tính CSS chính thường dùng để style cho text:

    - **font-size**: kích thước chữ. Có thể khai báo bằng nhiều loại đơn vị:

        | Đơn vị | Loại | Ý nghĩa | Ví dụ |
        |---|---|---|---|
        | `px` | Tuyệt đối | Cố định, không phụ thuộc phần tử nào khác | `font-size: 16px;` |
        | `rem` | Tương đối | Theo font-size của thẻ `<html>` — **không cộng dồn**, nhất quán dù lồng sâu | `font-size: 1.5rem;` |
        | `em` | Tương đối | Theo font-size của phần tử cha — **cộng dồn** khi lồng nhiều cấp | `font-size: 1.5em;` |
        | `%` | Tương đối | Tương tự `em`, tính theo % font-size của phần tử cha | `font-size: 150%;` |
        | `vw` | Tương đối viewport | Theo % chiều rộng màn hình — dùng cho fluid typography | `font-size: 5vw;` |

        <details>
        <summary> Xem phần khác biệt chi tiết giữa `em` và `rem` ở ghi chú bên dưới bảng default heading.</summary>

        <br>

        Ví dụ minh họa sự khác nhau:

        ```html
        <html style="font-size: 16px;">
            <div style="font-size: 20px;">
                <p style="font-size: 1.5em;">Chữ này = 20 × 1.5 = 30px</p>
                <p style="font-size: 1.5rem;">Chữ này = 16 × 1.5 = 24px</p>
            </div>
        </html>
        ```

        - `em` tính theo font-size của **phần tử cha trực tiếp** (`div` = 20px) → `1.5em` = 30px.
        - `rem` luôn tính theo font-size của **thẻ gốc `<html>`** (16px), bất kể nằm lồng sâu bao nhiêu → `1.5rem` = 24px, không quan tâm `div` là bao nhiêu.

        Nếu lồng thêm một cấp nữa với `em`, giá trị sẽ **cộng dồn** theo cấp cha ngay phía trên nó:

        ```html
        <p style="font-size: 1.5em;">   <!-- cha: 20px → 1.5em = 30px -->
            <span style="font-size: 1.5em;">Chữ này = 30 × 1.5 = 45px</span>
        </p>
        ```

        Trong khi đó nếu dùng `rem` ở cả hai cấp, `span` vẫn ra đúng `1.5rem` = 24px như `p`, không nhân dồn thêm lần nữa.

        Nếu đã khai báo chung `font-size` cho toàn bộ page (VD: `html { font-size: 62.5%; }` → `1rem = 10px`) mà không ghi đè riêng cho từng thẻ heading/`p`, các thẻ này sẽ dùng **font-size mặc định của trình duyệt (UA stylesheet)**, vốn tính theo đơn vị `em` **tương đối theo phần tử cha**:

        | Thẻ | Mặc định trình duyệt (em) | Quy đổi ra px (khi `1rem = 10px`) | Tương đương rem |
        |---|---|---|---|
        | `h1` | `2em` | 20px | `2rem` |
        | `h2` | `1.5em` | 15px | `1.5rem` |
        | `h3` | `1.17em` | 11.7px | `1.17rem` |
        | `h4` | `1em` | 10px | `1rem` |
        | `h5` | `0.83em` | 8.3px | `0.83rem` |
        | `h6` | `0.67em` | 6.7px | `0.67rem` |
        | `p` | `1em` | 10px | `1rem` |

        > Giá trị `em` chỉ quy đổi trùng khớp sang `rem` như trên khi phần tử cha (thường là `body`) không tự ghi đè `font-size` — tức là font-size của nó vẫn bằng font-size gốc (`html`). Nếu `body` (hoặc phần tử cha khác) có `font-size` riêng, `em` sẽ tính theo giá trị đó thay vì theo root, khi đó `em` và `rem` sẽ lệch nhau.
        >
        > Trong thực tế, phần lớn dự án sẽ **ghi đè tường minh lại các giá trị** này bằng `rem`(VD: `h1 { font-size: 3.2rem; }`) thay vì phụ thuộc vào mặc định trình duyệt, để đảm bảo nhất quán giữa các trình duyệt.

        </details>

        <br>

    - **font-weight**: độ đậm của chữ. Giá trị số từ `100` (mảnh nhất) đến `900` (đậm nhất), hoặc từ khóa `normal` (= 400), `bold` (= 700):
        ```css
        h1 { font-weight: 700; }
        p  { font-weight: normal; }
        ```

    - **font-family**: khai báo font chữ, thường liệt kê nhiều font dự phòng (fallback) theo thứ tự ưu tiên, kết thúc bằng một font hệ thống chung (`serif`, `sans-serif`, `monospace`...):
        ```css
        body { font-family: "Segoe UI", Roboto, Arial, sans-serif; }
        ```

        Lưu ý: cần `""` khi tên font chứa khoảng trắng hoặc ký tự đặc biệt (như "Segoe UI" trong ví dụ).

    - **line-height**: khoảng cách giữa các dòng chữ. Nên dùng giá trị **không đơn vị** (VD: `1.5`) thay vì `px`/`em`, vì nó sẽ tự tính theo font-size của chính phần tử đó, tránh lỗi khi phần tử con có font-size khác:
        ```css
        p { line-height: 1.5; }
        ```

    - **color**: màu chữ — có thể khai báo bằng `hex`, `rgb()`/`rgba()`, `hsl()`, hoặc tên màu (`red`, `black`...):
        ```css
        p { color: #333; }
        ```

    - **text-align**: căn lề chữ theo chiều ngang — `left`, `right`, `center`, `justify`:
        ```css
        h1 { text-align: center; }
        ```

    - **text-decoration**: trang trí đường kẻ trên chữ — `underline` (gạch chân), `line-through` (gạch ngang), `none` (bỏ gạch chân, thường dùng cho thẻ `<a>`):
        ```css
        a { text-decoration: none; }
        ```

    - **letter-spacing** / **word-spacing**: khoảng cách giữa các ký tự / giữa các từ:
        ```css
        h1 { letter-spacing: 0.05em; }
        ```

### 2.2. List

```html
<!-- Cơ bản -->
<ul>
    <li>Sữa</li>
    <li>Trứng</li>
</ul>

<!-- Đầy đủ -->
<ol type="A" reversed style="list-style-position: outside; font-size: 1.4rem; color: #333; line-height: 1.6;">
    <li>Mục C</li>
    <li>Mục B</li>
    <li>Mục A</li>
</ol>
```

- Các loại thẻ danh sách:

    | Thẻ | Ý nghĩa | Ví dụ |
    |---|---|---|
    | `ul` | Danh sách không thứ tự (unordered list) — mỗi mục hiển thị bullet, dùng khi thứ tự các mục không quan trọng | `<ul><li>Mục 1</li></ul>` |
    | `ol` | Danh sách có thứ tự (ordered list) — mỗi mục tự đánh số, dùng khi thứ tự có ý nghĩa (các bước, xếp hạng) | `<ol><li>Mục 1</li></ol>` |
    | `li` | Một mục trong `ul`/`ol` (list item) | `<li>Nội dung</li>` |
    | `dl` | Danh sách mô tả (description list) — gồm cặp thuật ngữ/định nghĩa | `<dl>...</dl>` |
    | `dt` | Thuật ngữ (description term) trong `dl` | `<dt>HTML</dt>` |
    | `dd` | Định nghĩa/mô tả (description definition) cho `dt` đứng trước nó | `<dd>Ngôn ngữ đánh dấu...</dd>` |

    <details>
    <summary>Ví dụ đầy đủ với <code>dl</code></summary>

    Một `dt` có thể đi kèm nhiều `dd`, và một `dd` cũng có thể mô tả chung cho nhiều `dt` đứng liền trước:

    ```html
    <dl>
        <dt>HTML</dt>
        <dd>Ngôn ngữ đánh dấu dùng để xây dựng cấu trúc trang web.</dd>

        <dt>Chó</dt>
        <dt>Mèo</dt>
        <dd>Đều là thú cưng phổ biến.</dd>
    </dl>
    ```

    </details>

- Các thuộc tính chính của `ol`:

    | Thuộc tính | Ý nghĩa | Ví dụ |
    |---|---|---|
    | `type` | Kiểu đánh số: `1` (số, mặc định), `A`/`a` (chữ hoa/thường), `I`/`i` (số La Mã hoa/thường) | `<ol type="I">` |
    | `start` | Số bắt đầu đếm (không đổi kiểu hiển thị, chỉ đổi giá trị) | `<ol start="5">` → mục đầu tiên là 5 |
    | `reversed` | Đảo ngược thứ tự đếm (từ cao xuống thấp) | `<ol reversed>` → 3, 2, 1 |

    `li` cũng có thuộc tính `value` để ghi đè số thứ tự cho riêng một mục (chỉ có tác dụng trong `ol`, các mục sau đó tiếp tục đếm từ giá trị này):

    ```html
    <ol>
        <li>Một</li>
        <li value="10">Mười</li>
        <li>Mười một</li>
    </ol>
    ```

- Danh sách lồng nhau (nested list) — đặt một `ul`/`ol` bên trong một `<li>` của danh sách cha:

    ```html
    <ul>
        <li>Trái cây
            <ul>
                <li>Táo</li>
                <li>Cam</li>
            </ul>
        </li>
        <li>Rau củ</li>
    </ul>
    ```

- Các thuộc tính CSS chính thường dùng để style cho danh sách:

    - **list-style-type**: đổi kiểu bullet/số hiển thị — dùng thay cho thuộc tính HTML `type` (khuyến khích dùng CSS thay vì thuộc tính HTML để tách nội dung khỏi trình bày):

        | Giá trị | Áp dụng cho | Ý nghĩa |
        |---|---|---|
        | `disc` | `ul` | Chấm tròn đặc — mặc định của `ul` |
        | `circle` | `ul` | Chấm tròn rỗng |
        | `square` | `ul` | Hình vuông |
        | `decimal` | `ol` | Số `1, 2, 3` — mặc định của `ol` |
        | `upper-alpha` / `lower-alpha` | `ol` | Chữ `A, B, C` / `a, b, c` |
        | `upper-roman` / `lower-roman` | `ol` | Số La Mã `I, II, III` / `i, ii, iii` |
        | `none` | `ul`/`ol` | Bỏ hết bullet/số |

        ```css
        ul { list-style-type: square; }
        ol { list-style-type: upper-roman; }
        ```

    - **list-style-position**: vị trí bullet/số so với nội dung mục:

        | Giá trị | Ý nghĩa |
        |---|---|
        | `outside` | Các dòng sau căn lề với dòng đầu — **mặc định** |
        | `inside` | Các dòng sau căn lề với dấu bullet (xấu) |

        ```css
        ul { list-style-position: inside; }
        ```

    - **list-style-image**: dùng hình ảnh thay cho bullet mặc định:

        ```css
        ul { list-style-image: url("bullet.png"); }
        ```

    - **list-style**: shorthand gộp cả 3 thuộc tính trên theo thứ tự `type` `position` `image`:

        ```css
        ul { list-style: square inside url("bullet.png"); }
        ```

        > Muốn bỏ hoàn toàn bullet/số (VD khi dùng `ul` để làm menu điều hướng) thì dùng `list-style: none;`.

### 2.3. Link

```html
<!-- Cơ bản -->
<a href="https://www.google.com/">Google</a>

<!-- Đầy đủ -->
<a href="https://www.google.com/" target="_blank" rel="noopener noreferrer">Mở Google ở tab mới</a>
```

- Thuộc tính chính của `a`:

    | Thuộc tính | Ý nghĩa | Ví dụ |
    |---|---|---|
    | `href` | Đường dẫn đích — bắt buộc để thẻ có tác dụng liên kết, thiếu `href` thì `a` chỉ là text thường | `<a href="about.html">Giới thiệu</a>` |
    | `target` | Nơi mở liên kết: `_self` (mặc định, cùng tab) hoặc `_blank` (tab mới) | `<a href="..." target="_blank">` |
    | `download` | Tải file về máy thay vì mở trong trình duyệt, có thể kèm tên file muốn lưu | `<a href="html5.png" download>Tải icon</a>` |
    | `rel` | Khai báo quan hệ với trang đích; nên thêm `noopener noreferrer` khi dùng `target="_blank"` để tránh trang mới truy cập ngược lại `window.opener` (rủi ro bảo mật) | `<a ... target="_blank" rel="noopener noreferrer">` |

- Các dạng giá trị `href` thường gặp:

    | Dạng | Ý nghĩa | Ví dụ |
    |---|---|---|
    | URL tuyệt đối | Trỏ tới một trang bên ngoài domain hiện tại | `href="https://www.google.com/"` |
    | Đường dẫn tương đối | Trỏ tới file khác trong cùng dự án, tính từ vị trí file hiện tại | `href="about.html"` |
    | Đường dẫn gốc (`/`) | Trỏ tới trang chủ, tính từ gốc domain chứ không phải từ file hiện tại | `href="/"` |
    | Neo trong trang (`#id`) | Cuộn tới phần tử có `id` tương ứng trên cùng trang; riêng `href="#"` (không có `id`) sẽ cuộn lên đầu trang | `href="#footer"` |
    | `mailto:` | Mở ứng dụng mail mặc định của máy, soạn sẵn email gửi tới địa chỉ khai báo | `href="mailto:random@email.com"` |
    | `tel:` | Gọi tới số điện thoại được ghi — hữu ích khi mở trên di động | `href="tel:+1234567890"` |

    <details>
    <summary>Ví dụ các dạng <code>href</code> đặc biệt</summary>

    ```html
    <li>Download an <a href="html5.png" download>HTML5 favicon</a></li>
    <li>Contact me at <a href="mailto:random@email.com">my email address</a>.</li>
    <li>Dial <a href="tel:+1234567890">my phone number</a>.</li>
    <li>Open <a href="https://www.google.com/" target="_blank">Google</a> in a new tab.</li>
    ```

    </details>

- Style liên kết bằng CSS dùng pseudo-class theo trạng thái. Nên khai báo đúng thứ tự **LVHA** (Link → Visited → Hover → Active), vì các rule khai báo sau sẽ đè lên rule trước nếu cùng độ ưu tiên:

    | Pseudo-class | Ý nghĩa |
    |---|---|
    | `:link` | Liên kết chưa được truy cập |
    | `:visited` | Liên kết đã được truy cập |
    | `:hover` | Khi di chuột qua liên kết |
    | `:active` | Khi đang nhấn giữ chuột trên liên kết |

    ```css
    a:link { color: blue; }
    a:visited { color: purple; }
    a:hover { color: red; text-decoration: none; }
    a:active { color: orange; }
    ```

    Thuộc tính `style=""` (inline style) chỉ áp dụng style trực tiếp lên một phần tử cụ thể tại thời điểm đó — nó không có khái niệm "trạng thái" (state) như `:hover`, `:focus`, `:active`, `:nth-child()`,... Do đó, Pseudo-class cần một **selector** để trình duyệt biết khi nào áp dụng style này, mà inline style không có selector nào cả, nó chỉ là style luôn-luôn-đúng cho phần tử đó.

    - Mặc định của trình duyệt (khi không tự khai báo gì) cho từng trạng thái:

        | Trạng thái | Mặc định của trình duyệt |
        |---|---|
        | `:link` | `color: blue;` + gạch chân |
        | `:visited` | `color: purple;` + gạch chân |
        | `:hover` | Không đổi màu, chỉ đổi con trỏ chuột thành hình bàn tay |
        | `:active` | Không đổi màu ở trình duyệt hiện đại — giữ nguyên màu của `:link`/`:visited` |

    - Nếu khai báo **thiếu một trạng thái** (vd có `:link` mà không có `:visited`), trạng thái thiếu đó **không** tự rơi về mặc định trình duyệt, mà đi tìm rule gần nhất theo thứ tự ưu tiên:

        1. Rule pseudo-class riêng cho trạng thái đó (nếu có khai)
        2. Rule trên `.class`/thẻ `a` gốc, nếu rule đó có khai property tương ứng (vd `color`)
        3. Giá trị kế thừa (`inherit`) từ phần tử cha
        4. Chỉ khi hoàn toàn không có rule CSS nào của mình áp lên phần tử, mới rơi về mặc định trình duyệt ở bảng trên

        Ví dụ: nếu chỉ viết `.footer-link { color: green; }` mà không khai riêng `:link`/`:visited`/`:hover`/`:active`, thì **mọi trạng thái** của link đó đều hiện màu `green` — vì đây là rule tác giả (author) duy nhất cho `color`, và CSS tự viết luôn đè lên CSS mặc định của trình duyệt bất kể độ ưu tiên (specificity), do khác nguồn gốc (origin) trong thứ tự cascade.

